# 技能快速参考

ECC 插件中所有 113 个技能的自动生成摘要。

## 快速查找

| 技能 | 用途 | 使用场景 |
|------|------|----------|
| agent-architecture-audit | Agent 和 LLM 应用的全栈诊断工具 | 审查 12 层 Agent 架构栈 |
| agent-eval | 编码代理的正面对比评测 | 比较 Claude Code、Aider、Codex 等代理 |
| agent-harness-construction | 设计和优化 AI Agent 动作空间 | 优化工具定义和观察格式 |
| agent-introspection-debugging | AI Agent 故障的结构化自调试工作流 | 捕获、诊断、恢复和内省报告 |
| agent-self-evalulation | 完成任务后的自我评估 | 5 个维度自评：准确性、完整性、清晰度、可操作性、简洁性 |
| agent-sort | 为特定仓库构建 ECC 安装计划 | 项目只需要 ECC 的子集 |
| agentic-engineering | 以 Agent 化工程师身份工作 | 评估优先执行、分解、成本感知路由 |
| agentic-os | 构建持久化多 Agent 操作系统 | 内核架构、专业代理、文件记忆 |
| autonomous-agent-harness | 将 Claude Code 转为完全自主 Agent 系统 | 持久记忆、定时操作、任务队列 |
| autonomous-loops | 自主 Claude Code 循环模式和架构 | 无干预开发工作流 |
| claude-devfleet | 通过 Claude DevFleet 编排多 Agent 任务 | 并行派发多个 Agent 到隔离 worktree |
| continuous-agent-loop | 持续自主 Agent 循环模式 | 质量门控、评估、恢复控制 |
| dynamic-workflow-mode | 设计任务本地 harness | 评估门控、可复用技能提取 |
| loop-design-check | 设计目标导向的 Agent 循环 | 检查循环失败模式 |
| orch-add-feature | 端到端编排构建全新功能 | 添加不存在的功能 |
| orch-build-mvp | 从设计文档编排构建 MVP | 有设计/规格文档时 |
| orch-change-feature | 编排修改现有功能行为 | 功能正常但需要改变行为 |
| orch-fix-defect | 编排修复 Bug | 行为错误或崩溃 |
| orch-pipeline | orch-* 技能族的共享编排引擎 | 被其他 orch-* 技能间接加载 |
| orch-refine-code | 编排行为保持的重构 | 结构改进但行为不变 |
| parallel-execution-optimizer | 通过并行工作加速任务 | 并发代理、批量工具调用 |
| plan-orchestrate | 读取计划文档，分解步骤 | 多步骤计划的编排 |
| team-agent-orchestration | 团队化 Agent 编排 | 工作项、所有权、Agent 看板 |
| team-builder | 交互式 Agent 选择器 | 组合并派发并行团队 |
| ai-regression-testing | AI 辅助开发的回归测试策略 | 沙盒模式 API 测试 |
| benchmark | 测量性能基线 | PR 前后性能对比 |
| benchmark-methodology | 竞品评分方法论 | 9 维度加权评分 |
| benchmark-optimization-loop | 递归优化和基准测试 | 尝试多种变体选择最佳 |
| delivery-gate | 阻止 Claude 完成直到质量检查通过 | 检测合理化模式 |
| e2e-testing | Playwright E2E 测试模式 | 页面对象模型、CI/CD 集成 |
| eval-harness | Claude Code 会话的正式评估框架 | 评估驱动开发 (EDD) |
| plankton-code-quality | 使用 Plankton 的写时代码质量强制 | 每次编辑自动格式化和 lint |
| tdd-workflow | 测试驱动开发工作流 | 新功能、Bug 修复、重构 |
| verification-loop | Claude Code 会话的综合验证系统 | 功能完成后、PR 创建前 |
| accessibility | 使用 WCAG 2.2 AA 级设计无障碍产品 | UI 组件规范、审计 |
| safety-guard | 防止生产系统上的破坏性操作 | 自主代理运行时 |
| security-review | 安全审查技能 | 认证、用户输入、密钥、API 端点 |
| security-scan | 扫描 .claude/ 目录安全漏洞 | 配置错误、注入风险 |
| springboot-security | Spring Security 最佳实践 | 认证授权、CSRF、密钥 |
| design-system | 生成或审计设计系统 | 视觉一致性检查 |
| frontend-design-direction | 设置前端设计方向 | 生产 UI 工作 |
| frontend-patterns | 前端开发模式 | React、Next.js、状态管理 |
| frontend-slides | 创建动画丰富的 HTML 演示文稿 | PPT 转 Web |
| react-native-patterns | React Native 和 Expo 应用模式 | Expo Router、状态分离 |
| react-patterns | React 18/19 模式 | Hooks 纪律、服务端/客户端组件边界 |
| react-performance | React 和 Next.js 性能优化模式 | Vercel 工程最佳实践 |
| react-testing | React 组件测试 | Testing Library、Vitest/Jest、MSW |
| vite-patterns | Vite 构建工具模式 | 配置、插件、HMR、SSR |
| vue-patterns | Vue.js 3 Composition API 模式 | 组件架构、Pinia 状态管理 |
| browser-qa | 自动化视觉测试和 UI 交互验证 | 部署后验证 |
| click-path-audit | 追踪每个用户按钮的完整状态变更 | 用户报告 UI 故障但调试无果 |
| api-design | REST API 设计模式 | 资源命名、分页、过滤、错误响应 |
| backend-patterns | 后端架构模式 | Node.js、Express、Next.js API |
| database-migrations | 数据库迁移最佳实践 | Schema 变更、数据迁移、回滚 |
| deployment-patterns | 部署工作流模式 | CI/CD、Docker、健康检查 |
| docker-patterns | Docker 和 Docker Compose 模式 | 本地开发、容器安全 |
| postgres-patterns | PostgreSQL 数据库模式 | 查询优化、Schema 设计、索引 |
| redis-patterns | Redis 数据结构模式 | 缓存策略、分布式锁、限流 |
| bun-runtime | Bun 运行时 | 包管理器、打包器、测试运行器 |
| coding-standards | 跨项目编码规范 | 命名、可读性、不可变性 |
| error-handling | 跨语言错误处理模式 | TypeScript、Python、Go |
| golang-patterns | Go 惯用模式 | 最佳实践和约定 |
| golang-testing | Go 测试模式 | 表驱动测试、子测试、基准测试 |
| java-coding-standards | Java 编码标准 | Spring Boot 和 Quarkus 服务 |
| jpa-patterns | JPA/Hibernate 模式 | 实体设计、关系、查询优化 |
| python-patterns | Python 惯用风格 | PEP 8、类型提示、最佳实践 |
| python-testing | Python 测试策略 | pytest、TDD、fixtures、mocking |
| rust-patterns | Rust 惯用模式 | 所有权、错误处理、trait、并发 |
| rust-testing | Rust 测试模式 | 单元测试、集成测试、异步测试 |
| springboot-patterns | Spring Boot 架构模式 | REST API、分层服务、数据访问 |
| springboot-tdd | Spring Boot 测试驱动开发 | JUnit 5、Mockito、Testcontainers |
| springboot-verification | Spring Boot 验证循环 | 构建、静态分析、测试覆盖率 |
| architecture-decision-records | 捕获架构决策为结构化 ADR | 自动检测决策时刻 |
| blueprint | 将一行目标转为多会话构建计划 | 多 PR 任务、跨会话重构 |
| council | 召集四声议会处理模糊决策 | 多路径无明显赢家时 |
| deep-research | 多源深度研究 | firecrawl 和 exa MCP |
| exa-search | 通过 Exa MCP 的神经搜索 | Web、代码、公司研究 |
| plan-canvas | 在本地浏览器画布中打开计划 | 人工标注、审批 |
| product-lens | 在构建前验证"为什么" | 产品诊断、方向验证 |
| search-first | 编码前研究工作流 | 搜索现有工具和库 |
| recursive-decision-ledger | 递归决策账本 | 重复展开、标记决策过程 |
| configure-ecc | ECC 交互式安装器 | 引导选择和安装技能 |
| code-tour | 创建 CodeTour 文件 | 代码导览、架构走查 |
| codebase-onboarding | 分析代码库生成入门指南 | 首次打开项目 |
| codehealth-mcp | 通过 CodeScene MCP 实时代码健康 | 重构前审查、变更后验证 |
| config-gc | Claude Code 配置垃圾回收 | 清理冗余、过时配置 |
| context-budget | 审计上下文窗口消耗 | 识别臃肿组件 |
| ecc-guide | 引导用户了解 ECC 功能 | 查找技能、命令、代理 |
| ecc-recipes | 将工作流映射到 ECC 命令组 | 命令组配方族 |
| hookify-rules | 创建 hookify 规则 | Hook 规则语法和模式 |
| prompt-optimizer | 分析和优化原始 prompt | 识别意图、匹配 ECC 组件 |
| repo-scan | 跨栈源代码资产审计 | 分类每个文件、检测嵌入库 |
| rules-distill | 从技能中提取规则 | 跨领域原则提炼 |
| skill-comply | 可视化技能/规则/代理定义是否被遵循 | 自动场景生成 |
| skill-stocktake | 审计 Claude 技能和命令质量 | 快速扫描和完整盘点 |
| token-budget-advisor | 提供响应深度选择 | 控制响应长度和 token 预算 |
| content-hash-cache-pattern | 使用 SHA-256 内容哈希缓存 | 文件处理管道 |
| cost-aware-llm-pipeline | LLM API 成本优化模式 | 模型路由、预算跟踪 |
| data-throughput-accelerator | 加速大数据摄取 | ETL、仓库加载 |
| latency-critical-systems | 延迟敏感系统 | 实时仪表板、市场数据 |
| strategic-compact | 在逻辑间隔建议手动压缩 | 保持上下文 |
| ck | Claude Code 持久化项目记忆 | 会话启动时自动加载 |
| continuous-learning | [已弃用] 遗留 v1 技能提取器 | 使用 continuous-learning-v2 |
| continuous-learning-v2 | 基于直觉的学习系统 | 观察会话、创建原子直觉 |
| unified-memory | 跨代理共享持久化上下文 | Claude、Codex、Hermes、Cursor |
| canary-watch | 部署后监控和验证 URL | HTTP 端点、SSE 流、静态资源 |
| github-ops | GitHub 仓库操作和管理 | Issue 分类、PR 管理、CI/CD |
| git-workflow | Git 工作流模式 | 分支策略、提交约定 |
| opensource-pipeline | 开源管道 | Fork、清理、打包私有项目 |
| ai-first-engineering | AI 优先工程运营模型 | AI Agent 生成大量实现输出 |
| mle-workflow | 生产机器学习工程工作流 | 数据合约、训练、评估、部署 |
| gateguard | 事实强制门控 | 阻止 Edit/Write/Bash 直到调查 |
| santa-method | 多 Agent 对抗式验证 | 收敛循环、两个独立审查代理 |

