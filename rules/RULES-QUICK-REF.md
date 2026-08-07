# 规则快速参考

ECC 插件中所有规则的自动生成摘要。

## 结构

规则按 **通用** 层加 **语言特定** 目录组织。通用规则始终适用；语言特定规则扩展或覆盖通用规则。当语言特定规则与通用规则冲突时，语言特定规则优先。

```
rules/
├── common/          # 语言无关的原则（始终安装）
├── golang/          # Go 特定
├── java/            # Java 特定
├── python/          # Python 特定
├── react/           # React 特定（扩展 typescript + common）
├── rust/            # Rust 特定
├── typescript/      # TypeScript/JavaScript 特定
├── vue/             # Vue 3 特定
└── web/             # Web 和前端特定
```

## 快速查找

### 通用规则（始终适用）

| 规则 | 用途 | 要点 |
|------|------|------|
| agents.md | Agent 编排与委派 | 11 个 agent（planner、code-reviewer、tdd-guide 等）；独立任务并行执行；委派完成契约 |
| code-review.md | 代码审查标准与流程 | 强制触发条件；严重性级别（CRITICAL/HIGH/MEDIUM/LOW）；80% 覆盖率门槛；敏感代码使用 security-reviewer |
| coding-style.md | 通用编码规范 | 不可变性（关键）；KISS/DRY/YAGNI；文件 <800 行，函数 <50 行；camelCase 命名；禁止直接修改 |
| development-workflow.md | 功能实现流水线 | 先调研；规划（planner agent）；TDD（RED-GREEN-REFACTOR）；代码审查；使用 conventional 格式提交 |
| git-workflow.md | Git 提交与 PR 标准 | Conventional 提交类型（feat、fix、refactor、docs、test、chore、perf、ci）；PR 流程需包含完整摘要 |
| hooks.md | Hook 系统概述 | PreToolUse、PostToolUse、Stop hook 类型；自动接受权限；TodoWrite 最佳实践 |
| patterns.md | 通用设计模式 | 骨架项目；Repository 模式；一致的 API 响应封装 |
| performance.md | 模型选择与上下文管理 | Haiku/Sonnet/Opus 选择策略；上下文窗口管理；扩展思维 + 计划模式；构建故障排查 |
| security.md | 安全检查清单与协议 | 禁止硬编码密钥；SQL 注入/XSS/CSRF 防护；security-reviewer agent；轮换已泄露的密钥 |
| testing.md | 测试要求 | 最低 80% 覆盖率；单元测试 + 集成测试 + E2E 测试缺一不可；TDD 强制执行（RED-GREEN-REFACTOR）；AAA 测试结构 |

### 语言特定规则

