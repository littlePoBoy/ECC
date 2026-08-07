# Hook 快速参考

ECC 插件中所有 hook 的自动生成摘要。

## Hook 生命周期

Hook 是事件驱动的自动化机制，在 Claude Code 工具执行生命周期的特定节点触发：

```
会话开始 → SessionStart hook 触发
  ↓
用户请求 → Claude 选择工具 → PreToolUse hook 触发 → 工具执行 → PostToolUse hook 触发
  ↓ （每次工具调用重复）
Claude 完成响应 → Stop hook 触发
  ↓
上下文压缩 → PreCompact hook 触发（保存状态）
  ↓
会话结束 → SessionEnd hook 触发
```

- **PreToolUse** hook 在工具执行前运行。退出码 2 阻止调用；退出码 0 加 stderr 仅发出警告。
- **PostToolUse** hook 在工具完成后运行。用于分析输出，但无法阻止执行。
- **Stop** hook 在每次 Claude 响应后运行。用于批量质量检查和状态持久化。
- **SessionStart/SessionEnd** hook 在会话生命周期边界运行。
- **PreCompact** hook 在上下文压缩前运行，用于保存状态。
- **PostToolUseFailure** hook 在工具调用失败时运行。

Hook 通过 `ECC_HOOK_PROFILE`（minimal/standard/strict）进行配置文件级别的门控，并可通过 `ECC_DISABLED_HOOKS` 单独禁用。

---

## 快速查找

### PreToolUse Hook

| Hook | 匹配器 | 行为 | 是否阻断 | 异步 |
|------|---------|------|---------|------|
| `pre:bash:dispatcher` | Bash | 统一预检调度：质量检查、tmux 提醒、git push 提醒、GateGuard | 是（关键问题退出码 2） | 否 |
| `pre:write:doc-file-warning` | Write | 警告非标准文档文件（允许 README、CLAUDE、CONTRIBUTING 等） | 否（仅警告） | 否 |
| `pre:edit-write:suggest-compact` | Edit\|Write | 在逻辑间隔（约每 50 次工具调用）建议手动执行 `/compact` | 否（仅警告） | 否 |
| `pre:observe:continuous-learning` | * | 捕获工具使用观察数据，用于持续学习 | 否（异步，非阻断） | 是 |
| `pre:governance-capture` | Bash\|Write\|Edit\|MultiEdit | 捕获治理事件（密钥检测、策略违规、审批请求）。需设置 `ECC_GOVERNANCE_CAPTURE=1` 启用 | 否 | 否 |
| `pre:config-protection` | Write\|Edit\|MultiEdit | 阻止对 linter/formatter 配置文件的修改；引导 agent 修复代码而非削弱检查配置 | 是（退出码 2） | 否 |
| `pre:mcp-health-check` | * | 在 MCP 工具执行前检查 MCP 服务器健康状态；阻止对不健康 MCP 服务器的调用 | 是（针对不健康的服务器） | 否 |
| `pre:edit-write:gateguard-fact-force` | Edit\|Write\|MultiEdit | 事实强制门控：阻止每个文件的首次 Edit/Write/MultiEdit，要求先进行调查（检查引用方、数据模式、用户指令）后再放行 | 是（退出码 2） | 否 |

### PostToolUse Hook

| Hook | 匹配器 | 行为 | 异步 |
|------|---------|----------|-------|
| `post:dispatcher:sync` | * | 在单个进程中运行同步 PostToolUse 子 hook（PR 日志记录、构建分析、质量门控、设计质量检查、Prettier 格式化、TypeScript 检查、console.log 警告） | 否 |
| `post:dispatcher:async` | * | 在单个进程中运行后台 PostToolUse 子 hook（非阻断分析任务） | 是 |
| `post:mcp-health-check` | * | 跟踪失败的 MCP 工具调用，标记不健康的服务器，尝试重连（在 PostToolUseFailure 时触发） | 否 |

### 生命周期 Hook

| Hook | 事件 | 行为 | 异步 |
|------|-------|----------|-------|
| `session:start` | SessionStart | 加载上次会话上下文并检测包管理器 | 否 |
| `session-start:plan-canvas-sessions` | SessionStart | 展示未关闭的 Plan Canvas 浏览器审查会话，以便新会话可以恢复规划流程 | 否 |
| `pre:compact` | PreCompact | 在上下文压缩前保存状态 | 否 |
| `stop:format-typecheck` | Stop | 批量格式化（Biome/Prettier）并类型检查（tsc）本次响应中编辑的所有 JS/TS 文件 | 否 |
| `stop:check-console-log` | Stop | 在每次响应后检查修改的文件中是否残留 `console.log` | 否 |
| `stop:session-end` | Stop | 当有 transcript 路径可用时，持久化会话状态 | 是 |
| `stop:evaluate-session` | Stop | 评估会话中的可提取模式（持续学习） | 是 |
| `stop:cost-tracker` | Stop | 跟踪每次会话的 token 和成本指标 | 是 |
| `stop:desktop-notify` | Stop | 当 Claude 完成响应时发送桌面通知（macOS/WSL），包含任务摘要 | 是 |
| `session:end:marker` | SessionEnd | 会话结束生命周期标记和清理日志 | 是 |

