# 脚本快速参考

ECC 插件中所有脚本的自动生成摘要。

## 快速查找

### 顶层脚本

| 脚本 | 用途 | 用法 |
|--------|---------|-------|
| catalog.js | 生成技能/代理/命令目录 | `node catalog.js` |
| consult.js | ECC 项目设置咨询向导 | `node consult.js` |
| control-pane.js | 启动控制面板 Web UI | `node control-pane.js` |
| dashboard-web.js | 运维就绪状态仪表盘 Web 服务器 | `node dashboard-web.js` |
| discussion-audit.js | 审计 GitHub 讨论中的模式 | `node discussion-audit.js` |
| doctor.js | 诊断 ECC 安装健康状态 | `node doctor.js` |
| ecc.js | ECC 主 CLI 入口 | `node ecc.js <command>` |
| feedback.js | 收集并存储用户反馈 | `node feedback.js` |
| harness-adapter-compliance.js | 检查 Harness 适配器合规性 | `node harness-adapter-compliance.js` |
| harness-audit.js | 审计 Harness 配置和状态 | `node harness-audit.js` |
| install-apply.js | 将 ECC 安装应用到目标 | `node install-apply.js` |
| install-plan.js | 生成 ECC 安装计划 | `node install-plan.js` |
| ito.js | ITO（智能任务编排）引擎 | `node ito.js` |
| list-installed.js | 列出已安装的 ECC 组件 | `node list-installed.js` |
| loop-status.js | 显示循环/编排状态 | `node loop-status.js` |
| memory.js | 记忆库操作（读取/写入/搜索） | `node memory.js` |
| memory-mcp.mjs | 记忆 MCP 服务器（ESM） | `node memory-mcp.mjs` |
| observability-readiness.js | 检查可观测性技术栈就绪状态 | `node observability-readiness.js` |
| operator-readiness-dashboard.js | 完整运维就绪状态仪表盘 | `node operator-readiness-dashboard.js` |
| orchestrate-codex-worker.sh | 编排 Codex 工作进程 | `bash orchestrate-codex-worker.sh` |
| orchestrate-worktrees.js | 编排 git worktree 会话 | `node orchestrate-worktrees.js` |
| orchestration-status.js | 显示编排状态 | `node orchestration-status.js` |
| plan-canvas.js | Plan Canvas CLI 操作 | `node plan-canvas.js` |
| platform-audit.js | 审计平台配置 | `node platform-audit.js` |
| preview-pack-smoke.js | 预览包冒烟测试 | `node preview-pack-smoke.js` |
| release-approval-gate.js | 发布审批关卡检查 | `node release-approval-gate.js` |
| repair.js | 修复 ECC 安装问题 | `node repair.js` |
| session-inspect.js | 检查会话状态和上下文 | `node session-inspect.js` |
| sessions-cli.js | 会话管理 CLI | `node sessions-cli.js` |
| setup-package-manager.js | 检测并配置包管理器 | `node setup-package-manager.js` |
| skill-create-output.js | 生成技能创建输出 | `node skill-create-output.js` |
| skills-health.js | 检查技能健康状态和有效性 | `node skills-health.js` |
| status.js | ECC 整体状态显示 | `node status.js` |
| sync-ecc-to-codex.sh | 将 ECC 配置同步到 Codex | `bash sync-ecc-to-codex.sh` |
| uninstall.js | 卸载 ECC 组件 | `node uninstall.js` |
| work-items.js | 管理工作项（GitHub Issues 集成） | `node work-items.js` |

---

## CI 脚本 (`ci/`)

用于持续集成验证和安全检查的脚本。

| 脚本 | 用途 |
|--------|---------|
| catalog.js | CI 专用目录生成 |
| check-unicode-safety.js | 扫描文件中的危险 Unicode（同形字、零宽字符、双向文本覆盖） |
| generate-command-registry.js | 生成命令注册表用于验证 |
| scan-supply-chain-iocs.js | 扫描依赖中的供应链攻击指标 |
| supply-chain-advisory-sources.js | 管理供应链公告数据源 |
| validate-agents.js | 验证代理 frontmatter 格式和内容 |
| validate-commands.js | 验证命令文件格式和结构 |
| validate-hooks.js | 验证 hooks 配置 |
| validate-install-manifests.js | 验证安装清单文件 |
| validate-no-personal-paths.js | 确保代码库中无个人路径泄露 |
| validate-rules.js | 验证规则文件格式 |
| validate-skills.js | 验证技能目录结构和 SKILL.md 格式 |
| validate-workflow-security.js | 验证工作流脚本的安全性问题 |

---

## Codex 集成脚本 (`codex/`)

用于 Codex 平台集成的脚本。