| 语言 | 规则 | 用途 | 扩展 |
|------|------|------|------|
| golang | coding-style.md | Go 格式化、接口、错误处理 | common/coding-style.md |
| golang | hooks.md | Go hooks：gofmt、go vet、staticcheck | common/hooks.md |
| golang | patterns.md | 函数选项、小接口、依赖注入 | common/patterns.md |
| golang | security.md | Go 密钥管理、gosec 扫描、context 超时 | common/security.md |
| golang | testing.md | go test、表驱动测试、-race 标志 | common/testing.md |
| java | coding-style.md | Java 格式化、不可变性、现代特性、流 | common/coding-style.md |
| java | hooks.md | google-java-format、checkstyle、编译检查 | common/hooks.md |
| java | patterns.md | Repository、服务层、构造函数注入、DTO、密封类型 | common/patterns.md |
| java | security.md | SQL 注入、输入验证、认证、依赖安全 | common/security.md |
| java | testing.md | JUnit 5、AssertJ、Mockito、Testcontainers、JaCoCo | common/testing.md |
| python | coding-style.md | PEP 8、类型注解、black/isort/ruff、frozen dataclasses | common/coding-style.md |
| python | fastapi.md | FastAPI 特定：异步、DI、schema、安全、测试 | （独立） |
| python | hooks.md | black/ruff 格式化、mypy/pyright 类型检查 | common/hooks.md |
| python | patterns.md | Protocol（鸭子类型）、dataclasses 作为 DTO、上下文管理器 | common/patterns.md |
| python | security.md | dotenv 密钥管理、bandit 扫描 | common/security.md |
| python | testing.md | pytest 框架、覆盖率、基于 mark 的分类 | common/testing.md |
| react | coding-style.md | JSX、文件扩展名、命名、服务端/客户端边界、hooks 纪律 | typescript/coding-style.md + common/coding-style.md |
| react | hooks.md | Hooks 规则、useEffect 指导、依赖数组、自定义 hooks | typescript/patterns.md + common/patterns.md |
| react | patterns.md | 容器/展示分离、状态定位、RSC、Suspense、表单、数据获取 | typescript/patterns.md + common/patterns.md |
| react | security.md | dangerouslySetInnerHTML、不安全 URL、服务端 Actions、CSP、原型污染 | typescript/security.md + common/security.md |
| react | testing.md | RTL、Vitest/Jest、MSW、查询优先级、userEvent、无障碍断言 | typescript/testing.md + common/testing.md |
| rust | coding-style.md | rustfmt/clippy、不可变性、所有权/借用、错误处理、迭代器 | common/coding-style.md |
| rust | hooks.md | cargo fmt、cargo clippy、cargo check | common/hooks.md |
| rust | patterns.md | 基于 traits 的 Repository、newtype、枚举状态机、密封 traits、builder | common/patterns.md |
| rust | security.md | 密钥管理、参数化查询、unsafe 代码规则、cargo audit/deny | common/security.md |
| rust | testing.md | #[test]、rstest、proptest、mockall、cargo-llvm-cov | common/testing.md |
| typescript | coding-style.md | 类型/接口、禁止 `any`、使用 spread 实现不可变、Zod 验证 | common/coding-style.md |
| typescript | hooks.md | Prettier 格式化、tsc 类型检查、console.log 审查 | common/hooks.md |
| typescript | patterns.md | API 响应格式、自定义 hooks、Repository 接口 | common/patterns.md |
| typescript | security.md | 环境变量密钥管理、security-reviewer agent | common/security.md |
| typescript | testing.md | Playwright 用于 E2E、e2e-runner agent | common/testing.md |
| vue | coding-style.md | SFC 结构、Composition API、响应式纪律、宏/模板 | common/coding-style.md |
| vue | hooks.md | vue-tsc 类型检查、ESLint + Prettier、架构边界 | common/hooks.md |
| vue | patterns.md | Composables、props/emits/v-model、provide/inject、Pinia、vue-router、vue-query | common/patterns.md |
| vue | security.md | v-html XSS、URL/样式注入、客户端 bundle 密钥 | common/security.md |
| vue | testing.md | Vitest + @vue/test-utils、Pinia 测试、mount 配置 | common/testing.md |
| web | coding-style.md | CSS 自定义属性、动画属性、语义化 HTML、文件组织 | common/coding-style.md |
| web | design-quality.md | 反模板策略、设计质量要求、风格方向 | common/patterns.md |
| web | hooks.md | Prettier、ESLint、tsc（增量 + 超时）、Stylelint、文件大小守卫 | common/hooks.md |
| web | patterns.md | 复合组件、状态管理分层、URL 作为状态、数据获取 | common/patterns.md |
| web | performance.md | Core Web Vitals 目标、bundle 预算、图片/字体/动画优化 | common/performance.md |
| web | security.md | 基于 nonce 的 CSP、XSS 防护、HTTPS 响应头、表单安全 | common/security.md |
| web | testing.md | 视觉回归、无障碍、跨浏览器、响应式断点 | common/testing.md |

## 详细规则说明

### common/agents.md

- **用途**：定义如何编排和委派工作给专业子 agent。
- **核心规则**：
  - 11 个可用 agent：planner、architect、tdd-guide、code-reviewer、security-reviewer、build-error-resolver、e2e-runner、refactor-cleaner、doc-updater、rust-reviewer、harmonyos-app-resolver
  - 复杂功能使用 planner，编写代码后使用 code-reviewer，新功能/缺陷使用 tdd-guide
  - 独立操作始终使用并行任务执行
  - 委派完成契约：最终消息即为交付物；委派后需负责收集结果
  - 复杂问题使用多视角分析与分角色子 agent
- **适用范围**：所有项目

### common/code-review.md

- **用途**：合并前的代码审查标准与流程。
- **核心规则**：
  - 强制审查触发条件：代码变更后、提交到共享分支前、安全敏感代码、架构变更、PR 前
  - 审查清单：代码可读、函数 <50 行、文件 <800 行、无深层嵌套、显式错误处理、无硬编码密钥、测试存在、80% 覆盖率
  - 严重性级别：CRITICAL（阻止）、HIGH（警告）、MEDIUM（提示）、LOW（备注）
  - 认证、用户输入、数据库查询、加密、支付相关代码使用 security-reviewer agent
  - 审查流程：git diff、安全检查、质量检查、运行测试、验证覆盖率、agent 审查
- **适用范围**：所有项目

### common/coding-style.md

