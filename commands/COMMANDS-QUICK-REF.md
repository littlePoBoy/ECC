# 命令快速参考

ECC 插件中全部 56 个命令的自动生成摘要。

## 快速查找

| 命令 | 用途 | 使用场景 |
|------|------|----------|
| `/build-fix` | 检测构建系统并逐步修复构建/类型错误 | 任何语言的构建或类型错误 |
| `/checkpoint` | 创建、验证或列出工作流检查点 | 保存/恢复工作流进度里程碑 |
| `/code-review` | 审查未提交的更改或 GitHub PR（本地模式或 PR 模式） | 提交前或审查 PR 时 |
| `/cost-report` | 从指标日志生成本地 Claude Code 费用报告 | 按天/模型/会话跟踪 Claude Code 费用 |
| `/ecc-guide` | 导航 ECC 的 agents、skills、commands、hooks 和文档 | 为任务找到合适的 ECC 功能入口 |
| `/evolve` | 分析直觉并建议/生成进化的结构 | 将直觉提升为 commands、skills 或 agents |
| `/feature-dev` | 引导式功能开发，强调代码库理解 | 以架构为重点开始新功能开发 |
| `/go-build` | 修复 Go 构建错误、go vet 警告和 linter 问题 | Go 构建/vet/lint 失败 |
| `/go-review` | 全面的 Go 代码审查（惯用写法、并发、安全性） | 编写或提交 Go 代码后 |
| `/go-test` | 使用表驱动测试强制执行 Go 的 TDD 工作流 | 使用 TDD 实现新的 Go 函数 |
| `/harness-audit` | 运行确定性仓库审计并生成评分卡 | 为仓库就绪度跨 12 个类别打分 |
| `/learn` | 从当前会话中提取可复用的模式 | 解决非平凡问题后 |
| `/learn-eval` | 提取、评估并通过质量门控保存模式 | 更高质量的模式提取，带保存/丢弃决策 |
| `/loop-start` | 启动带有安全默认值的托管自主循环 | 运行顺序/连续/无限循环模式 |
| `/loop-status` | 检查活跃循环的状态、进度和失败信号 | 监控正在运行的自主循环 |
| `/model-route` | 为当前任务推荐最佳模型层级 | 在 haiku/sonnet/opus 之间选择 |
| `/orch-add-feature` | 端到端编排新功能构建 | 添加全新功能，完整流水线 |
| `/orch-build-mvp` | 从设计文档编排 MVP 引导 | 将 SDD/PRD 转化为可运行的垂直切片 |
| `/orch-change-feature` | 编排修改现有功能为新行为 | 更改已正常工作的行为 |
| `/orch-fix-defect` | 编排修复缺陷并添加回归测试 | 复现和修复异常/错误行为 |
| `/orch-refine-code` | 编排行为保持的重构 | 不改变行为的前提下重构代码 |
| `/orch-review` | 对 diff 或 PR 运行 orch-review 工作流 | 多维度审查，带对抗性验证 |
| `/plan` | 创建分步实施计划 | 开始功能开发、架构变更、复杂重构 |
| `/plan-canvas` | 在浏览器 Plan Canvas 中打开产物进行审查 | 可视化标注审批的计划审查 |
| `/plan-prd` | 生成精益 PRD 并移交给 /plan | 实施前的需求阶段 |
| `/pr` | 从当前分支创建 GitHub PR | 推送提交并发起拉取请求 |
| `/project-init` | 检测技术栈并生成 ECC 引导计划 | 为新项目配置 ECC |
| `/projects` | 列出已知项目和直觉统计 | 查看 continuous-learning-v2 项目注册表 |
| `/promote` | 将项目级直觉提升为全局范围 | 跨项目共享全局直觉 |
| `/prp-commit` | 使用自然语言文件定位快速提交 | 用自然语言暂存和提交 |
| `/prp-implement` | 带严格验证循环执行计划 | 逐步执行计划文件并持续验证 |
| `/prp-plan` | 带代码库分析的全面计划创建 | 深度 PRP 规划，含模式提取 |
| `/prp-pr` | 创建 GitHub PR（PRP 工作流变体） | 从 PRP 工作流发起 PR |
| `/prp-prd` | 交互式 PRD 生成器，带反复提问 | 问题优先、假设驱动的产品规格 |
| `/python-review` | Python 代码审查（PEP 8、类型提示、安全性） | 编写或提交 Python 代码后 |
| `/quality-gate` | 为单个文件运行 ECC 格式化质量门控 | 通过质量门控 hook 检查格式化 |
| `/react-build` | 修复 React 构建失败（Vite、webpack、Next.js 等） | React/打包器/水合构建错误 |
| `/react-review` | React 代码审查（hooks、RSC、a11y、安全性） | 编写或合并 React 代码前 |
| `/react-test` | 使用 RTL 强制执行 React 的 TDD 工作流 | 使用 TDD 实现 React 组件 |
| `/refactor-clean` | 安全识别并移除死代码 | 通过测试验证清理未使用的代码 |
| `/resume-session` | 加载最近的会话并恢复完整上下文 | 从之前的会话继续工作 |
| `/review-pr` | 使用专业 agents 进行全面 PR 审查 | 多视角 PR 审查 |
| `/rust-build` | 修复 Rust 构建错误、借用检查器问题 | Rust 构建/clippy/fmt 失败 |
| `/rust-review` | Rust 代码审查（所有权、生命周期、unsafe） | 编写或提交 Rust 代码后 |
| `/rust-test` | 强制执行 Rust 的 TDD 工作流 | 使用 TDD 实现新的 Rust 函数 |
| `/santa-loop` | 对抗性双审收敛循环 | 两位独立审查者均需批准方可发布 |
| `/save-session` | 将会话状态保存到带日期的文件 | 会话结束或接近上下文限制前 |
| `/security-scan` | 对 agent/hook/MCP 入口运行 AgentShield | Claude Code 配置的安全审计 |
| `/sessions` | 管理会话历史、别名和元数据 | 列出、加载、设置会话别名 |
| `/setup-pm` | 配置首选包管理器 | 设置 npm/pnpm/yarn/bun 偏好 |
| `/skill-create` | 分析 git 历史以生成 SKILL.md 文件 | 从仓库历史中提取编码模式 |
| `/skill-health` | 显示 skill 组合健康度仪表板 | 查看成功率、失败模式、修正记录 |
| `/test-coverage` | 分析覆盖率并生成缺失的测试 | 达到 80% 以上的测试覆盖率 |
| `/update-codemaps` | 生成精简 token 的架构代码地图 | 为 AI 消费记录项目结构 |
| `/update-docs` | 从真实来源文件同步文档 | 根据代码变更更新文档 |
| `/vue-review` | Vue.js 代码审查（Composition API、响应式、a11y） | 编写或合并 Vue 代码前 |