| 脚本 | 用途 |
|--------|---------|
| check-codex-global-state.sh | 检查 Codex 全局状态配置 |
| check-plugin-cache.js | 验证 Codex 插件缓存完整性 |
| install-global-git-hooks.sh | 为 Codex 全局安装 ECC git hooks |
| merge-codex-config.js | 将 ECC 配置合并到 Codex 配置中 |
| merge-mcp-config.js | 合并 MCP 服务器配置 |

---

## Hook 脚本 (`hooks/`)

由 hook 系统调用的可执行脚本。Hook 调用图详见 [HOOKS-QUICK-REF.md](../hooks/HOOKS-QUICK-REF.md)。

### 调度器

| 脚本 | 用途 |
|--------|---------|
| bash-hook-dispatcher.js | 将 PreToolUse Bash hook 路由到子处理器 |
| pre-bash-dispatcher.js | PreToolUse bash 子调度器 |
| post-bash-dispatcher.js | PostToolUse bash 子调度器 |
| posttooluse-dispatcher.js | PostToolUse 顶层调度器 |
| run-with-flags.js | Hook 配置门控包装器（`ECC_HOOK_PROFILE`、`ECC_DISABLED_HOOKS`） |
| run-with-flags-shell.sh | run-with-flags 的 Shell 变体 |
| check-hook-enabled.js | 检查特定 hook 是否被配置/标志启用 |
| plugin-hook-bootstrap.js | 插件模式的 hook 引导 |

### PreToolUse Hook

| 脚本 | 用途 | 匹配器 |
|--------|---------|---------|
| auto-tmux-dev.js | 为长时间运行的开发命令建议使用 tmux | Bash |
| block-no-verify.js | 阻止未经验证的提交 | Bash |
| config-protection.js | 保护关键配置文件免受意外编辑 | Write |
| doc-file-warning.js | 对非标准文档文件创建发出警告 | Write |
| gateguard-fact-force.js | 在声明前强制进行事实核查 | Edit/Write |
| governance-capture.js | 捕获治理决策 | Edit/Write |
| insaits-security-wrapper.js | 敏感操作的安全包装器 | Bash |
| mcp-health-check.js | 使用前检查 MCP 服务器健康状态 | MCP |
| pre-bash-commit-quality.js | 在 `git commit` 前对暂存文件进行 lint 检查并验证提交消息 | Bash |
| pre-bash-dev-server-block.js | 阻止在 tmux 外运行开发服务器 | Bash |
| pre-bash-git-push-reminder.js | 在 git push 前提醒进行代码审查 | Bash |
| pre-bash-tmux-reminder.js | 为长命令建议使用 tmux | Bash |
| pre-compact.js | 上下文压缩前保存状态 | PreCompact |
| pretooluse-visible-output.js | 确保 hook 输出可见 | PreToolUse |
| pre-write-doc-warn.js | 写入文档文件前发出警告 | Write |
| suggest-compact.js | 按间隔建议手动执行 `/compact` | Edit/Write |

### PostToolUse Hook

| 脚本 | 用途 | 匹配器 |
|--------|---------|---------|
| design-quality-check.js | 对通用模板风格的 UI 发出警告 | Edit/Write |
| observe-runner.js | 运行持续学习观察器 | Edit/Write |
| post-bash-build-complete.js | 构建完成后分析构建输出 | Bash |
| post-bash-command-log.js | 记录 bash 命令用于审计 | Bash |
| post-bash-pr-created.js | 在 `gh pr create` 后记录 PR URL | Bash |
| post-edit-accumulator.js | 累积编辑统计数据 | Edit |
| post-edit-console-warn.js | 对编辑文件中的 console.log 发出警告 | Edit |
| post-edit-format.js | 编辑后使用 Prettier/ruff 自动格式化文件 | Edit |
| post-edit-typecheck.js | 编辑 .ts/.tsx 文件后运行类型检查器 | Edit |
| quality-gate.js | 编辑后执行快速质量检查 | Edit/Write |

### 生命周期 Hook

| 脚本 | 用途 | 事件 |
|--------|---------|-------|
| check-console-log.js | 审计修改文件中的 console.log | Stop |
| cost-tracker.js | 发送运行成本遥测数据 | Stop |
| cursor-session-env.js | 设置 Cursor 会话环境 | SessionStart |
| desktop-notify.js | 发送包含任务摘要的桌面通知 | Stop |
| ecc-context-monitor.js | 监控上下文窗口使用情况 | Stop |
| ecc-metrics-bridge.js | 将 ECC 指标桥接到可观测性技术栈 | Stop |
| ecc-statusline.js | 更新 ECC 状态行显示 | Stop |
| evaluate-session.js | 评估会话中可提取的模式 | Stop |
| plan-canvas-sessions.js | 显示待处理的 Plan Canvas 审查 | SessionStart |
| session-activity-tracker.js | 跟踪会话活动指标 | Stop |
| session-end.js | 会话结束清理 | SessionEnd |
| session-end-marker.js | 会话结束生命周期标记 | SessionEnd |
| session-start.js | 加载上次上下文并检测包管理器 | SessionStart |
| session-start-bootstrap.js | 引导会话状态 | SessionStart |
| stop-format-typecheck.js | 停止时组合执行格式化和类型检查 | Stop |