- **用途**：跨所有语言的通用编码规范。
- **核心规则**：
  - 不可变性为关键原则：始终创建新对象，禁止直接修改已有对象
  - KISS、DRY、YAGNI 原则
  - 文件组织：多个小文件优于少数大文件；典型 200-400 行，上限 800 行
  - 全面处理错误；禁止静默吞没错误
  - 在系统边界使用基于 schema 的验证检查所有输入
  - 命名：变量/函数使用 camelCase，类型/组件使用 PascalCase，常量使用 UPPER_SNAKE_CASE
  - 代码异味：避免深层嵌套、魔法数字、过长函数
- **适用范围**：所有项目

### common/development-workflow.md

- **用途**：Git 操作前的完整功能开发流水线。
- **核心规则**：
  - 第 0 步（调研）：优先使用 GitHub 代码搜索，其次查阅库文档，检查包注册中心，优先选择经过验证的方案
  - 第 1 步（规划）：使用 planner agent；生成 PRD、架构、任务列表
  - 第 2 步（TDD）：RED-GREEN-REFACTOR；验证 80%+ 覆盖率
  - 第 3 步（代码审查）：使用 code-reviewer agent；处理 CRITICAL 和 HIGH 级别问题
  - 第 4 步（提交）：Conventional 提交格式
  - 第 5 步（预审查）：CI 通过、无合并冲突、分支与目标同步
- **适用范围**：所有项目

### common/git-workflow.md

- **用途**：Git 提交消息格式与 PR 流程。
- **核心规则**：
  - 提交格式：`<type>: <description>`，类型包括：feat、fix、refactor、docs、test、chore、perf、ci
  - PR 流程：分析完整提交历史、使用 git diff 查看所有变更、撰写完整摘要、包含测试计划
  - 新分支推送时使用 `-u` 标志
- **适用范围**：所有项目

### common/hooks.md

- **用途**：Claude Code hook 系统概述。
- **核心规则**：
  - 三种 hook 类型：PreToolUse（验证）、PostToolUse（自动格式化/检查）、Stop（最终验证）
  - 自动接受权限：仅对受信任的计划启用；禁止使用 dangerously-skip-permissions
  - TodoWrite：追踪进度、验证理解、支持实时引导
- **适用范围**：所有项目

### common/patterns.md

- **用途**：跨所有语言的通用设计模式。
- **核心规则**：
  - 实现新功能前先搜索经过验证的骨架项目
  - Repository 模式：标准 CRUD 接口，具体存储实现
  - API 响应格式：一致的封装包含 success/status、data、error、metadata
- **适用范围**：所有项目

### common/performance.md

- **用途**：模型选择策略与上下文窗口管理。
- **核心规则**：
  - Haiku：轻量级 agent、结对编程、工作 agent（节省 3 倍成本）
  - Sonnet：主要开发、编排工作流、复杂编码
  - Opus：架构决策、深度推理、研究
  - 复杂任务避免使用上下文窗口的最后 20%
  - 扩展思维默认启用（31,999 个 token）；使用 Option+T / Alt+T 切换
  - 构建故障排查：使用 build-error-resolver agent，逐步修复
- **适用范围**：所有项目

### common/security.md

- **用途**：所有提交的强制安全检查清单。
- **核心规则**：
  - 任何提交前：无硬编码密钥、所有输入已验证、SQL 注入/XSS/CSRF 防护、认证已验证、限流、安全的错误消息
  - 绝不硬编码密钥；使用环境变量或密钥管理器
  - 安全响应：立即停止、使用 security-reviewer agent、优先修复 CRITICAL 问题、轮换已泄露密钥
- **适用范围**：所有项目

### common/testing.md

- **用途**：测试要求与 TDD 工作流。
- **核心规则**：
  - 最低 80% 测试覆盖率
  - 三种测试类型全部必需：单元测试、集成测试、E2E 测试
  - TDD 强制执行：先写测试（RED）、实现（GREEN）、重构（IMPROVE）
  - AAA 模式：Arrange-Act-Assert
  - 测试名称应描述被测行为
  - 新功能主动使用 tdd-guide agent
- **适用范围**：所有项目

---

### golang/coding-style.md

- **用途**：Go 特定编码规范。
- **核心规则**：
  - gofmt 和 goimports 强制执行
  - 接受接口，返回结构体
  - 保持接口精简（1-3 个方法）
  - 始终使用 `fmt.Errorf("...: %w", err)` 包装错误并附加上下文
- **扩展**：common/coding-style.md

### golang/hooks.md

- **用途**：Go 特定的 PostToolUse hooks。
- **核心规则**：
  - gofmt/goimports 用于自动格式化
  - go vet 用于静态分析
  - staticcheck 用于扩展静态检查