## 分类

### 规划与设计
- `/plan` - 重新陈述需求、评估风险、创建分步实施计划
- `/plan-prd` - 生成精益 PRD 并移交给 /plan
- `/plan-canvas` - 在浏览器 Plan Canvas 中打开产物进行标注审批审查
- `/prp-plan` - 带代码库分析和模式提取的全面计划创建
- `/prp-prd` - 交互式 PRD 生成器，问题优先、假设驱动的提问
- `/feature-dev` - 引导式功能开发，强调代码库理解

### 开发
- `/build-fix` - 检测构建系统并逐步修复构建/类型错误
- `/go-build` - 修复 Go 构建错误、go vet 警告和 linter 问题
- `/rust-build` - 修复 Rust 构建错误、借用检查器问题和依赖问题
- `/react-build` - 修复 React 构建失败（Vite、webpack、Next.js、CRA、Parcel、esbuild）

### 测试
- `/go-test` - 使用表驱动测试和覆盖率强制执行 Go 的 TDD 工作流
- `/rust-test` - 使用 rstest/proptest/mockall 强制执行 Rust 的 TDD 工作流
- `/react-test` - 使用 React Testing Library 强制执行 React 的 TDD 工作流
- `/test-coverage` - 分析覆盖率、识别缺口、生成缺失的测试

