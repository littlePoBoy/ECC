# 代理快速参考

ECC 插件中所有代理的自动生成摘要。

## 快速查找

| 代理 | 用途 | 使用场景 |
|------|------|----------|
| architect | 系统架构与可扩展性设计 | 规划功能、重构大型系统、架构决策 |
| build-error-resolver | 以最小差异修复 TypeScript/构建错误 | 构建失败或出现类型错误时 |
| code-architect | 基于代码库模式设计功能架构 | 为新功能创建实现蓝图 |
| code-explorer | 分析现有代码库功能并追踪执行路径 | 在新开发之前理解现有代码 |
| code-reviewer | 通用代码质量、安全性和可维护性审查 | 编写或修改代码后立即使用 |
| code-simplifier | 在保持行为不变的前提下简化代码 | 编写代码后提升清晰度和可维护性 |
| cpp-build-resolver | 修复 C++ 构建、CMake 和链接器错误 | C++ 构建失败时 |
| database-reviewer | PostgreSQL 查询优化、模式设计、安全审查 | 编写 SQL、创建迁移、设计模式时 |
| doc-updater | 生成代码地图并更新文档 | 更新代码地图、README 和指南 |
| docs-lookup | 通过 Context7 获取当前库/框架文档 | 用户询问如何使用库、框架或 API 时 |
| e2e-runner | 生成、维护和运行端到端测试 | 使用 Playwright 或 Agent Browser 测试关键用户流程 |
| go-build-resolver | 修复 Go 构建、vet 和 linter 错误 | Go 构建失败时 |
| go-reviewer | 审查 Go 代码的惯用模式和并发性 | 所有 Go 代码变更 |
| java-build-resolver | 修复 Java/Maven/Gradle 构建错误（Spring Boot 和 Quarkus） | Java 构建失败时 |
| java-reviewer | 审查 Java 代码的 Spring Boot 和 Quarkus 最佳实践 | 所有 Java 代码变更 |
| loop-operator | 安全运行自主代理循环 | 运行带监控和干预的自主循环 |
| performance-optimizer | 识别瓶颈并优化性能 | 代码缓慢、包体积过大、内存泄漏、渲染问题 |
| planner | 创建详细的实施计划 | 复杂功能、架构变更、重构 |
| pr-test-analyzer | 审查 PR 测试覆盖率的质量和完整性 | 评估 PR 的测试是否覆盖了变更行为 |
| python-reviewer | 审查 Python 代码的 PEP 8、类型提示、安全性 | 所有 Python 代码变更 |
| react-build-resolver | 修复跨打包工具的 React 构建失败 | React 构建失败时（Vite、webpack、Next.js、CRA 等） |
| react-reviewer | 审查 React 代码的 hooks、RSC、无障碍性和性能 | 任何涉及 .tsx/.jsx 文件的变更 |
| refactor-cleaner | 移除死代码、重复代码和未使用的导出 | 代码维护和清理 |
| rust-build-resolver | 修复 Rust cargo 构建和借用检查器错误 | Rust 构建失败时 |
| rust-reviewer | 审查 Rust 代码的所有权、安全性和惯用模式 | 所有 Rust 代码变更 |
| security-reviewer | 检测和修复安全漏洞 | 编写认证、输入处理、API 或敏感数据代码后 |
| spec-miner | 从现有代码库中提取行为规范 | 将遗留项目引入规范驱动开发 |
| tdd-guide | 强制执行测试驱动开发方法论 | 编写新功能、修复缺陷、重构 |
| type-design-analyzer | 评估类型设计的封装性和不变量表达 | 审查类型系统设计质量 |
| typescript-reviewer | 审查 TypeScript/JavaScript 的类型安全和异步正确性 | 所有 TypeScript/JavaScript 代码变更 |
| vue-reviewer | 审查 Vue.js 代码的响应式、组合式 API、SSR 安全性 | 任何涉及 .vue 文件或 Vue 生态代码的变更 |

## 详细代理说明

---

### 审查类代理

---

#### code-reviewer