- **扩展**：common/hooks.md

### golang/patterns.md

- **用途**：Go 特定设计模式。
- **核心规则**：
  - 函数选项模式用于可配置构造函数
  - 小接口定义在使用处
  - 基于构造函数的依赖注入
- **扩展**：common/patterns.md

### golang/security.md

- **用途**：Go 特定安全指南。
- **核心规则**：
  - 使用环境变量管理密钥，缺失时快速失败
  - gosec 用于静态安全分析
  - 始终使用 context.Context 进行超时控制
- **扩展**：common/security.md

### golang/testing.md

- **用途**：Go 特定测试规范。
- **核心规则**：
  - 标准 `go test` 配合表驱动测试
  - 始终使用 `-race` 标志运行
  - `go test -cover` 用于覆盖率检查
- **扩展**：common/testing.md

---

### java/coding-style.md

- **用途**：Java 特定编码规范，包含现代特性。
- **核心规则**：
  - google-java-format 或 Checkstyle 强制执行
  - 优先使用 `record` 作为值类型（Java 16+）；字段默认标记为 `final`
  - 公共 API 返回防御性副本（List.copyOf、Map.copyOf）
  - 使用现代特性：records、密封类、模式匹配、文本块、switch 表达式
  - Optional：仅从查找方法返回，禁止作为字段/参数使用
  - 流：保持管道简短（最多 3-4 个操作），避免副作用
- **扩展**：common/coding-style.md

### java/hooks.md

- **用途**：Java 特定的 PostToolUse hooks。
- **核心规则**：
  - google-java-format 用于自动格式化
  - checkstyle 用于风格检查
  - mvnw compile 或 gradlew compileJava 用于编译验证
- **扩展**：common/hooks.md

### java/patterns.md

- **用途**：Java 特定设计模式。
- **核心规则**：
  - 接口形式的 Repository 模式
  - 服务层：业务逻辑在服务中，控制器/仓库保持精简
  - 仅使用构造函数注入，禁止字段注入
  - Records 作为 DTO，配合静态工厂方法
  - Builder 模式用于具有大量可选参数的对象
  - 密封类型用于领域模型，配合穷举 switch 处理
  - 一致的 API 响应封装
- **扩展**：common/patterns.md

### java/security.md

- **用途**：Java 特定安全指南。
- **核心规则**：
  - 使用环境变量或密钥管理器管理凭据
  - 所有 SQL 使用 PreparedStatement；禁止拼接用户输入
  - DTO 上使用 Bean Validation（@NotNull、@NotBlank、@Size）
  - 密码使用 bcrypt/Argon2，禁止 MD5/SHA1
  - OWASP Dependency-Check 或 Snyk 进行 CVE 扫描
  - 禁止在 API 响应中暴露堆栈跟踪
- **扩展**：common/security.md

### java/testing.md

- **用途**：Java 特定测试规范。
- **核心规则**：
  - JUnit 5 配合 @Test、@ParameterizedTest、@Nested、@DisplayName
  - AssertJ 用于流式断言
  - Mockito 用于模拟
  - Testcontainers 用于集成测试，连接真实数据库
  - src/test/java 镜像 src/main/java 的包结构
  - JaCoCo 用于覆盖率报告；目标行覆盖率 80%+
- **扩展**：common/testing.md

---

### python/coding-style.md

- **用途**：Python 特定编码规范。
- **核心规则**：
  - 遵循 PEP 8；所有函数签名使用类型注解
  - 优先使用不可变数据结构：frozen dataclasses、NamedTuple
  - black 用于格式化，isort 用于导入排序，ruff 用于 lint
- **扩展**：common/coding-style.md

### python/fastapi.md

- **用途**：FastAPI 特定开发规则。
- **核心规则**：
  - 使用 `create_app()` 构建应用；精简路由；分离 request/update/response schemas
  - I/O 端点使用 `async def`；禁止从异步路由调用同步阻塞操作
  - 通过 `Depends` 进行依赖注入；路由处理器内禁止使用 SessionLocal()
  - 响应模型中禁止包含密码/token；使用 `response_model`
  - CORS：使用环境特定的源，禁止带凭据时使用通配符
  - 测试：覆盖确切的依赖项；测试后清除覆盖
- **适用范围**：FastAPI 项目（独立，扩展 Python 规则）

### python/hooks.md

- **用途**：Python 特定的 PostToolUse hooks。
- **核心规则**：
  - black/ruff 用于自动格式化
  - mypy/pyright 用于类型检查
  - 警告 print() 语句（应使用 logging 模块）