---

## 详细 Hook 说明

### PreToolUse Hook

#### pre:bash:dispatcher
- **类型**: PreToolUse
- **匹配器**: Bash
- **行为**: 统一 Bash 预检调度器。运行质量检查，建议长时间运行的命令（npm test、cargo build、docker）使用 tmux，提醒在 `git push` 前审查更改，并运行 GateGuard 检查。内部调度到子 hook：开发服务器阻止器、tmux 提醒、git push 提醒、pre-commit 质量检查。
- **退出码**: 2（阻止关键问题，如在 tmux 外运行开发服务器）、0（非关键问题仅警告）
- **异步**: 否
- **超时**: 未指定

#### pre:write:doc-file-warning
- **类型**: PreToolUse
- **匹配器**: Write
- **行为**: 警告非标准文档文件。允许 README、CLAUDE、CONTRIBUTING、CHANGELOG、LICENSE、SKILL 以及 docs/ 和 skills/ 下的文件。跨平台路径处理。
- **退出码**: 0（仅警告）
- **异步**: 否
- **配置文件**: standard、strict

#### pre:edit-write:suggest-compact
- **类型**: PreToolUse
- **匹配器**: Edit|Write
- **行为**: 在逻辑间隔（约每 50 次工具调用）建议手动执行 `/compact`，以管理上下文窗口使用。
- **退出码**: 0（仅警告）
- **异步**: 否
- **配置文件**: standard、strict

#### pre:observe:continuous-learning
- **类型**: PreToolUse
- **匹配器**: *（所有工具）
- **行为**: 捕获工具使用意图/观察数据，用于持续学习信号。委托给 `observe-runner.js` 记录工具使用模式。
- **退出码**: 不适用（异步，非阻断）
- **异步**: 是（超时：10 秒）
- **配置文件**: standard、strict

#### pre:governance-capture
- **类型**: PreToolUse
- **匹配器**: Bash|Write|Edit|MultiEdit
- **行为**: 捕获治理事件，包括密钥检测、策略违规和审批请求。必须通过 `ECC_GOVERNANCE_CAPTURE=1` 显式启用。
- **退出码**: 0（非阻断）
- **异步**: 否
- **超时**: 10 秒
- **配置文件**: standard、strict

#### pre:config-protection
- **类型**: PreToolUse
- **匹配器**: Write|Edit|MultiEdit
- **行为**: 阻止对 linter 和 formatter 配置文件的修改（如 .eslintrc、.prettierrc、biome.json）。引导 agent 修复代码，而非削弱 lint/format 配置。
- **退出码**: 2（阻断）
- **异步**: 否
- **超时**: 5 秒
- **配置文件**: standard、strict

#### pre:mcp-health-check
- **类型**: PreToolUse
- **匹配器**: *（所有工具，目标为 MCP 工具调用）
- **行为**: 在 MCP 工具执行前检查 MCP 服务器健康状态。阻止对不健康 MCP 服务器的调用。
- **退出码**: 2（阻止不健康的 MCP 调用）
- **异步**: 否
- **配置文件**: standard、strict

#### pre:edit-write:gateguard-fact-force
- **类型**: PreToolUse
- **匹配器**: Edit|Write|MultiEdit
- **行为**: 事实强制门控，阻止每个文件的首次 Edit/Write/MultiEdit，要求先完成调查再放行。要求 agent 检查引用方、数据模式和用户指令。强制进行有依据的编辑，而非投机性更改。
- **退出码**: 2（在调查完成前持续阻断）
- **异步**: 否
- **超时**: 5 秒
- **配置文件**: standard、strict

### PostToolUse Hook

#### post:dispatcher:sync
- **类型**: PostToolUse
- **匹配器**: *（所有工具）
- **行为**: 同步 PostToolUse 调度器，在单个进程中运行所有同步子 hook，同时保留各 hook 的独立控制。子 hook 包括：PR 日志记录（在 `gh pr create` 后记录 PR URL）、构建分析、质量门控（编辑后的快速检查）、设计质量检查（警告通用模板 UI）、Prettier 格式化（自动格式化 JS/TS）、TypeScript 检查（`tsc --noEmit`）、console.log 警告。
- **异步**: 否
- **超时**: 30 秒