### 审查与质量
- `/code-review` - 审查未提交的更改或 GitHub PR（本地和 PR 模式）
- `/go-review` - Go 代码审查：惯用模式、并发、错误处理
- `/rust-review` - Rust 代码审查：所有权、生命周期、unsafe 使用
- `/python-review` - Python 代码审查：PEP 8、类型提示、安全性
- `/react-review` - React 代码审查：hooks、RSC、a11y、渲染性能
- `/vue-review` - Vue.js 代码审查：Composition API、响应式、模板安全性
- `/review-pr` - 使用专业 agents 的全面 PR 审查
- `/orch-review` - 带对抗性验证工作流的多维度审查
- `/quality-gate` - 为单个文件运行 ECC 格式化质量门控
- `/santa-loop` - 对抗性双审收敛循环（两位独立审查者）

### 编排（orch-* 流水线）
- `/orch-add-feature` - 研究、规划、TDD、审查、提交，用于全新功能
- `/orch-build-mvp` - 使用 GAN 测试框架将 SDD/PRD 转化为可运行的垂直切片
- `/orch-change-feature` - 更改现有功能行为，测试先行
- `/orch-fix-defect` - 将缺陷复现为失败的回归测试，修复至通过
- `/orch-refine-code` - 行为保持的重构，以现有测试套件作为安全网

### Git 与 PR
- `/pr` - 从当前分支创建 GitHub PR，含模板发现
- `/prp-pr` - 创建 GitHub PR（PRP 工作流变体，含产物引用）
- `/prp-commit` - 使用自然语言文件定位快速提交
- `/prp-implement` - 逐步执行计划文件并持续验证
- `/checkpoint` - 创建、验证或列出工作流检查点

### 会话管理
- `/save-session` - 将会话状态保存到 ~/.claude/session-data/ 中带日期的文件
- `/resume-session` - 加载最近的会话并恢复完整上下文
- `/sessions` - 管理会话历史、别名和元数据

### 学习与 Skills
- `/learn` - 从当前会话中提取可复用的模式
- `/learn-eval` - 提取、评估并通过质量门控保存模式
- `/skill-create` - 分析 git 历史以生成 SKILL.md 文件
- `/skill-health` - 显示带分析数据的 skill 组合健康度仪表板
- `/evolve` - 分析直觉并建议/生成进化的结构
- `/promote` - 将项目级直觉提升为全局范围

### 项目设置与导航
- `/project-init` - 检测技术栈并生成 ECC 引导计划
- `/setup-pm` - 配置首选包管理器（npm/pnpm/yarn/bun）
- `/ecc-guide` - 导航 ECC 的 agents、skills、commands、hooks 和文档
- `/projects` - 列出已知项目和直觉统计

### 监控与报告
- `/cost-report` - 生成本地 Claude Code 费用报告
- `/harness-audit` - 运行确定性仓库审计
- `/security-scan` - 运行 AgentShield 安全扫描
- `/loop-start` - 启动带有安全默认值的托管自主循环
- `/loop-status` - 检查活跃循环的状态和失败信号
- `/model-route` - 为当前任务推荐最佳模型层级

### 文档
- `/update-codemaps` - 生成精简 token 的架构代码地图
- `/update-docs` - 从真实来源文件同步文档

---

## 详细命令说明

### /build-fix
- **用途**: 检测项目构建系统并以最小安全更改逐步修复构建/类型错误
- **使用场景**: 构建失败、类型错误、拉取破坏性更改后
- **用法**: `/build-fix`
- **依赖项**: 自动检测构建系统（npm/pnpm/yarn、tsc、cargo、maven、gradle、go、python）

### /checkpoint
- **用途**: 运行验证检查后创建、验证或列出工作流检查点
- **使用场景**: 保存工作流进度、比较里程碑间的状态
- **用法**: `/checkpoint [create|verify|list] [name]`
- **依赖项**: Git