- **扩展**：common/hooks.md

### python/patterns.md

- **用途**：Python 特定设计模式。
- **核心规则**：
  - Protocol 用于鸭子类型（结构化子类型）
  - Dataclasses 作为 DTO
  - 上下文管理器用于资源管理
  - 生成器用于惰性求值
- **扩展**：common/patterns.md

### python/security.md

- **用途**：Python 特定安全指南。
- **核心规则**：
  - dotenv 用于密钥管理；os.environ 缺失时抛出 KeyError
  - bandit 用于静态安全分析
- **扩展**：common/security.md

### python/testing.md

- **用途**：Python 特定测试规范。
- **核心规则**：
  - pytest 作为测试框架
  - `pytest --cov=src --cov-report=term-missing` 用于覆盖率
  - 使用 `pytest.mark` 进行测试分类（unit、integration）
- **扩展**：common/testing.md

---

### react/coding-style.md

- **用途**：React 特定编码规范。
- **核心规则**：
  - 含 JSX 的文件使用 .tsx；纯逻辑文件使用 .ts
  - 组件使用 PascalCase；hooks 使用 useCamelCase
  - 优先使用 `type Props = {}` 定义封闭的 props 类型；始终解构 props
  - 自闭合标签；使用 fragments 而非 wrapper divs
  - 默认使用服务端组件；仅在需要 state/effects/refs/浏览器 API 时使用 `"use client"`
  - React 导入在前，第三方其次，项目导入最后
  - 优先使用本地状态；Context 用于低频跨组件状态；外部存储用于持久/共享状态
  - 新代码禁止使用类组件
- **扩展**：typescript/coding-style.md + common/coding-style.md

### react/hooks.md

- **用途**：React hooks 规则与最佳实践。
- **核心规则**：
  - Hooks 仅在函数组件或自定义 hook 的顶层使用；禁止在循环/条件中使用
  - useEffect 仅用于外部系统同步；禁止用于派生状态、数据转换或父组件通知
  - 依赖数组始终包含所有响应式值；禁止忽略 exhaustive-deps
  - 每个订阅/定时器/监听器必须有清理逻辑
  - 默认不使用 memoize；仅在引用相等性重要或计算昂贵时添加 useMemo/useCallback
  - 相同逻辑序列出现在 2 个以上组件中时提取为自定义 hook
  - useState：依赖前值时使用函数式更新器；3 个以上相关值使用 useReducer
  - useRef：DOM ref 和可变容器；渲染期间禁止读写 ref.current
  - React 19：use()、useFormStatus()、useOptimistic()、useTransition()
- **扩展**：typescript/patterns.md + common/patterns.md

### react/patterns.md

- **用途**：React 特定设计模式。
- **核心规则**：
  - 容器/展示分离：容器负责数据，展示组件保持纯函数
  - 状态定位决策树：useState > 提升到父组件 > Context（低频）> 外部存储 > 服务端状态库
  - 默认使用服务端组件；客户端组件通过 "use client" 选择加入
  - 每个 Suspense 边界上方需要一个 Error Boundary
  - 表单：优先使用非受控配合 form actions（React 19）；需要实时验证时使用受控
  - 数据获取：RSC fetch > TanStack Query > SWR > 禁止在 useEffect 中 fetch
  - key：稳定、在兄弟节点中唯一、可重排列表禁止使用索引
  - 组合优于继承；相关控件使用复合组件
  - React 19：ref 作为常规 prop，无需 forwardRef
- **扩展**：typescript/patterns.md + common/patterns.md

### react/security.md

- **用途**：React 特定安全指南。
- **核心规则**：
  - 关键：dangerouslySetInnerHTML 是代码审查停止信号；不可避免时使用 DOMPurify 净化
  - 验证 URL 协议；阻止 javascript: 和 data: URL
  - target="_blank" 链接始终添加 rel="noopener noreferrer"
  - Server Actions 是公共 API 端点；使用 Zod 验证每个输入；在 action 内部进行认证
  - 带公共前缀的环境变量（NEXT_PUBLIC_、VITE_、REACT_APP_）会被打包到客户端；视为公开
  - 禁止将 session 存储在 localStorage；使用 httpOnly cookies
  - CSP：基于 nonce 的脚本，script-src 中避免 unsafe-inline/unsafe-eval
  - 防范通过不受信任 JSON 的对象展开导致的原型污染
  - 生产构建：禁止公开 source maps
- **扩展**：typescript/security.md + common/security.md

### react/testing.md