- **用途**：专业的代码审查专家，专注于质量、安全性和可维护性
- **使用场景**：编写或修改代码后立即使用；所有代码变更必须使用
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：无
- **说明**：基于置信度过滤（仅在超过 80% 确定时报告）。包含全面的误报列表以避免噪音。涵盖安全、代码质量、React/Next.js、Node.js/后端、性能和最佳实践。裁定结果：通过 / 警告 / 阻止。

#### database-reviewer

- **用途**：PostgreSQL 专家，专注于查询优化、模式设计、安全性和性能
- **使用场景**：编写 SQL、创建迁移、设计模式、排查数据库性能问题
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：技能：`postgres-patterns`、`database-migrations`
- **说明**：整合 Supabase 最佳实践。涵盖 RLS、连接池、并发、索引策略。标记反模式如 `SELECT *`、`varchar(255)`、OFFSET 分页、未参数化查询。

#### go-reviewer

- **用途**：专业的 Go 代码审查专家，专注于惯用 Go、并发、错误处理和性能
- **使用场景**：所有 Go 代码变更；Go 项目必须使用
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：技能：`golang-patterns`
- **说明**：涵盖安全（SQL/命令注入、竞态条件）、错误处理（忽略的错误、缺少包装）、并发（goroutine 泄漏、通道死锁）和 Go 惯用模式（表驱动测试、context 作为第一个参数）。

#### java-reviewer

- **用途**：专业的 Java 代码审查专家，专注于 Spring Boot 和 Quarkus 项目
- **使用场景**：所有 Java 代码变更；Java 项目必须使用
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：技能：`springboot-patterns`、`quarkus-patterns`
- **说明**：从构建文件自动检测 Spring Boot 与 Quarkus。涵盖分层架构、JPA/Panache、MongoDB（Panache）、安全、并发、工作流/状态机。将严重安全问题上报给 `security-reviewer`。

#### python-reviewer

- **用途**：专业的 Python 代码审查专家，专注于 PEP 8、Pythonic 惯用模式、类型提示、安全性和性能
- **使用场景**：所有 Python 代码变更；Python 项目必须使用
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：技能：`python-patterns`
- **说明**：涵盖安全（SQL 注入、命令注入、eval/exec）、类型提示、Pythonic 模式（列表推导式、`isinstance`、枚举）、并发和框架特定检查（Django、FastAPI、Flask）。

#### react-reviewer

- **用途**：专业的 React/JSX 审查专家，专注于 hooks、RSC 边界、无障碍性和性能
- **使用场景**：任何涉及 .tsx/.jsx 文件或 React 组件逻辑的变更；React 项目必须使用
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：代理：`typescript-reviewer`（同时调用）、`security-reviewer`；规则：`react/coding-style.md`、`react/hooks.md`、`react/patterns.md`、`react/security.md`、`react/testing.md`；技能：`react-patterns`、`react-testing`、`accessibility`
- **说明**：与 `typescript-reviewer` 划分职责范围 -- React 负责 hooks 规则、`dangerouslySetInnerHTML`、RSC 边界、无障碍性、渲染性能、Server Action 验证。对于 `.tsx`/`.jsx` PR 应同时调用两个代理。

#### rust-reviewer

- **用途**：专业的 Rust 代码审查专家，专注于所有权、生命周期、错误处理、unsafe 使用和惯用模式
- **使用场景**：所有 Rust 代码变更；Rust 项目必须使用
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：技能：`rust-patterns`
- **说明**：涵盖安全（未检查的 `unwrap()`、无正当理由的 unsafe）、错误处理（被忽略的错误、缺少上下文）、所有权（不必要的克隆、String 与 &str）、并发（在 async 中阻塞、无界通道）和性能。

#### security-reviewer

- **用途**：安全漏洞检测和修复专家
- **使用场景**：编写处理用户输入、认证、API 端点或敏感数据的代码后
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：技能：`security-review`
- **说明**：涵盖 OWASP Top 10、硬编码密钥、输入验证、认证/授权、依赖安全。标记模式如包含用户输入的 shell 命令、字符串拼接 SQL、`innerHTML = userInput`、明文密码。针对严重发现的紧急响应协议。

#### typescript-reviewer