### /code-review
- **用途**: 对本地未提交更改或 GitHub PR 进行代码审查，含安全和质量检查
- **使用场景**: 提交前、审查 PR、代码库入门了解
- **用法**: `/code-review [pr-number | pr-url | 留空表示本地审查]`
- **依赖项**: `gh` CLI（PR 模式）、项目的 lint/test/build 工具

### /cost-report
- **用途**: 从 cost-tracker 指标日志按天、模型和会话汇总本地 Claude Code 费用
- **使用场景**: 跟踪 Claude Code 费用、导出费用数据
- **用法**: `/cost-report [csv]`
- **依赖项**: `~/.claude/metrics/costs.jsonl`（来自 stop:cost-tracker hook）

### /ecc-guide
- **用途**: Everything Claude Code 的对话式地图，帮助发现适合任务的功能入口
- **使用场景**: 探索 ECC 功能、查找合适的 command/skill/agent
- **用法**: `/ecc-guide [setup|skills|commands|hooks|install|find: <query>]`
- **依赖项**: ECC 仓库文件（README.md、AGENTS.md、agent.yaml 等）

### /evolve
- **用途**: 分析直觉并建议或生成进化的结构（commands、skills、agents）
- **使用场景**: 当直觉聚集成值得提升的更高层级模式时
- **用法**: `/evolve [--generate]`
- **依赖项**: continuous-learning-v2 直觉 CLI、Python 3

### /feature-dev
- **用途**: 结构化的功能开发工作流，强调在编写代码前先理解代码库
- **使用场景**: 以架构为重点开始新功能开发
- **用法**: `/feature-dev`
- **依赖项**: code-explorer、code-architect、code-reviewer agents

### /go-build
- **用途**: 逐步修复 Go 构建错误、go vet 警告和 linter 问题
- **使用场景**: `go build` 失败、vet 问题、lint 警告、依赖损坏
- **用法**: `/go-build`
- **依赖项**: go-build-resolver agent、Go 工具链

### /go-review
- **用途**: 全面的 Go 代码审查：惯用模式、并发安全、错误处理、安全性
- **使用场景**: 编写或修改 Go 代码后、提交前
- **用法**: `/go-review`
- **依赖项**: go-reviewer agent、Go 工具链

### /go-test
- **用途**: 使用表驱动测试强制执行 Go 的 TDD 工作流
- **使用场景**: 实现新的 Go 函数、添加测试覆盖率、修复缺陷
- **用法**: `/go-test [description]`
- **依赖项**: golang-patterns、tdd-workflow skills

### /harness-audit
- **用途**: 运行确定性仓库审计并返回优先级评分卡（最多 12 个类别）
- **使用场景**: 为仓库就绪度打分、识别 ECC 采用差距
- **用法**: `/harness-audit [scope] [--format text|json] [--root path]`
- **依赖项**: `scripts/harness-audit.js`

### /learn
- **用途**: 从当前会话中提取可复用的模式并保存为候选 skills
- **使用场景**: 解决了值得记住的非平凡问题后
- **用法**: `/learn`
- **依赖项**: 无

### /learn-eval
- **用途**: 提取、通过质量门控评估，然后保存模式（/learn 的扩展）
- **使用场景**: 更高质量的模式提取，带保存/丢弃/吸收决策
- **用法**: `/learn-eval`
- **依赖项**: 现有 skills（用于重叠检查）

### /loop-start
- **用途**: 启动带有安全默认值的托管自主循环模式
- **使用场景**: 运行顺序、continuous-pr、rfc-dag 或无限循环模式
- **用法**: `/loop-start [pattern] [--mode safe|fast]`
- **依赖项**: ECC hook 配置文件、测试套件

### /loop-status
- **用途**: 检查活跃循环的状态、进度、失败信号和建议干预措施
- **使用场景**: 监控正在运行的自主循环、调试卡住的会话
- **用法**: `/loop-status [--watch]`
- **依赖项**: Claude 会话 JSONL 文件

### /model-route
- **用途**: 基于复杂度、风险和预算为当前任务推荐最佳模型层级
- **使用场景**: 在 haiku/sonnet/opus 之间选择以优化成本
- **用法**: `/model-route [task-description] [--budget low|med|high]`
- **依赖项**: 无