- **用途**：React 特定测试规范。
- **核心规则**：
  - React Testing Library（RTL）用于组件测试；Vitest 或 Jest 作为运行器
  - 测试用户所见所行，而非实现细节
  - 查询优先级：getByRole > getByLabelText > getByText > getByTestId（最后手段）
  - 优先使用 userEvent 而非 fireEvent；始终 await userEvent 调用
  - MSW 在网络层进行网络模拟
  - 组件避免快照测试；使用视觉回归工具
  - 在 renderWithProviders helper 中统一包装 providers
  - 自定义 hooks：使用 renderHook 测试，状态变更包装在 act 中
  - 无障碍：在组件测试中运行 axe 断言
  - 覆盖率：工具函数 >=90%、hooks >=85%、组件 >=80%、容器 >=70%
- **扩展**：typescript/testing.md + common/testing.md

---

### rust/coding-style.md

- **用途**：Rust 特定编码规范。
- **核心规则**：
  - rustfmt 强制执行；clippy 使用 `-D warnings`（将警告视为错误）
  - 默认不可变；仅在需要时使用 `let mut`；可选分配优先使用 Cow<T>
  - 默认借用（&T）；仅在存储/消费时获取所有权；优先接受 &str 而非 String
  - 错误处理：Result<T, E> 配合 ?；库使用 thiserror，应用使用 anyhow；生产代码禁止 unwrap()
  - 转换优先使用迭代器链；复杂控制流使用循环
  - 按领域组织模块，而非按类型
  - 可见性：默认私有；内部共享使用 pub(crate)；公共 API 使用 pub
- **扩展**：common/coding-style.md

### rust/hooks.md

- **用途**：Rust 特定的 PostToolUse hooks。
- **核心规则**：
  - cargo fmt 用于自动格式化
  - cargo clippy 用于 lint 检查
  - cargo check 用于编译验证（比 cargo build 更快）
- **扩展**：common/hooks.md

### rust/patterns.md

- **用途**：Rust 特定设计模式。
- **核心规则**：
  - 基于 traits 的 Repository 模式（Send + Sync 约束）
  - 服务层通过构造函数进行依赖注入（Box<dyn Trait>）
  - Newtype 模式用于类型安全（防止参数混淆）
  - 枚举状态机：使非法状态不可表示；始终穷举匹配
  - Builder 模式用于具有大量可选参数的结构体
  - 密封 traits 用于扩展性控制
  - 泛型 ApiResponse 枚举用于一致的 API 响应
- **扩展**：common/patterns.md

### rust/security.md

- **用途**：Rust 特定安全指南。
- **核心规则**：
  - 使用环境变量管理密钥，启动时快速失败
  - 使用 sqlx/diesel/sea-orm 进行参数化查询；禁止将用户输入格式化到 SQL 中
  - 解析而非验证：在边界处转换为类型化结构体（newtype 模式）
  - unsafe 代码：最小化代码块；每个 unsafe 需要 // SAFETY: 注释；审查时审计所有 unsafe
  - cargo audit 用于 CVE 扫描；cargo deny 用于许可证/安全公告合规
  - 禁止在 API 响应中暴露内部路径/堆栈跟踪；使用 tracing 进行结构化日志
- **扩展**：common/security.md

### rust/testing.md

- **用途**：Rust 特定测试规范。
- **核心规则**：
  - #[test] 配合 #[cfg(test)] 模块用于单元测试
  - rstest 用于参数化测试；proptest 用于属性测试
  - mockall 用于基于 traits 的模拟；#[tokio::test] 用于异步测试
  - 单元测试在同一文件中；集成测试在 tests/ 目录中
  - cargo-llvm-cov 用于覆盖率；目标行覆盖率 80%+
  - 测试命令：cargo test、--lib、--test <name>、--doc
- **扩展**：common/testing.md

---

### typescript/coding-style.md

- **用途**：TypeScript/JavaScript 特定编码规范。
- **核心规则**：
  - 导出函数和公共 API 使用显式类型；局部变量让 TS 推断
  - interface 用于可扩展的对象形状；type 用于联合/交叉/元组
  - 禁止使用 `any`；使用 `unknown` 并安全缩窄；调用方相关类型使用泛型
  - React Props：命名的 interface/type、显式回调类型、禁止使用 React.FC
  - 通过 spread 操作符实现不可变性；参数使用 Readonly<T>
  - 错误处理：async/await 配合 try-catch；使用 instanceof 缩窄 unknown 错误
  - Zod 用于基于 schema 的验证，支持类型推断
  - 生产代码禁止 console.log；使用日志库
- **扩展**：common/coding-style.md

### typescript/hooks.md