- **用途**：专业的 TypeScript/JavaScript 代码审查专家，专注于类型安全、异步正确性和安全性
- **使用场景**：所有 TypeScript 和 JavaScript 代码变更；TypeScript/JavaScript 项目必须使用
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：技能：`coding-standards`、`frontend-patterns`、`backend-patterns`
- **说明**：涵盖安全（eval、XSS、注入、路径遍历）、类型安全（`any` 滥用、`as` 断言）、异步正确性（未处理的 rejection、浮动 promise）、错误处理、Node.js 特定问题。对于 React 特定审查，请配合 `react-reviewer` 使用。

#### vue-reviewer

- **用途**：专业的 Vue.js 审查专家，专注于组合式 API、响应式、组件架构和 SSR 安全性
- **使用场景**：任何涉及 .vue 文件或 Vue 生态代码（Pinia、Vue Router、Nuxt）的变更；Vue 项目必须使用
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：代理：`typescript-reviewer`（同时调用）；规则：`vue/coding-style.md`、`vue/hooks.md`、`vue/patterns.md`、`vue/security.md`、`vue/testing.md`；技能：`vue-patterns`
- **说明**：与 `typescript-reviewer` 划分职责范围 -- Vue 负责响应式正确性、`v-html` 审计、组合式函数、Vue Router、Pinia、SSR 安全性、无障碍性、渲染性能。对于 `.vue` PR 应同时调用两个代理。

#### pr-test-analyzer

- **用途**：审查 PR 测试覆盖率的质量和完整性，重点关注行为覆盖
- **使用场景**：评估 PR 的测试是否真正覆盖了变更行为
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：无
- **说明**：将变更代码映射到对应测试。按影响程度评级覆盖差距（关键、重要、锦上添花）。检查有意义的断言、不稳定模式、测试隔离。

---

### 构建修复类代理

---

#### build-error-resolver

- **用途**：构建和 TypeScript 错误解决专家，以最小差异修复
- **使用场景**：构建失败或出现类型错误时
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：无
- **说明**：仅修复构建/类型错误 -- 不进行架构修改。涵盖 TypeScript 错误、构建失败、依赖问题、配置错误。成功标准：`tsc --noEmit` 退出码为 0，`npm run build` 完成。重构交给 `refactor-cleaner`，架构变更交给 `architect`。

#### cpp-build-resolver

- **用途**：C++ 构建、CMake 和编译错误解决专家
- **使用场景**：C++ 构建失败时
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：技能：`cpp-coding-standards`
- **说明**：修复编译错误、CMake 配置、链接器错误、模板实例化错误、包含/依赖问题。仅进行精确修复。3 次修复尝试失败后停止。

#### go-build-resolver

- **用途**：Go 构建、vet 和编译错误解决专家
- **使用场景**：Go 构建失败时
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：技能：`golang-patterns`
- **说明**：修复 `go build` 错误、`go vet` 警告、`staticcheck`/`golangci-lint` 问题、模块依赖问题、类型错误。更改导入后始终运行 `go mod tidy`。未经批准不得添加 `//nolint`。

#### java-build-resolver

- **用途**：Java/Maven/Gradle 构建错误解决专家，支持 Spring Boot 和 Quarkus
- **使用场景**：Java 构建失败时
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：技能：`springboot-patterns`、`quarkus-patterns`
- **说明**：从构建文件自动检测 Spring Boot 与 Quarkus。处理注解处理器错误（Lombok、MapStruct）、依赖冲突、Checkstyle/SpotBugs 违规。Spring Boot（bean 装配、循环依赖）和 Quarkus（CDI、Panache、原生镜像、响应式）分别有独立的修复模式。

#### react-build-resolver

- **用途**：诊断和修复跨 Vite、webpack、Next.js、CRA、Parcel、esbuild 和 Bun 的 React 构建失败
- **使用场景**：React 构建失败时；React 构建失败必须使用
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：代理：`react-reviewer`（构建通过后进行代码审查）；规则：`react/coding-style.md`、`react/patterns.md`；技能：`react-patterns`、`frontend-patterns`；命令：`/react-build`、`/react-review`
- **说明**：处理 JSX/TSX 编译错误、tsconfig 问题、打包工具特定配置、水合不匹配、服务端/客户端组件边界、Tailwind/PostCSS 流水线失败。自动检测构建系统。不得为了"通过构建"而禁用类型检查。