### /orch-add-feature
- **用途**: 端到端编排新功能构建（研究、规划、TDD、审查、门控提交）
- **使用场景**: 为项目添加全新功能
- **用法**: `/orch-add-feature <要添加的内容>`
- **依赖项**: orch-add-feature skill、orch-pipeline 引擎

### /orch-build-mvp
- **用途**: 从设计/规格文档编排引导可工作的 MVP
- **使用场景**: 将 SDD/PRD 转化为可运行的垂直切片
- **用法**: `/orch-build-mvp <设计/规格文档路径>`
- **依赖项**: orch-build-mvp skill、orch-pipeline 引擎、GAN 测试框架

### /orch-change-feature
- **用途**: 编排修改现有功能为新的期望行为（测试先行）
- **使用场景**: 功能可用但行为应有所不同（非缺陷，非新功能）
- **用法**: `/orch-change-feature <新的期望行为>`
- **依赖项**: orch-change-feature skill、orch-pipeline 引擎

### /orch-fix-defect
- **用途**: 编排修复缺陷，将其复现为失败的回归测试，然后修复至通过
- **使用场景**: 行为异常/错误
- **用法**: `/orch-fix-defect <异常描述>`
- **依赖项**: orch-fix-defect skill、orch-pipeline 引擎

### /orch-refine-code
- **用途**: 编排行为保持的重构，以现有测试套件作为安全网
- **使用场景**: 不改变行为的前提下重构代码
- **用法**: `/orch-refine-code <重构内容>`
- **依赖项**: orch-refine-code skill、orch-pipeline 引擎、refactor-cleaner agent

### /orch-review
- **用途**: 对 diff 运行 orch-review 原生工作流，含多维度审查和对抗性验证
- **使用场景**: 使用结构化维度审查本地更改或 GitHub PR
- **用法**: `/orch-review [pr-number | pr-url | 留空表示本地]`
- **依赖项**: `gh` CLI（PR 模式）、orch-review 工作流

### /plan
- **用途**: 重新陈述需求、评估风险、创建分步实施计划（等待确认）
- **使用场景**: 开始新功能、架构变更、复杂重构
- **用法**: `/plan [功能描述 | path/to/*.prd.md]`
- **依赖项**: 可选 planner agent

### /plan-canvas
- **用途**: 在浏览器 Plan Canvas 中打开计划或 HTML 产物进行标注审批审查
- **使用场景**: 实施前对计划产物进行可视化审查
- **用法**: `/plan-canvas [path/to/artifact.plan.md | path/to/artifact.html]`
- **依赖项**: plan-canvas skill、`scripts/plan-canvas.js`

### /plan-prd
- **用途**: 生成精益的、问题优先的 PRD，并移交给 /plan 进行实施规划
- **使用场景**: 实施前的需求阶段
- **用法**: `/plan-prd [产品/功能想法]`
- **依赖项**: 无（移交给 /plan）

### /pr
- **用途**: 从当前分支创建 GitHub PR，含模板发现、提交分析和推送
- **使用场景**: 完成工作后发起拉取请求
- **用法**: `/pr [base-branch] [--draft]`
- **依赖项**: `gh` CLI、Git

### /project-init
- **用途**: 检测项目技术栈并生成 ECC 引导计划（干运行模式）
- **使用场景**: 为新项目配置 ECC
- **用法**: `/project-init [--dry-run] [--target claude|cursor] [--skills ...]`
- **依赖项**: ECC 安装脚本（`scripts/install-plan.js`、`scripts/install-apply.js`）

### /projects
- **用途**: 列出已知项目及其直觉/观察计数
- **使用场景**: 查看 continuous-learning-v2 项目注册表
- **用法**: `/projects`
- **依赖项**: continuous-learning-v2 直觉 CLI、Python 3

### /promote
- **用途**: 将项目级直觉提升为全局范围
- **使用场景**: 跨项目共享全局直觉
- **用法**: `/promote [instinct-id] [--force] [--dry-run]`
- **依赖项**: continuous-learning-v2 直觉 CLI、Python 3