- **用途**：TypeScript/JavaScript 特定 hooks。
- **核心规则**：
  - Prettier 用于自动格式化
  - tsc 用于编辑后的类型检查
  - 编辑文件中的 console.log 警告
  - Stop hook：审计所有修改文件中的 console.log
- **扩展**：common/hooks.md

### typescript/patterns.md

- **用途**：TypeScript/JavaScript 特定模式。
- **核心规则**：
  - 泛型 ApiResponse<T> 接口，包含 success、data、error、meta
  - 自定义 hooks 模式（如 useDebounce）
  - 泛型 Repository<T> 接口，包含 CRUD 操作
- **扩展**：common/patterns.md

### typescript/security.md

- **用途**：TypeScript/JavaScript 特定安全指南。
- **核心规则**：
  - 绝不硬编码密钥；使用 process.env 并进行验证
  - 使用 security-reviewer agent 进行全面审计
- **扩展**：common/security.md

### typescript/testing.md

- **用途**：TypeScript/JavaScript 特定测试规范。
- **核心规则**：
  - Playwright 用于关键用户流程的 E2E 测试
  - 使用 e2e-runner agent 进行 Playwright 测试
- **扩展**：common/testing.md

---

### vue/coding-style.md

- **用途**：Vue 3 特定编码规范。
- **核心规则**：
  - 始终使用 `<script setup lang="ts">` 和 Composition API；新代码禁止 Options API
  - 块顺序：script setup、template、style scoped；每个文件一个组件
  - ref 是主要的状态 API；仅在需要组合对象状态时使用 reactive
  - 解构 reactive/Pinia store 时必须使用 toRefs/storeToRefs
  - computed getter 必须是纯函数（无副作用、无异步、无 DOM）
  - 在 setup 中同步注册生命周期钩子；在 onUnmounted 中清理
  - 每个 v-for 使用 :key；禁止在同一元素上同时使用 v-if 和 v-for
- **扩展**：common/coding-style.md

### vue/hooks.md

- **用途**：Vue 特定的 PostToolUse hooks。
- **核心规则**：
  - vue-tsc --noEmit 用于 SFC + TypeScript 检查（而非普通 tsc）
  - eslint --fix 配合 eslint-plugin-vue（vue/vue3-recommended）
  - prettier --write 用于格式化；优先通过 ESLint 使用 Prettier
  - 可选：Feature-Sliced Design 边界强制执行
  - 顺序：先按文件执行 lint + 格式化，再执行项目范围的类型检查
- **扩展**：common/hooks.md

### vue/patterns.md

- **用途**：Vue 特定设计模式。
- **核心规则**：
  - Composables（useXxx）：接受 MaybeRefOrGetter<T>，返回 toRefs(reactive(...))
  - 基于类型的 defineProps/defineEmits；defineModel 用于双向绑定
  - provide/inject 使用 Symbol InjectionKey<T>；暴露只读 + 更新函数
  - Pinia：setup stores 使用 ref/computed/function；storeToRefs 用于 state/getters
  - vue-router：路由组件懒加载；beforeEach 认证门控；监听特定参数
  - vue-query：管理服务端缓存状态；query key 中使用 ref/computed（禁止 .value）
- **扩展**：common/patterns.md

### vue/security.md

- **用途**：Vue 特定安全指南。
- **核心规则**：
  - 模板仅来自受信任来源；禁止运行时从用户输入编译模板
  - v-html 是直接的 XSS 攻击向量；使用 DOMPurify 净化或避免使用
  - :href/:src 不会被转义；验证 URL 协议（仅允许 http/https/mailto）
  - :style 配合用户输入不安全（CSS 数据窃取）；使用对象语法配合属性白名单
  - import.meta.env.VITE_* 会被打包到浏览器；API 密钥保持在服务端
  - httpOnly cookies 用于 session token；禁止将凭据打包到客户端
- **扩展**：common/security.md

### vue/testing.md

- **用途**：Vue 特定测试规范。
- **核心规则**：
  - Vitest + @vue/test-utils；happy-dom 或 jsdom 环境
  - mount 用于完整渲染；shallowMount 用于存根子组件
  - 仅测试公共接口：props、events、slots、渲染输出
  - Composables：纯响应式直接测试；涉及生命周期/inject 时通过宿主组件测试
  - Pinia：组件中使用 createTestingPinia()；隔离测试时使用 setActivePinia(createPinia())
  - Mount 配置：global.plugins、global.stubs、global.mocks、global.provide
- **扩展**：common/testing.md

---

### web/coding-style.md