## 分类

### 编排与代理

- **agent-architecture-audit** - Agent 和 LLM 应用的全栈诊断工具。审查 12 层 Agent 架构栈
- **agent-eval** - 编码代理的正面对比评测，带通过率、成本、时间指标
- **agent-harness-construction** - 设计和优化 AI Agent 动作空间、工具定义
- **agent-introspection-debugging** - AI Agent 故障的结构化自调试工作流
- **agent-self-evalulation** - 完成任务后的 5 维度自我评估
- **agent-sort** - 为特定仓库构建证据支持的 ECC 安装计划
- **agentic-engineering** - 以 Agent 化工程师身份工作：评估优先、分解、成本感知
- **agentic-os** - 构建持久化多 Agent 操作系统
- **autonomous-agent-harness** - 将 Claude Code 转为完全自主 Agent 系统
- **autonomous-loops** - 自主 Claude Code 循环模式和架构
- **claude-devfleet** - 通过 Claude DevFleet 编排多 Agent 编码任务
- **continuous-agent-loop** - 持续自主 Agent 循环模式，带质量门控
- **dynamic-workflow-mode** - 设计任务本地 harness 和可复用技能提取
- **loop-design-check** - 设计目标导向的 Agent 循环并审查失败模式
- **orch-add-feature** - 端到端编排构建全新功能
- **orch-build-mvp** - 从设计文档编排构建工作 MVP
- **orch-change-feature** - 编排修改现有功能行为
- **orch-fix-defect** - 编排修复 Bug：复现、修复、审查、门控提交
- **orch-pipeline** - orch-* 技能族的共享编排引擎
- **orch-refine-code** - 编排行为保持的重构
- **parallel-execution-optimizer** - 通过并行工作加速任务
- **plan-orchestrate** - 读取计划文档，设计每步 Agent 链
- **team-agent-orchestration** - 团队化 Agent 编排
- **team-builder** - 交互式 Agent 选择器，组合并行团队