#### post:dispatcher:async
- **类型**: PostToolUse
- **匹配器**: *（所有工具）
- **行为**: 异步 PostToolUse 调度器，在单个进程中运行后台子 hook。非阻断分析任务，不会延迟工具执行。
- **异步**: 是（超时：45 秒）

#### post:mcp-health-check（PostToolUseFailure）
- **类型**: PostToolUseFailure
- **匹配器**: *（所有工具）
- **行为**: 跟踪失败的 MCP 工具调用，标记不健康的服务器，并尝试重连。在 MCP 工具调用失败时运行。
- **异步**: 否
- **配置文件**: standard、strict

### SessionStart Hook

#### session:start
- **类型**: SessionStart
- **匹配器**: *（始终触发）
- **行为**: 从之前的会话加载有上限的历史上下文，检测项目状态（包管理器、框架），并准备会话元数据。上下文大小受 `ECC_SESSION_START_MAX_CHARS`（默认：8000 字符）限制。可通过 `ECC_SESSION_START_CONTEXT=off` 禁用。
- **异步**: 否

#### session-start:plan-canvas-sessions
- **类型**: SessionStart
- **匹配器**: *（始终触发）
- **行为**: 展示未关闭的 Plan Canvas 浏览器审查会话，以便新的 Claude Code 会话可以恢复规划流程。
- **异步**: 否
- **配置文件**: standard、strict

### PreCompact Hook

#### pre:compact
- **类型**: PreCompact
- **匹配器**: *（始终触发）
- **行为**: 在上下文压缩前保存会话状态。确保在会话被压缩前持久化重要上下文。
- **异步**: 否
- **配置文件**: standard、strict

### Stop Hook

#### stop:format-typecheck
- **类型**: Stop
- **匹配器**: *（始终触发）
- **行为**: 使用 Biome 或 Prettier 批量格式化当前响应中编辑的所有 JS/TS 文件，然后运行 TypeScript 类型检查（`tsc --noEmit`）。在 Stop 阶段统一运行，而非在每次 Edit 后单独执行，以提高效率。
- **异步**: 否
- **超时**: 300 秒（5 分钟）
- **配置文件**: standard、strict

#### stop:check-console-log
- **类型**: Stop
- **匹配器**: *（始终触发）
- **行为**: 在每次响应后审计所有修改的文件中的 `console.log` 语句。警告代码中残留的调试日志。
- **异步**: 否
- **配置文件**: standard、strict

#### stop:session-end
- **类型**: Stop
- **匹配器**: *（始终触发）
- **行为**: 在每次响应后持久化会话状态。需要 Stop 事件中的 `transcript_path` 来捕获完整会话数据。
- **异步**: 是（超时：10 秒）
- **配置文件**: minimal、standard、strict

#### stop:evaluate-session
- **类型**: Stop
- **匹配器**: *（始终触发）
- **行为**: 评估会话中的可提取模式，作为持续学习系统的一部分。从会话历史中识别可复用模式。
- **异步**: 是（超时：10 秒）
- **配置文件**: minimal、standard、strict

#### stop:cost-tracker
- **类型**: Stop
- **匹配器**: *（始终触发）
- **行为**: 跟踪每次会话的 token 和成本指标。输出轻量级运行成本遥测标记。可通过 `ECC_CONTEXT_MONITOR_COST_WARNINGS=off` 抑制。
- **异步**: 是（超时：10 秒）
- **配置文件**: minimal、standard、strict

#### stop:desktop-notify
- **类型**: Stop
- **匹配器**: *（始终触发）
- **行为**: 当 Claude 完成响应时发送桌面通知（macOS/WSL），包含任务摘要。无需监控终端即可获得环境感知。
- **异步**: 是（超时：10 秒）
- **配置文件**: standard、strict

### SessionEnd Hook

#### session:end:marker
- **类型**: SessionEnd
- **匹配器**: *（始终触发）
- **行为**: 会话结束生命周期标记。执行清理日志记录并标记会话边界。非阻断。
- **异步**: 是（超时：10 秒）
- **配置文件**: minimal、standard、strict

---

## 子 Hook（内部调度）

调度器 hook（`pre:bash:dispatcher`、`post:dispatcher:sync`、`post:dispatcher:async`）在单个进程中运行多个子 hook。这些子 hook 不直接在 hooks.json 中配置，而是由调度器执行：

### Pre-Bash 子 Hook（通过 pre:bash:dispatcher 调度）
| 子 Hook | 行为 | 退出码 |
|---------|----------|--------|
| 开发服务器阻止器 | 阻止在 tmux 外运行 `npm run dev` 等命令 | 2（阻断） |
| Tmux 提醒 | 建议长时间运行的命令使用 tmux | 0（警告） |
| Git push 提醒 | 提醒在 `git push` 前审查更改 | 0（警告） |
| Pre-commit 质量检查 | 对暂存文件运行 lint，验证提交消息格式，检测 console.log/debugger/密钥 | 2（关键）/ 0（警告） |