### /prp-commit
- **用途**: 使用自然语言文件定位快速提交
- **使用场景**: 用自然语言描述进行暂存和提交
- **用法**: `/prp-commit [target description]`
- **依赖项**: Git

### /prp-implement
- **用途**: 带严格验证循环执行实施计划（类型检查、lint、测试、构建、集成）
- **使用场景**: 逐步执行计划文件并持续验证
- **用法**: `/prp-implement <path/to/plan.md>`
- **依赖项**: 项目验证命令（type-check、lint、test、build）

### /prp-plan
- **用途**: 创建全面的、自包含的实施计划，含完整代码库模式提取
- **使用场景**: 带代码库智能采集的深度规划
- **用法**: `/prp-plan <功能描述 | path/to/prd.md>`
- **依赖项**: 无（如提供则读取 PRD）

### /prp-pr
- **用途**: 从当前分支创建 GitHub PR（PRP 工作流变体，含产物引用）
- **使用场景**: 从 PRP 工作流发起 PR
- **用法**: `/prp-pr [base-branch] [--draft]`
- **依赖项**: `gh` CLI、Git

### /prp-prd
- **用途**: 交互式 PRD 生成器，带问题优先、假设驱动的反复提问
- **使用场景**: 通过反复发现创建产品需求文档
- **用法**: `/prp-prd [功能/产品想法]`
- **依赖项**: 无

### /python-review
- **用途**: 全面的 Python 代码审查：PEP 8、类型提示、安全性、Pythonic 惯用写法
- **使用场景**: 编写或提交 Python 代码后
- **用法**: `/python-review`
- **依赖项**: python-reviewer agent、Python 工具链（ruff、mypy、black、bandit）

### /quality-gate
- **用途**: 为单个文件运行 ECC 格式化质量门控
- **使用场景**: 通过质量门控 hook 检查格式化
- **用法**: `/quality-gate [path]`
- **依赖项**: `scripts/hooks/quality-gate.js`、格式化工具（Biome、Prettier、gofmt、ruff）

### /react-build
- **用途**: 修复 Vite、webpack、Next.js、CRA、Parcel、esbuild、Bun 的 React 构建失败
- **使用场景**: JSX/TSX 编译错误、水合不匹配、服务端/客户端边界失败
- **用法**: `/react-build`
- **依赖项**: react-build-resolver agent

### /react-review
- **用途**: React 代码审查：hook 正确性、渲染性能、RSC 边界、无障碍性
- **使用场景**: 编写或合并 React 代码前
- **用法**: `/react-review`
- **依赖项**: react-reviewer agent、typescript-reviewer agent（配套）

### /react-test
- **用途**: 使用 React Testing Library 配合 Vitest/Jest 强制执行 React 的 TDD 工作流
- **使用场景**: 使用 TDD 实现 React 组件或 hooks
- **用法**: `/react-test [description]`
- **依赖项**: react-testing、tdd-workflow skills

### /refactor-clean
- **用途**: 安全识别并移除死代码，每次更改后进行验证
- **使用场景**: 清理未使用的代码、依赖和导出
- **用法**: `/refactor-clean`
- **依赖项**: 死代码检测工具（knip、depcheck、ts-prune、vulture、deadcode）

### /resume-session
- **用途**: 加载最近的会话文件并恢复完整上下文继续工作
- **使用场景**: 开始新会话以继续之前的工作
- **用法**: `/resume-session [date | path]`
- **依赖项**: ~/.claude/session-data/ 中的会话文件

### /review-pr
- **用途**: 使用多个专业 agents 进行全面 PR 审查
- **使用场景**: 对拉取请求进行多视角审查
- **用法**: `/review-pr [PR-number-or-URL] [--focus=comments|tests|errors|types|code|simplify]`
- **依赖项**: code-reviewer、pr-test-analyzer、silent-failure-hunter、type-design-analyzer、code-simplifier agents