### 质量与测试

- **ai-regression-testing** - AI 辅助开发的回归测试策略
- **benchmark** - 测量性能基线，检测 PR 前后回归
- **benchmark-methodology** - 竞品评分方法论，9 维度加权
- **benchmark-optimization-loop** - 递归优化和基准测试循环
- **delivery-gate** - Stop hook 阻止完成直到质量检查通过
- **e2e-testing** - Playwright E2E 测试模式和 CI/CD 集成
- **eval-harness** - 评估驱动开发 (EDD) 正式框架
- **plankton-code-quality** - 使用 Plankton 的写时代码质量强制
- **tdd-workflow** - 测试驱动开发，80%+ 覆盖率
- **verification-loop** - Claude Code 会话的综合验证系统

### 安全与防护

- **accessibility** - 使用 WCAG 2.2 AA 级设计无障碍产品
- **safety-guard** - 防止生产系统上的破坏性操作
- **security-review** - 安全审查：认证、输入处理、密钥、API
- **security-scan** - 使用 AgentShield 扫描 .claude/ 目录安全漏洞
- **springboot-security** - Spring Security 最佳实践

### 前端与 UI

- **design-system** - 生成或审计设计系统
- **frontend-design-direction** - 设置 ECC 前端设计方向
- **frontend-patterns** - 前端开发模式：React、Next.js、状态管理
- **frontend-slides** - 创建动画丰富的 HTML 演示文稿
- **react-native-patterns** - React Native 和 Expo 应用模式
- **react-patterns** - React 18/19 模式
- **react-performance** - React 和 Next.js 性能优化模式
- **react-testing** - React 组件测试
- **vite-patterns** - Vite 构建工具模式
- **vue-patterns** - Vue.js 3 Composition API 模式
- **browser-qa** - 自动化视觉测试和 UI 交互验证
- **click-path-audit** - 追踪每个用户按钮的完整状态变更序列