---

## 库模块 (`lib/`)

顶层脚本和 hook 共用的共享模块。

### 核心工具

| 模块 | 用途 |
|--------|---------|
| utils.js | 通用工具函数 |
| package-manager.js | 检测并配置 npm/pnpm/yarn/bun |
| project-detect.js | 检测项目类型和结构 |
| resolve-ecc-root.js | 解析 ECC 安装根路径 |
| resolve-formatter.js | 解析项目代码格式化工具 |
| path-safety.js | 路径验证和清理 |
| shell-split.js | Shell 命令字符串解析 |
| shell-substitution.js | Shell 变量替换 |
| hook-flags.js | Hook 配置和标志管理 |
| llm-summary.js | LLM 驱动的摘要生成 |
| loopback-guard.js | 防止 hook 递归调用 |
| transcript-context.js | 转录上下文提取 |
| feedback-links.js | 生成反馈收集链接 |
| cursor-agent-names.js | Cursor 代理名称解析 |

### 记忆与状态

| 模块 | 用途 |
|--------|---------|
| memory-vault.js | 记忆库核心操作 |
| memory-vault-format.js | 记忆库数据格式处理 |
| state-store/index.js | 基于 SQLite 的状态存储入口 |
| state-store/schema.js | 状态存储数据库模式 |
| state-store/queries.js | 状态存储查询辅助工具 |
| state-store/migrations.js | 状态存储模式迁移 |

### 安装系统

| 模块 | 用途 |
|--------|---------|
| install-executor.js | 执行安装计划 |
| install-lifecycle.js | 安装生命周期管理 |
| install-manifests.js | 安装清单解析 |
| install-state.js | 跟踪安装状态 |
| install/config.js | 安装配置 |
| install/apply.js | 应用安装变更 |
| install/link-rewrite.js | 为安装目标重写链接 |
| install/request.js | 安装请求处理 |
| install/runtime.js | 安装运行时上下文 |
| install/claude-skill-migration.js | 安装期间的技能迁移 |

### 安装目标

| 模块 | 用途 |
|--------|---------|
| install-targets/registry.js | 安装目标注册表 |
| install-targets/helpers.js | 共享安装目标辅助工具 |
| install-targets/claude-home.js | 安装到 `~/.claude/` |
| install-targets/claude-project.js | 安装到项目 `.claude/` |
| install-targets/codex-home.js | 安装到 Codex 主目录 |
| install-targets/cursor-project.js | 安装到 Cursor 项目 |
| install-targets/zed-project.js | 安装到 Zed 项目 |
| install-targets/gemini-project.js | 安装到 Gemini 项目 |
| install-targets/kimi-project.js | 安装到 Kimi 项目 |
| install-targets/codebuddy-project.js | 安装到 CodeBuddy 项目 |
| install-targets/joycode-project.js | 安装到 JoyCode 项目 |
| install-targets/hermes-home.js | 安装到 Hermes 主目录 |
| install-targets/openclaw-home.js | 安装到 OpenClaw 主目录 |
| install-targets/opencode-home.js | 安装到 OpenCode 主目录 |
| install-targets/qwen-home.js | 安装到 Qwen 主目录 |
| install-targets/antigravity-project.js | 安装到 Antigravity 项目 |

### 代理与编排

| 模块 | 用途 |
|--------|---------|
| agent-data-home.js | 解析代理数据主目录 |
| agent-tools.js | 代理工具配置 |
| agent-proximity/index.js | 代理邻近度计算入口 |
| agent-proximity/graph.js | 代理依赖图 |
| agent-proximity/distance.js | 代理距离度量 |
| orchestration-session.js | 编排会话管理 |
| tmux-worktree-orchestrator.js | Tmux + worktree 编排 |
| worktree-lifecycle/lifecycle.js | Git worktree 生命周期管理 |
| worktree-lifecycle/git.js | Git worktree 操作 |

### 会话管理