### /rust-build
- **用途**: 逐步修复 Rust 构建错误、借用检查器问题和依赖问题
- **使用场景**: cargo build/check 失败、clippy 警告、借用检查器错误
- **用法**: `/rust-build`
- **依赖项**: rust-build-resolver agent、Rust 工具链

### /rust-review
- **用途**: Rust 代码审查：所有权、生命周期、错误处理、unsafe 使用
- **使用场景**: 编写或提交 Rust 代码后
- **用法**: `/rust-review`
- **依赖项**: rust-reviewer agent、Rust 工具链

### /rust-test
- **用途**: 使用 #[test]、rstest、proptest、mockall 强制执行 Rust 的 TDD 工作流
- **使用场景**: 使用 TDD 实现新的 Rust 函数
- **用法**: `/rust-test [description]`
- **依赖项**: rust-testing、rust-patterns skills

### /santa-loop
- **用途**: 对抗性双审收敛循环 -- 两位独立审查者均需批准方可通过
- **使用场景**: 发布前的高置信度代码审查
- **用法**: `/santa-loop [file-or-glob | description]`
- **依赖项**: code-reviewer agent (Opus)、Codex CLI 或 Gemini CLI（用于模型多样性）

### /save-session
- **用途**: 将当前会话状态保存到带日期的文件，以便将来恢复
- **使用场景**: 会话结束、接近上下文限制前、解决复杂问题后
- **用法**: `/save-session`
- **依赖项**: 无（写入 ~/.claude/session-data/）

### /security-scan
- **用途**: 对 agent、hook、MCP、权限和密钥入口运行 AgentShield
- **使用场景**: Claude Code 配置的安全审计
- **用法**: `/security-scan [path] [--format text|json|markdown|html] [--min-severity ...] [--fix]`
- **依赖项**: ecc-agentshield 扫描器、security-reviewer agent

### /sessions
- **用途**: 管理 Claude Code 会话历史、别名和会话元数据
- **使用场景**: 列出、加载、设置别名或检查会话
- **用法**: `/sessions [list|load|alias|info|help] [options]`
- **依赖项**: scripts/lib/session-manager.js、scripts/lib/session-aliases.js

### /setup-pm
- **用途**: 配置首选包管理器（npm/pnpm/yarn/bun）
- **使用场景**: 设置或更改包管理器偏好
- **用法**: `/setup-pm`
- **依赖项**: scripts/setup-package-manager.js

### /skill-create
- **用途**: 分析本地 git 历史以提取编码模式并生成 SKILL.md 文件
- **使用场景**: 从仓库历史中提取团队约定
- **用法**: `/skill-create [--commits N] [--output path] [--instincts]`
- **依赖项**: Git、可选 continuous-learning-v2

### /skill-health
- **用途**: 显示 skill 组合健康度仪表板，含成功率、失败模式和修正记录
- **使用场景**: 监控 skill 质量、识别退化的 skills
- **用法**: `/skill-health [--panel failures] [--json]`
- **依赖项**: scripts/skills-health.js

### /test-coverage
- **用途**: 分析测试覆盖率、识别缺口，生成缺失的测试以达到 80% 以上阈值
- **使用场景**: 提高测试覆盖率、识别未测试的代码路径
- **用法**: `/test-coverage`
- **依赖项**: 项目测试框架（jest、vitest、pytest、cargo-llvm-cov、go test、JaCoCo）

### /update-codemaps
- **用途**: 扫描项目结构并生成精简 token 的架构代码地图
- **使用场景**: 为 AI 上下文消费记录项目结构
- **用法**: `/update-codemaps`
- **依赖项**: 无

### /update-docs
- **用途**: 从真实来源文件（脚本、模式、路由、导出）同步文档
- **使用场景**: 代码更改后更新文档、检查过时文档
- **用法**: `/update-docs`
- **依赖项**: 无

### /vue-review
- **用途**: Vue.js 代码审查：Composition API 正确性、响应式、可组合模式、模板安全性
- **使用场景**: 编写或合并 Vue 代码前
- **用法**: `/vue-review`
- **依赖项**: vue-reviewer agent、typescript-reviewer agent（配套）