### 后端与基础设施

- **api-design** - REST API 设计模式
- **backend-patterns** - 后端架构模式
- **database-migrations** - 数据库迁移最佳实践
- **deployment-patterns** - 部署工作流和 CI/CD 管道模式
- **docker-patterns** - Docker 和 Docker Compose 模式
- **postgres-patterns** - PostgreSQL 数据库模式
- **redis-patterns** - Redis 数据结构和缓存模式
- **bun-runtime** - Bun 运行时、包管理器、打包器

### 语言特定模式

- **coding-standards** - 跨项目编码规范基线
- **error-handling** - 跨语言错误处理模式（TS/Python/Go）
- **golang-patterns** - Go 惯用模式和最佳实践
- **golang-testing** - Go 测试模式：表驱动、子测试、基准
- **java-coding-standards** - Java 编码标准（Spring Boot/Quarkus）
- **jpa-patterns** - JPA/Hibernate 实体设计和查询优化
- **python-patterns** - Python 惯用风格、PEP 8、类型提示
- **python-testing** - Python 测试策略：pytest、TDD
- **rust-patterns** - Rust 惯用模式：所有权、错误处理、trait
- **rust-testing** - Rust 测试模式：单元、集成、异步
- **springboot-patterns** - Spring Boot 架构模式
- **springboot-tdd** - Spring Boot 测试驱动开发
- **springboot-verification** - Spring Boot 验证循环

### 研究与规划