#### rust-build-resolver

- **用途**：Rust 构建、编译和依赖错误解决专家
- **使用场景**：Rust 构建失败时
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：技能：`rust-patterns`
- **说明**：修复 `cargo build`/`cargo check` 错误、借用检查器问题、生命周期错误、trait 实现不匹配、Cargo 依赖/feature 问题、`cargo clippy` 警告。不得使用 `unsafe` 绕过借用检查器错误。不得添加 `.unwrap()` 来消除类型错误。

---

### 规划与架构类代理

---

#### architect

- **用途**：软件架构专家，专注于系统设计、可扩展性和技术决策
- **使用场景**：规划新功能、重构大型系统、做出架构决策
- **工具**：Read, Grep, Glob
- **模型**：opus
- **依赖项**：无
- **说明**：涵盖模块化、可扩展性、可维护性、安全性、性能。生成架构决策记录（ADR）。包含系统设计检查清单和反模式检测（大泥球、金锤子、上帝对象等）。

#### code-architect

- **用途**：通过分析现有代码库模式和约定来设计功能架构
- **使用场景**：为新功能创建实现蓝图
- **工具**：Read, Grep, Glob, Bash
- **模型**：sonnet
- **依赖项**：无
- **说明**：在提出新抽象之前先分析现有模式。生成包含文件路径、接口、数据流和依赖顺序构建序列（类型 -> 核心逻辑 -> 集成 -> UI -> 测试 -> 文档）的实现蓝图。

#### planner

- **用途**：专业的规划专家，专注于复杂功能和重构
- **使用场景**：功能实现、架构变更、复杂重构
- **工具**：Read, Grep, Glob
- **模型**：opus
- **依赖项**：无
- **说明**：创建包含分阶段拆解、文件路径、依赖关系、风险评估和测试策略的详细实施计划。每个阶段应可独立交付。包含完整示例（Stripe 订阅）。将功能分为最小可行 -> 核心体验 -> 边界情况 -> 优化四个层级。

---

### 分析与探索类代理

---

#### code-explorer

- **用途**：通过追踪执行路径和映射架构来深入分析现有代码库功能
- **使用场景**：在新开发之前理解现有功能的工作方式
- **工具**：Read, Grep, Glob
- **模型**：sonnet
- **依赖项**：无
- **说明**：从入口点追踪执行路径，映射架构层，识别模式和约定，记录依赖关系。生成包含关键文件、依赖关系和新开发建议的结构化探索报告。

#### code-simplifier

- **用途**：简化和精炼代码，提升清晰度、一致性和可维护性，同时保持行为不变
- **使用场景**：编写代码后提升清晰度；专注于最近修改的代码
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：无
- **说明**：提取深层嵌套逻辑，用提前返回替换复杂条件，移除死代码/未使用的导入，合并重复逻辑，拆解过度抽象的一次性辅助函数。仅进行功能等价的变更。

#### spec-miner

- **用途**：从现有代码库中提取行为规范，用于 OpenSpec
- **使用场景**：将遗留项目引入规范驱动开发；"为此项目挖掘规范"
- **工具**：Read, Grep, Glob, Bash, Write
- **模型**：opus
- **依赖项**：无（完全自给自足）
- **说明**：生成扁平化的需求（WHEN->THEN）和不变量（始终为真）块。对大型模块使用采样扩展策略。输出到 `openspec/specs/<capability>/spec.md`。仅写入 `openspec/specs/` 目录。Bash 保持只读。包含结构化元数据（实体、强制执行、id、测试锚点）。为未来的 OpenSpec 变更做好增量准备。

#### type-design-analyzer

- **用途**：分析类型设计的封装性、不变量表达、实用性和强制执行
- **使用场景**：审查类型系统设计质量
- **工具**：Read, Grep, Glob
- **模型**：sonnet
- **依赖项**：无
- **说明**：评估四个维度：封装性（内部是否隐藏）、不变量表达（类型是否编码业务规则）、不变量实用性（是否防止真实缺陷）、强制执行（类型系统强制 vs 逃生通道）。生成每个类型的评分和改进建议。