| 模块 | 用途 |
|--------|---------|
| session-manager.js | 会话 CRUD 操作 |
| session-bridge.js | 跨工具会话桥接 |
| session-aliases.js | 会话别名解析 |
| session-adapters/registry.js | 会话适配器注册表 |
| session-adapters/canonical-session.js | 规范会话格式适配器 |
| session-adapters/claude-history.js | Claude 历史会话适配器 |
| session-adapters/codex-worktree.js | Codex worktree 会话适配器 |
| session-adapters/dmux-tmux.js | dmux/tmux 会话适配器 |
| session-adapters/opencode.js | OpenCode 会话适配器 |
| observer-sessions.js | 观察器会话管理 |

### MCP 与配置

| 模块 | 用途 |
|--------|---------|
| mcp-config.js | MCP 服务器配置管理 |
| mcp-inventory/collect.js | 收集 MCP 服务器清单 |
| mcp-inventory/canonical-mcp.js | 规范 MCP 服务器格式 |
| mcp-inventory/readers/claude-code.js | 读取 Claude Code MCP 配置 |
| mcp-inventory/readers/codex.js | 读取 Codex MCP 配置 |
| mcp-inventory/readers/opencode.js | 读取 OpenCode MCP 配置 |

### 技能演进与改进

| 模块 | 用途 |
|--------|---------|
| skill-evolution/index.js | 技能演进入口 |
| skill-evolution/tracker.js | 跟踪技能使用情况和有效性 |
| skill-evolution/health.js | 技能健康指标 |
| skill-evolution/provenance.js | 技能来源追踪 |
| skill-evolution/versioning.js | 技能版本管理 |
| skill-evolution/dashboard.js | 技能演进仪表盘 |
| skill-improvement/amendify.js | 技能修正生成 |
| skill-improvement/evaluate.js | 评估技能有效性 |
| skill-improvement/health.js | 技能改进健康检查 |
| skill-improvement/observations.js | 收集技能改进观察数据 |

### 控制面板与仪表盘

| 模块 | 用途 |
|--------|---------|
| control-pane/server.js | 控制面板 HTTP 服务器 |
| control-pane/ui.js | 控制面板 UI 渲染 |
| control-pane/state.js | 控制面板状态管理 |
| control-pane/actions.js | 控制面板操作处理器 |
| control-pane/message-sink.js | 控制面板消息处理 |
| control-pane/proximity.js | 控制面板邻近度可视化 |
| control-pane/proximity-viz.js | 邻近度可视化渲染器 |
| control-pane/work-item-mutations.js | 工作项变更处理器 |

### Plan Canvas

| 模块 | 用途 |
|--------|---------|
| plan-canvas/sdk.js | Plan Canvas SDK |
| plan-canvas/server.js | Plan Canvas Web 服务器 |
| plan-canvas/sessions.js | Plan Canvas 会话管理 |
| plan-canvas/markdown.js | Plan Canvas Markdown 处理 |
| plan-canvas/ui.js | Plan Canvas UI 渲染 |

### GitHub 协作

| 模块 | 用途 |
|--------|---------|
| github-coordination.js | GitHub 协作入口 |
| github-coordination/gh-api.js | GitHub API 客户端 |
| github-coordination/actions.js | GitHub 操作处理器 |
| github-coordination/parsing.js | GitHub 数据解析 |
| github-coordination/policy.js | GitHub 协作策略 |
| github-coordination/state.js | GitHub 协作状态 |
| github-coordination/store.js | GitHub 协作持久化 |
| github-discussions.js | GitHub 讨论集成 |

### 其他模块

| 模块 | 用途 |
|--------|---------|
| compute-sponsor.js | 计算赞助追踪 |
| harness-adapter-compliance.js | Harness 适配器合规性检查 |
| ito-environment.js | ITO 环境配置 |
| installer-executor.js | 旧版安装执行器 |

---

## 依赖项

除特别说明外，所有脚本均为 **Node.js >=18** CommonJS（`require`/`module.exports`）。

| 类别 | 运行时 | 外部依赖 |
|----------|---------|---------------|
| 顶层脚本 | Node.js | `better-sqlite3`、`express`（仪表盘） |
| CI 脚本 | Node.js | 无（自包含） |
| Codex 脚本 | Node.js / Bash | Git |
| Hook 脚本 | Node.js | 无（快速，无网络请求） |
| 库模块 | Node.js | `better-sqlite3`（state-store） |
| Shell 脚本 | Bash | Git、标准 Unix 工具 |

## 注意事项

- Hook 脚本在非关键错误时必须以 exit 0 退出（绝不能意外阻塞工具执行）
- Hook 脚本应控制在 200 行以内——将辅助函数提取到 `lib/` 中
- 所有 hook 通过 stdin 接收 JSON，通过 stdout 输出 JSON
- 所有 hook 应使用 `run-with-flags.js` 包装器，以确保配置门控正常工作
- 异步 hook 必须在 hooks.json 中设置 `"async": true`，超时时间不超过 30 秒