- **architecture-decision-records** - 捕获架构决策为结构化 ADR
- **blueprint** - 将一行目标转为多会话构建计划
- **council** - 召集四声议会处理模糊决策
- **deep-research** - 多源深度研究
- **exa-search** - 通过 Exa MCP 的神经搜索
- **plan-canvas** - 在本地浏览器画布中打开计划供标注
- **product-lens** - 构建前验证"为什么"
- **search-first** - 编码前研究工作流
- **recursive-decision-ledger** - 递归决策账本

### ECC 元数据与配置

- **configure-ecc** - ECC 交互式安装器
- **code-tour** - 创建 CodeTour 代码导览文件
- **codebase-onboarding** - 分析代码库生成结构化入门指南
- **codehealth-mcp** - 通过 CodeScene MCP 实时代码健康检查
- **config-gc** - Claude Code 配置垃圾回收
- **context-budget** - 审计上下文窗口消耗
- **ecc-guide** - 引导用户了解 ECC 功能
- **ecc-recipes** - 将工作流映射到 ECC 命令组
- **hookify-rules** - 创建 hookify 规则
- **prompt-optimizer** - 分析和优化原始 prompt
- **repo-scan** - 跨栈源代码资产审计
- **rules-distill** - 从技能中提取跨领域原则为规则
- **skill-comply** - 可视化技能/规则/代理是否被遵循
- **skill-stocktake** - 审计 Claude 技能和命令质量
- **token-budget-advisor** - 提供响应深度和 token 预算选择

### 性能与成本

- **content-hash-cache-pattern** - 使用 SHA-256 内容哈希缓存
- **cost-aware-llm-pipeline** - LLM API 成本优化模式
- **data-throughput-accelerator** - 加速大数据摄取
- **latency-critical-systems** - 延迟敏感系统模式
- **strategic-compact** - 在逻辑间隔建议手动上下文压缩

### 学习与记忆

- **ck** - Claude Code 持久化项目记忆
- **continuous-learning** - [已弃用] 使用 continuous-learning-v2
- **continuous-learning-v2** - 基于直觉的学习系统
- **unified-memory** - 跨代理共享持久化上下文

### DevOps 与 CI/CD

- **canary-watch** - 部署后监控和验证 URL
- **github-ops** - GitHub 仓库操作和管理
- **git-workflow** - Git 工作流模式
- **opensource-pipeline** - 开源管道：fork、清理、打包

### AI/ML 工程

- **ai-first-engineering** - AI 优先工程运营模型
- **mle-workflow** - 生产机器学习工程工作流

### 领域与工作流

- **gateguard** - 事实强制门控，阻止操作直到调查完成
- **santa-method** - 多 Agent 对抗式验证，带收敛循环

## 详细技能说明

### accessibility

- **用途**: 使用 WCAG 2.2 AA 级设计、实现和审计无障碍数字产品
- **使用场景**: 定义 Web/iOS/Android UI 组件规范；审计现有代码的无障碍障碍；实现新 WCAG 2.2 标准
- **依赖项**: `frontend-patterns`, `design-system`

### agent-architecture-audit

- **用途**: Agent 和 LLM 应用的全栈诊断工具。审查 12 层 Agent 架构栈的包装回归、记忆污染、工具纪律失败、隐藏修复循环和渲染损坏
- **依赖项**: `agent-introspection-debugging`, `agent-eval`, `security-review`, `autonomous-agent-harness`, `agent-harness-construction`

### agent-eval

- **用途**: 编码代理（Claude Code、Aider、Codex 等）在自定义任务上的正面对比评测

### agent-harness-construction

- **用途**: 设计和优化 AI Agent 动作空间、工具定义和观察格式

### agent-introspection-debugging

- **用途**: AI Agent 故障的结构化自调试工作流

### agent-self-evalulation

- **用途**: 完成任务后的 5 维度自我评估
- **依赖项**: `agent-eval`, `verification-loop`, `security-review`

### agent-sort

- **用途**: 通过并行仓库感知审查构建 ECC 安装计划
- **使用场景**: 项目只需 ECC 子集；需要可重复的安装决策

### agentic-engineering

- **用途**: 以 Agent 化工程师身份工作：评估优先执行、分解、成本感知模型路由

### agentic-os

- **用途**: 在 Claude Code 上构建持久化多 Agent 操作系统

### ai-first-engineering