### PostToolUse 同步子 Hook（通过 post:dispatcher:sync 调度）
| 子 Hook | 行为 |
|---------|----------|
| PR 日志记录 | 在 `gh pr create` 后记录 PR URL 和审查命令 |
| 构建分析 | 构建命令后的后台分析 |
| 质量门控 | 编辑后的快速质量检查 |
| 设计质量检查 | 当前端编辑趋向通用模板 UI 时发出警告 |
| Prettier 格式化 | 使用 Prettier 自动格式化 JS/TS 文件 |
| TypeScript 检查 | 编辑 .ts/.tsx 文件后运行 `tsc --noEmit` |
| console.log 警告 | 警告编辑文件中的 console.log 语句 |

---

## 运行时控制

### 环境变量

| 变量 | 默认值 | 说明 |
|----------|---------|-------------|
| `ECC_HOOK_PROFILE` | `standard` | Hook 配置文件：`minimal`、`standard` 或 `strict` |
| `ECC_DISABLED_HOOKS` | （无） | 逗号分隔的要禁用的 hook ID |
| `ECC_GATEGUARD` | `on` | 设为 `off` 可在设置/恢复期间禁用 GateGuard |
| `ECC_SESSION_START_MAX_CHARS` | `8000` | 会话启动上下文加载的最大字符数 |
| `ECC_SESSION_START_CONTEXT` | `on` | 设为 `off` 可完全禁用会话启动上下文 |
| `ECC_CONTEXT_MONITOR_COST_WARNINGS` | `on` | 设为 `off` 可抑制 API 费用估算 |
| `ECC_GOVERNANCE_CAPTURE` | `0` | 设为 `1` 可启用治理事件捕获 |

### 配置文件

| 配置文件 | 说明 |
|---------|-------------|
| `minimal` | 仅包含必要的生命周期和安全 hook |
| `standard` | 默认。平衡的质量 + 安全检查 |
| `strict` | 附加提醒和更严格的防护措施 |

---

## 内存持久化契约

内存持久化系统（定义在 `hooks/memory-persistence/` 中）为会话连续性提供稳定的生命周期契约：

| 事件 | Hook ID | 脚本 | 用途 |
|-------|---------|--------|---------|
| SessionStart | `session:start` | `session-start-bootstrap.js` | 加载有上限的历史上下文并检测项目状态 |
| PreCompact | `pre:compact` | `pre-compact.js` | 在上下文压缩前持久化会话状态 |
| PreToolUse | `pre:observe:continuous-learning` | `observe-runner.js` | 记录工具意图用于学习信号 |
| PostToolUse | `post:observe:continuous-learning` | `observe-runner.js` | 记录工具结果用于学习信号 |
| PostToolUse | `post:session-activity-tracker` | `session-activity-tracker.js` | 记录每次会话的工具调用和文件活动 |
| SessionEnd | `session:end:marker` | `session-end-marker.js` | 持久化会话结束摘要 |

运维预期：默认保持持久化数据本地存储，除非显式启用，否则避免将对话记录发送到托管服务，并遵守通过 `ECC_HOOK_PROFILE` 和 `ECC_DISABLED_HOOKS` 进行的配置文件门控。

---

## Hook 输入 Schema

所有 hook 通过 stdin 接收以下结构的 JSON：

```typescript
interface HookInput {
  tool_name: string;          // "Bash"、"Edit"、"Write"、"Read" 等
  tool_input: {
    command?: string;         // Bash: 正在运行的命令
    file_path?: string;       // Edit/Write/Read: 目标文件
    old_string?: string;      // Edit: 被替换的文本
    new_string?: string;      // Edit: 替换后的文本
    content?: string;         // Write: 文件内容
  };
  tool_output?: {             // 仅限 PostToolUse
    output?: string;          // 命令/工具输出
  };
}
```

## 退出码参考

| 退出码 | 含义 | 效果 |
|-----------|---------|--------|
| 0 | 成功 | 继续执行（通过 stderr 输出的警告会展示给 Claude） |
| 2 | 阻断 | 阻止工具调用（仅限 PreToolUse） |
| 其他非零值 | 错误 | 记录日志但不阻断 |

---

## 源文件

- **Hook 定义**: `hooks/hooks.json`
- **内存持久化契约**: `hooks/memory-persistence/hooks.json`
- **Hook 脚本**: `scripts/hooks/`
- **Hook 运行器包装器**: `scripts/hooks/run-with-flags.js`（配置文件门控和 hook 禁用）
- **引导解析器**: `scripts/hooks/plugin-hook-bootstrap.js`（解析 ECC 插件根目录）
