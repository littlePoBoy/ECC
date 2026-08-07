# 工作流快速参考

ECC 插件中所有工作流的自动生成摘要。

## 快速查找

| 工作流 | 用途 | 使用代理 |
|--------|------|----------|
| orch-review | 多维度代码审查，对 CRITICAL/HIGH 发现进行对抗性验证 | ecc:code-reviewer, ecc:<language>-reviewer, ecc:security-reviewer |

## 详细工作流说明

### orch-review.workflow.js

- **用途**: 作为 Claude Code 原生工作流执行 ECC 审查阶段。执行多维度审查（质量 + 语言 + 条件安全），然后对每个 CRITICAL/HIGH 发现进行对抗性验证。返回阻断性发现和建议性发现，供 orch-pipeline 的 Gate 2 使用。

- **阶段**:
  1. **审查 (Review)** — 每个维度启动一个审查代理并行运行。维度包括：正确性与质量（始终执行）、语言特定惯用法与陷阱（当指定语言时）、安全/OWASP（当 diff 或变更文件路径匹配安全敏感模式时）。
  2. **去重 (Dedup)** — 所有维度的发现通过标准化证据片段进行合并。每个保留的发现记录了哪些维度报告了它，并保留最严格的严重级别。
  3. **验证 (Verify)** — 每个唯一的 CRITICAL/HIGH 发现交由独立的对抗性验证器处理，该验证器在不确定时默认驳回。MEDIUM/LOW 发现作为建议性发现直接通过。

- **使用代理**:
  - `ecc:code-reviewer` — 始终运行，负责正确性与质量审查
  - `ecc:<language>-reviewer` — 条件执行；从语言到代理的映射中选择（typescript, python, go, rust, java, kotlin, swift, php, csharp, fsharp, react, vue, flutter, dart, django, fastapi, cpp）
  - `ecc:security-reviewer` — 条件执行；当 diff 或变更文件路径匹配安全敏感模式（auth, tokens, SQL, crypto, file system ops, external calls 等）时触发

- **调用方式**: 通过主对话循环中的 Claude Code Workflow 工具调用。`/orch-review` 命令（`commands/orch-review.md`）是面向用户的入口。

  ```jsonc
  Workflow({
    scriptPath: "workflows/orch-review.workflow.js",
    args: {
      diff: "<unified git diff text>",   // 必填
      language: "typescript",            // 可选 — 选择语言审查代理
      changedFiles: ["src/auth.ts"]      // 可选 — 供安全触发器评估
    }
  })
  ```

- **依赖项**:
  - 需要有效的 unified diff 字符串（`args.diff`）；缺失或为空时执行失败关闭策略
  - 可选的 `args.language` 字符串，用于选择语言特定的审查代理
  - 可选的 `args.changedFiles` 字符串路径数组，用于安全触发器评估
  - 依赖 ECC 代理定义（`ecc:code-reviewer`、`ecc:security-reviewer` 及语言特定审查器）已安装
  - 使用 Claude Code 原生 Workflow 引擎的 `parallel()` 执行并发代理，`agent()` 用于生成具有结构化输出验证的子代理

- **返回值**:

  ```jsonc
  {
    "verdict": "APPROVE" | "CHANGES_REQUESTED",
    "incomplete": false,
    "failedDimensions": [ /* { dimension, error } */ ],
    "blocking": [ /* 已确认的 CRITICAL/HIGH + 无法验证的发现 */ ],
    "advisory": [ /* MEDIUM/LOW + 已驳回的发现 */ ],
    "stats": { "dimensions", "failed", "raw", "unique", "confirmed", "unverified", "uncertain", "refuted" }
  }
  ```

- **设计说明**:
  - 每个阶段均执行失败关闭策略：若审查代理崩溃，该维度记录在 `failedDimensions` 中（裁决永远不会是干净的 APPROVE）；若验证器崩溃，阻断项保留在 `blocking` 中
  - 审查到去重的屏障机制防止验证器对同一缺陷跨维度重复运行
  - 仅当验证器以高置信度（confidence >= 0.8）证明某发现为误报时，才将其从 blocking 中移除
  - 包含提示词防御机制：审查器和验证器的提示词明确将 diff 标记为不可信输入，并指示代理忽略嵌入的指令