- **用途**: AI Agent 生成大量实现输出的团队工程运营模型

### ai-regression-testing

- **用途**: AI 辅助开发的回归测试策略

### api-design

- **用途**: REST API 设计模式：资源命名、状态码、分页、过滤、错误响应、版本控制

### architecture-decision-records

- **用途**: 将 Claude Code 会话中的架构决策捕获为结构化 ADR

### autonomous-agent-harness

- **用途**: 将 Claude Code 转为完全自主 Agent 系统

### autonomous-loops

- **用途**: 自主 Claude Code 循环模式和架构
- **使用场景**: 无干预开发工作流；选择正确的循环架构；构建 CI/CD 风格管道

### backend-patterns

- **用途**: 后端架构模式、API 设计、数据库优化

### benchmark

- **用途**: 测量性能基线，检测 PR 前后回归
- **使用场景**: PR 前后性能对比；设置性能基线；用户报告"感觉慢"

### benchmark-methodology

- **用途**: 竞品评分方法论，9 维度加权评分
- **依赖项**: `competitive-platform-analysis`, `competitive-report-structure`

### benchmark-optimization-loop

- **用途**: 递归优化、基准测试延迟/吞吐量/成本

### blueprint

- **用途**: 将一行目标转为多会话、多 Agent 工程项目的构建计划
- **使用场景**: 将大功能拆分为多个 PR；跨会话的重构/迁移

### browser-qa

- **用途**: 部署后自动化视觉测试和 UI 交互验证
- **使用场景**: 部署到 staging/preview 后；PR 审查前端代码时

### bun-runtime

- **用途**: Bun 作为运行时、包管理器、打包器和测试运行器
- **使用场景**: **优先 Bun**: 新 JS/TS 项目、Vercel 部署；**优先 Node**: 最大生态兼容性

### canary-watch

- **用途**: 部署后监控和验证 URL
- **使用场景**: 部署到生产/staging 后；合并高风险 PR 后

### ck

- **用途**: Claude Code 持久化项目记忆

### claude-devfleet

- **用途**: 通过 Claude DevFleet 编排多 Agent 编码任务

### click-path-audit

- **用途**: 追踪每个用户按钮的完整状态变更序列
- **使用场景**: 系统调试无果但用户报告 UI 故障；修改 Zustand store action 后
- **不适用场景**: API 级别 Bug；样式/布局问题；性能问题

### code-tour

- **用途**: 创建 CodeTour 代码导览文件
- **使用场景**: 代码导览、架构走查、PR 导览、RCA 导览
- **不适用场景**: 一次性解释；需要散文文档；实现或重构任务
- **依赖项**: `codebase-onboarding`, `coding-standards`, `council`

### codebase-onboarding

- **用途**: 分析不熟悉的代码库并生成结构化入门指南

### codehealth-mcp

- **用途**: 通过 CodeScene MCP 实时代码健康检查
- **使用场景**: 代码质量审查；重构热点模块；AI 变更后验证
- **依赖项**: `coding-standards`, `plankton-code-quality`, `verification-loop`, `tdd-workflow`, `security-review`

### coding-standards

- **用途**: 跨项目编码规范基线

### config-gc

- **用途**: Claude Code 配置垃圾回收
- **依赖项**: `skill-stocktake`, `configure-ecc`, `continuous-learning`, `security-review`

### configure-ecc

- **用途**: ECC 交互式安装器
- **依赖项**: 需通过插件或手动复制引导

### content-hash-cache-pattern

- **用途**: 使用 SHA-256 内容哈希缓存文件处理结果
- **使用场景**: 文件处理管道、CLI 工具、批量处理
- **不适用场景**: 必须始终新鲜的数据

### context-budget

- **用途**: 审计 Claude Code 上下文窗口消耗

### continuous-agent-loop

- **用途**: 持续自主 Agent 循环模式

### continuous-learning [已弃用]

- **用途**: 遗留 v1 stop-hook 技能提取器。使用 `continuous-learning-v2` 替代

### continuous-learning-v2

- **用途**: 基于直觉的学习系统

### cost-aware-llm-pipeline

- **用途**: LLM API 成本优化模式
- **使用场景**: 调用 Claude/OpenAI 等 LLM API 的应用