---

### 开发工作流类代理

---

#### tdd-guide

- **用途**：测试驱动开发专家，强制执行先写测试的方法论
- **使用场景**：编写新功能、修复缺陷、重构代码
- **工具**：Read, Write, Edit, Bash, Grep
- **模型**：sonnet
- **依赖项**：技能：`tdd-workflow`
- **说明**：强制执行红-绿-重构循环。要求 80% 以上覆盖率。涵盖单元、集成和端到端测试类型。强制边界情况测试：null/undefined、空值、无效类型、边界值、错误路径、竞态条件、大数据、特殊字符。包含针对 pass@1 和 pass@3 稳定性的评估驱动 TDD 补充说明。

#### e2e-runner

- **用途**：端到端测试专家，优先使用 Agent Browser，Playwright 作为备选
- **使用场景**：为关键用户流程生成、维护和运行端到端测试
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：技能：`e2e-testing`
- **说明**：优先使用 Agent Browser（语义选择器、AI 优化）而非原始 Playwright。使用页面对象模型模式、`data-testid` 定位器。处理不稳定测试隔离。管理制品（截图、视频、追踪记录）。成功标准：100% 关键流程通过，整体 >95%，不稳定率 <5%。

#### refactor-cleaner

- **用途**：死代码清理和合并专家
- **使用场景**：代码维护 -- 移除未使用的代码、重复代码和未使用的导出
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：无
- **说明**：使用 `knip`、`depcheck`、`ts-prune` 进行检测。按风险分类：安全（未使用的导出/依赖）、谨慎（动态导入）、高风险（公共 API）。每次移除一个类别，每批之后运行测试。不得在活跃功能开发期间或部署前移除。

#### doc-updater

- **用途**：文档和代码地图专家
- **使用场景**：更新代码地图、README 和指南
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：haiku
- **依赖项**：无
- **说明**：从代码库结构生成代码地图（AST 分析、依赖映射）。输出到 `docs/CODEMAPS/`。每个代码地图保持在 500 行以内。始终包含更新时间戳。单一事实来源：从代码生成，不要手动编写。

#### docs-lookup

- **用途**：通过 Context7 MCP 获取当前库/框架/API 文档
- **使用场景**：用户询问如何使用库、框架或 API，或需要最新的代码示例
- **工具**：Read, Grep, mcp__context7__resolve-library-id, mcp__context7__query-docs
- **模型**：haiku
- **依赖项**：MCP：Context7（`resolve-library-id`、`query-docs`）
- **说明**：通过 Context7 解析库 ID 和查询文档，而非依赖训练数据。每次请求最多 3 次调用。如果 Context7 不可用，回退到知识库并附加免责声明。将获取的文档视为不受信任的内容（防提示注入）。

#### performance-optimizer

- **用途**：性能分析和优化专家
- **使用场景**：识别瓶颈、优化慢代码、减小包体积、提升运行时性能
- **工具**：Read, Write, Edit, Bash, Grep, Glob
- **模型**：sonnet
- **依赖项**：无
- **说明**：涵盖算法分析、React/渲染优化、包体积优化、数据库查询优化、网络/API 优化、内存泄漏检测。目标：FCP <1.8s、LCP <2.5s、TTI <3.8s、CLS <0.1、TBT <200ms、gzip 后包体积 <200KB。生成性能审计报告。

#### loop-operator

- **用途**：运行自主代理循环，监控进度，并在循环停滞时安全干预
- **使用场景**：运行带监控和干预的自主循环
- **工具**：Read, Grep, Glob, Bash, Edit
- **模型**：sonnet
- **依赖项**：无
- **说明**：追踪进度检查点，检测停滞和重试风暴。在重复失败时暂停并缩小范围。在以下情况上报：跨两个检查点无进展、重复相同失败、成本偏离预算、合并冲突阻碍推进。要求质量门、评估基线、回退路径和分支/工作树隔离。