- **用途**：Web/前端特定编码规范。
- **核心规则**：
  - 按功能/表面区域组织，而非按文件类型
  - CSS 自定义属性用于设计 tokens（oklch 颜色、clamp 排版、间距）
  - 动画：仅使用合成器友好的属性（transform、opacity、clip-path、filter）
  - 语义化 HTML 优先；存在语义元素时禁止使用通用 wrapper div
  - 命名：组件使用 PascalCase、hooks 使用 use 前缀、CSS 类使用 kebab-case
- **扩展**：common/coding-style.md

### web/design-quality.md

- **用途**：防止模板化 UI 的设计质量标准。
- **核心规则**：
  - 反模板策略：禁止默认卡片网格、套路化 hero 区域、未修改的库默认样式
  - 每个表面至少需要 10 项要求中的 4 项（层次感、节奏感、深度、排版、语义化颜色、设计化状态、编辑式构图、纹理、有目的的动效、数据可视化融入设计）
  - 编码前选定具体的风格方向；有意识地定义调色板和排版
  - 值得采用的方向：编辑式、新粗野主义、玻璃态、深色/浅色奢华、bento、滚动叙事、3D、瑞士风格、复古未来主义
  - 组件清单：避免模板感、有意识的状态设计、层次感、可信度、双主题均有设计感
- **扩展**：common/patterns.md

### web/hooks.md

- **用途**：Web/前端特定 hook 推荐。
- **核心规则**：
  - 格式化：编辑文件时运行 pnpm prettier --write
  - Lint：编辑文件时运行 pnpm eslint --fix
  - 类型检查：pnpm tsc --noEmit --incremental 配合超时包装
  - CSS lint：编辑样式表时运行 pnpm stylelint --fix
  - PreToolUse：阻止超过 800 行的写入
  - Stop hook：pnpm build 用于生产构建验证
  - 顺序：格式化、lint、类型检查、构建验证
- **扩展**：common/hooks.md

### web/patterns.md

- **用途**：Web/前端特定设计模式。
- **核心规则**：
  - 复合组件用于共享状态的相关 UI（父组件管理状态，子组件通过 context 获取）
  - 渲染属性 / 插槽用于共享行为但标记不同的场景
  - 容器/展示分离
  - 状态管理分层：服务端状态（TanStack Query/SWR）、客户端状态（Zustand/Jotai）、URL 状态（搜索参数）、表单状态（React Hook Form）
  - URL 作为状态：持久化过滤器、排序、分页、活动标签、搜索查询
  - 数据获取：stale-while-revalidate、乐观更新、并行加载
- **扩展**：common/patterns.md

### web/performance.md

- **用途**：Web 特定的性能目标与优化。
- **核心规则**：
  - Core Web Vitals：LCP <2.5s、INP <200ms、CLS <0.1、FCP <1.5s、TBT <200ms
  - Bundle 预算：落地页 <150kb JS/<30kb CSS、应用页 <300kb/<50kb、微站 <80kb/<15kb
  - 加载策略：内联关键 CSS、预加载 hero 图片/字体、延迟非关键资源、动态导入重量级库
  - 图片：明确尺寸、仅 hero 使用 eager、折叠下方使用 lazy、优先 AVIF/WebP
  - 字体：最多两个字体族、font-display: swap、子集化、仅预加载关键字重
  - 动画：合成器友好的属性、will-change 谨慎使用、简单过渡使用 CSS
- **扩展**：common/performance.md

### web/security.md

- **用途**：Web 特定安全指南。
- **核心规则**：
  - 始终配置生产 CSP；脚本使用逐请求 nonce
  - 禁止注入未净化的 HTML；避免 innerHTML/dangerouslySetInnerHTML
  - 第三方脚本：异步加载、CDN 使用 SRI、季度审计
  - 响应头：HSTS、X-Content-Type-Options、X-Frame-Options、Referrer-Policy、Permissions-Policy
  - 表单：CSRF 防护、限流、客户端 + 服务端验证、蜜罐优于 CAPTCHA
- **扩展**：common/security.md

### web/testing.md

- **用途**：Web 特定的测试优先级与规范。
- **核心规则**：
  - 优先级顺序：视觉回归 > 无障碍 > 性能 > 跨浏览器 > 响应式
  - 视觉回归：关键断点截图（320、768、1024、1440）；测试 hero/滚动叙事区域
  - 无障碍：自动化检查、键盘导航、减弱动效、颜色对比度
  - 性能：对关键页面运行 Lighthouse
  - 跨浏览器：最低 Chrome、Firefox、Safari
  - 响应式：测试 320、375、768、1024、1440、1920；无溢出；触摸交互
  - E2E：Playwright；避免基于超时的不稳定断言；优先使用确定性等待
- **扩展**：common/testing.md