### council

- **用途**: 召集四声议会处理模糊决策
- **使用场景**: 多路径无明显赢家；需要明确权衡
- **不适用场景**: 验证输出正确性 → `santa-method`；分解功能 → `planner`；架构设计 → `architect`
- **依赖项**: `santa-method`, `search-first`, `architecture-decision-records`

### data-throughput-accelerator

- **用途**: 加速大数据摄取

### database-migrations

- **用途**: 数据库迁移最佳实践

### deep-research

- **用途**: 使用 firecrawl 和 exa MCP 进行多源深度研究

### delivery-gate

- **用途**: Stop hook 阻止完成直到质量检查通过

### deployment-patterns

- **用途**: 部署工作流和 CI/CD 管道模式

### design-system

- **用途**: 生成或审计设计系统
- **使用场景**: 新项目需要设计系统；审计视觉一致性

### docker-patterns

- **用途**: Docker 和 Docker Compose 模式

### dynamic-workflow-mode

- **用途**: 设计任务本地 harness、评估门控和可复用技能提取

### e2e-testing

- **用途**: Playwright E2E 测试模式

### ecc-guide

- **用途**: 引导用户了解 ECC 功能

### ecc-recipes

- **用途**: 将工作流映射到 ECC 命令组

### error-handling

- **用途**: 跨语言错误处理模式

### eval-harness

- **用途**: 评估驱动开发 (EDD) 正式框架

### exa-search

- **用途**: 通过 Exa MCP 的神经搜索
- **依赖项**: `deep-research`, `market-research`

### frontend-design-direction

- **用途**: 设置 ECC 前端设计方向
- **使用场景**: 构建网页、应用、仪表板；需要更强的产品特定设计判断

### frontend-patterns

- **用途**: 前端开发模式

### frontend-slides

- **用途**: 创建动画丰富的 HTML 演示文稿

### gateguard

- **用途**: 事实强制门控，阻止操作直到完成具体调查
- **依赖项**: `safety-guard`, `code-reviewer`

### git-workflow

- **用途**: Git 工作流模式

### github-ops

- **用途**: GitHub 仓库操作和管理

### golang-patterns

- **用途**: Go 惯用模式和最佳实践

### golang-testing

- **用途**: Go 测试模式

### hookify-rules

- **用途**: 创建 hookify 规则

### java-coding-standards

- **用途**: Java 编码标准（Spring Boot/Quarkus）
- **使用场景**: 编写或审查 Java 代码；强制命名/不可变性约定

### jpa-patterns

- **用途**: JPA/Hibernate 实体设计和查询优化

### latency-critical-systems

- **用途**: 延迟敏感系统

### loop-design-check

- **用途**: 设计目标导向的 Agent 循环并审查失败模式

### mle-workflow

- **用途**: 生产机器学习工程工作流
- **依赖项**: `python-patterns`, `python-testing`, `eval-harness`, `database-migrations`, `deployment-patterns`

### opensource-pipeline

- **用途**: 开源管道：fork、清理、打包

### orch-add-feature

- **用途**: 端到端编排构建全新功能
- **使用场景**: 用户想要不存在的功能

### orch-build-mvp

- **用途**: 从设计文档编排构建工作 MVP
- **使用场景**: 有设计/规格文档时

### orch-change-feature

- **用途**: 编排修改现有功能行为
- **使用场景**: 功能正常但行为需要不同

### orch-fix-defect

- **用途**: 编排修复 Bug
- **使用场景**: 行为错误：错误输出、崩溃、回归

### orch-pipeline

- **用途**: orch-* 技能族的共享编排引擎
- **使用场景**: 间接加载；仅在添加新操作时直接读取

### orch-refine-code

- **用途**: 编排行为保持的重构
- **使用场景**: 相同行为，更好结构

### parallel-execution-optimizer

- **用途**: 通过并行工作加速任务

### plan-canvas

- **用途**: 在本地浏览器画布中打开计划供标注
- **使用场景**: 写完计划后需要审批；需要指向而非输入反馈

### plan-orchestrate

- **用途**: 读取计划文档，设计每步 Agent 链

### plankton-code-quality

- **用途**: 使用 Plankton 的写时代码质量强制

### postgres-patterns

- **用途**: PostgreSQL 数据库模式
- **依赖项**: `database-reviewer`, `backend-patterns`

### product-lens

- **用途**: 构建前验证"为什么"
- **使用场景**: 功能开始前验证；每周产品审查

### prompt-optimizer

- **用途**: 分析和优化原始 prompt
- **使用场景**: 用户说"优化 prompt"、"改进 prompt"

### python-patterns

- **用途**: Python 惯用风格、PEP 8、类型提示

### python-testing

- **用途**: Python 测试策略

### react-native-patterns

- **用途**: React Native 和 Expo 应用模式
- **依赖项**: `frontend-patterns`, `coding-standards`, `tdd-workflow`, `e2e-testing`, `security-review`

### react-patterns

- **用途**: React 18/19 模式
- **依赖项**: `react-performance`, `frontend-patterns`, `accessibility`, `react-reviewer`

### react-performance

- **用途**: React 和 Next.js 性能优化模式
- **依赖项**: `react-patterns`, `react-testing`, `frontend-patterns`, `accessibility`

### react-testing

- **用途**: React 组件测试
- **依赖项**: `react-patterns`, `accessibility`, `e2e-testing`, `tdd-workflow`

### recursive-decision-ledger

- **用途**: 递归决策账本

### redis-patterns

- **用途**: Redis 数据结构和缓存模式
- **依赖项**: `postgres-patterns`, `backend-patterns`, `database-migrations`, `database-reviewer`

### repo-scan

- **用途**: 跨栈源代码资产审计
- **使用场景**: 接管大型遗留代码库；重大重构前

### rules-distill

- **用途**: 从技能中提取跨领域原则为规则

### rust-patterns

- **用途**: Rust 惯用模式
- **使用场景**: 编写、审查、重构 Rust 代码

### rust-testing

- **用途**: Rust 测试模式
- **使用场景**: 编写新 Rust 函数；添加测试覆盖

### safety-guard

- **用途**: 防止生产系统上的破坏性操作

### santa-method

- **用途**: 多 Agent 对抗式验证，带收敛循环

### search-first

- **用途**: 编码前研究工作流

### security-review

- **用途**: 安全审查技能

### security-scan

- **用途**: 使用 AgentShield 扫描 .claude/ 目录安全漏洞

### skill-comply

- **用途**: 可视化技能/规则/代理是否被遵循

### skill-stocktake

- **用途**: 审计 Claude 技能和命令质量

### springboot-patterns

- **用途**: Spring Boot 架构模式

### springboot-security

- **用途**: Spring Security 最佳实践

### springboot-tdd

- **用途**: Spring Boot 测试驱动开发
- **使用场景**: 新功能、Bug 修复、重构

### springboot-verification

- **用途**: Spring Boot 验证循环

### strategic-compact

- **用途**: 在逻辑间隔建议手动上下文压缩
- **依赖项**: Memory persistence hooks, `continuous-learning`

### tdd-workflow

- **用途**: 测试驱动开发，80%+ 覆盖率

### team-agent-orchestration

- **用途**: 团队化 Agent 编排

### team-builder

- **用途**: 交互式 Agent 选择器
- **使用场景**: 有多个 Agent 人设文件时；需要组合临时团队

### token-budget-advisor

- **用途**: 提供响应深度和 token 预算选择
- **使用场景**: 用户想控制响应长度；提到 token、预算、深度

### unified-memory

- **用途**: 跨代理共享持久化上下文
- **使用场景**: 保存另一个代理需要的上下文；在代理间传递工作

### verification-loop

- **用途**: Claude Code 会话的综合验证系统
- **使用场景**: 完成功能后；创建 PR 前；重构后

### vite-patterns

- **用途**: Vite 构建工具模式
- **使用场景**: 配置 vite.config.ts；设置环境变量；优化构建输出
- **依赖项**: `frontend-patterns`, `docker-patterns`

### vue-patterns

- **用途**: Vue.js 3 Composition API 模式
- **依赖项**: `accessibility`, `frontend-patterns`, `typescript`, `coding-standards`
