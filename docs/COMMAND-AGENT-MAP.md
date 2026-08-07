# Command → Agent / Skill Map

This document lists each slash command and the primary agent(s) or skills it invokes, plus notable direct-invoke agents. Use it to discover which commands use which agents and to keep refactoring consistent.

## Slash Commands

| Command | Description | Primary agent(s) | Notes |
|---------|-------------|------------------|-------|
| `/build-fix` | Detect build system and fix build/type errors | — (standalone) | Language-agnostic, no dedicated agent |
| `/checkpoint` | Create, verify, or list workflow checkpoints | — (skill: verification-loop) | |
| `/code-review` | Code review — local changes or GitHub PR | — (standalone) | No single agent; dispatches by language |
| `/cost-report` | Generate local cost report from ECC cost-tracker | — | Metrics log only |
| `/ecc-guide` | Navigate ECC agents, skills, commands, hooks, docs | — | Interactive guide |
| `/evolve` | Analyze instincts and suggest evolved structures | — (skill: continuous-learning-v2) | |
| `/feature-dev` | Guided feature development with architecture focus | architect, code-architect, code-explorer, code-reviewer | Multi-agent orchestration |
| `/go-build` | Fix Go build errors, vet warnings, linter issues | go-build-resolver | |
| `/go-review` | Go code review: idiomatic, concurrency, error handling | go-reviewer | |
| `/go-test` | TDD workflow for Go with table-driven tests | — (standalone) | No tdd-guide; self-contained |
| `/harness-audit` | Deterministic repo harness audit and scorecard | — | No single agent |
| `/learn` | Extract reusable patterns from session | — (skill: continuous-learning) | |
| `/learn-eval` | Extract patterns, self-evaluate, then save | — (skill: continuous-learning-v2) | |
| `/loop-start` | Start managed autonomous loop with safety defaults | loop-operator | |
| `/loop-status` | Inspect active loop state and progress | loop-operator | |
| `/model-route` | Recommend best model tier for current task | — | No agent; heuristic-based |
| `/orch-add-feature` | Orchestrate new feature end-to-end | code-reviewer, security-reviewer | Wrapper for orch-add-feature skill |
| `/orch-build-mvp` | Orchestrate MVP bootstrap from spec | planner, code-reviewer, security-reviewer | Wrapper for orch-build-mvp skill |
| `/orch-change-feature` | Orchestrate altering existing feature | code-reviewer, security-reviewer | Wrapper for orch-change-feature skill |
| `/orch-fix-defect` | Orchestrate bug fix with regression test | code-explorer, code-reviewer, security-reviewer | Wrapper for orch-fix-defect skill |
| `/orch-refine-code` | Orchestrate behavior-preserving refactor | code-reviewer, refactor-cleaner | Wrapper for orch-refine-code skill |
| `/orch-review` | Run orch-review Workflow over diff or PR | — (native Workflow) | No single agent |
| `/plan` | Restate requirements, create step-by-step plan | planner, architect | |
| `/plan-canvas` | Open plan/HTML in browser for annotate-and-approve | — (skill: plan-canvas) | |
| `/plan-prd` | Generate lean PRD, hand off to /plan | architect | |
| `/pr` | Create GitHub PR from current branch | — (standalone) | Template discovery, change analysis |
| `/project-init` | Detect stack, produce ECC onboarding dry-run | — | Uses install manifests |
| `/projects` | List known projects and instinct stats | — (skill: continuous-learning-v2) | |
| `/promote` | Promote project instincts to global scope | — (skill: continuous-learning-v2) | |
| `/prp-commit` | Quick commit with natural language file targeting | — (standalone) | |
| `/prp-implement` | Execute implementation plan with validation loops | — (standalone) | |
| `/prp-plan` | Comprehensive feature plan with codebase analysis | architect | |
| `/prp-prd` | Interactive PRD generator with back-and-forth | architect | |
| `/prp-pr` | Create GitHub PR (PRP variant) | — (standalone) | |
| `/python-review` | Python review: PEP 8, type hints, security | python-reviewer | |
| `/quality-gate` | Run ECC formatter quality gate for a file | — (hook-like) | |
| `/react-build` | Fix React build failures (Vite/webpack/Next/etc.) | react-build-resolver | |
| `/react-review` | React review: hooks, render perf, a11y, security | react-reviewer, typescript-reviewer | TSX/JSX triggers TS reviewer |
| `/react-test` | TDD workflow for React with RTL | react-reviewer, tdd-guide | |
| `/refactor-clean` | Safely identify and remove dead code | — (standalone) | No refactor-cleaner agent invoked |
| `/resume-session` | Load most recent session and resume work | — (skill: session-management) | |
| `/review-pr` | Comprehensive PR review with specialized agents | code-reviewer, code-simplifier, pr-test-analyzer, type-design-analyzer | Multi-agent dispatch |
| `/rust-build` | Fix Rust build errors, borrow checker issues | rust-build-resolver | |
| `/rust-review` | Rust review: ownership, lifetimes, unsafe | rust-reviewer | |
| `/rust-test` | TDD workflow for Rust with cargo-llvm-cov | — (standalone) | No tdd-guide; self-contained |
| `/santa-loop` | Adversarial dual-review convergence loop | code-reviewer | Two independent reviewers |
| `/save-session` | Save session state for future resumption | — (skill: session-management) | |
| `/security-scan` | Run AgentShield against agent/hook/MCP surfaces | security-reviewer | Via security-scan skill |
| `/sessions` | Manage session history and metadata | — | |
| `/setup-pm` | Configure preferred package manager | — | Script-based |
| `/skill-create` | Extract coding patterns from git history | — (standalone) | Local Skill Creator |
| `/skill-health` | Skill portfolio health dashboard | — | Analytics only |
| `/test-coverage` | Analyze coverage, identify gaps, generate tests | — (standalone) | |
| `/update-codemaps` | Scan structure, generate architecture codemaps | architect | |
| `/update-docs` | Sync docs from source-of-truth files | — (standalone) | No doc-updater agent invoked |
| `/vue-review` | Vue review: Composition API, reactivity, security | vue-reviewer, typescript-reviewer | .vue/.ts triggers TS reviewer |

## Agents

| Agent | Model | Purpose |
|-------|-------|---------|
| `architect` | opus | System design, scalability, technical decisions |
| `build-error-resolver` | sonnet | Build/TypeScript error resolution with minimal diffs |
| `code-architect` | sonnet | Feature architecture from codebase patterns |
| `code-explorer` | sonnet | Deep codebase analysis: execution paths, layers, deps |
| `code-reviewer` | sonnet | Code quality, security, maintainability review |
| `code-simplifier` | sonnet | Simplify and refine code for clarity |
| `cpp-build-resolver` | sonnet | C++/CMake build and linker error resolution |
| `database-reviewer` | sonnet | PostgreSQL optimization, schema design, security |
| `doc-updater` | haiku | Documentation and codemap specialist |
| `docs-lookup` | haiku | Context7 MCP docs/API lookup with examples |
| `e2e-runner` | sonnet | E2E testing with Playwright, artifact management |
| `go-build-resolver` | sonnet | Go build/vet/linter error resolution |
| `go-reviewer` | sonnet | Go idiomatic, concurrency, error handling review |
| `java-build-resolver` | sonnet | Java/Maven/Gradle build error resolution (Spring Boot, Quarkus) |
| `java-reviewer` | sonnet | Java review: layered arch, JPA, security, concurrency |
| `loop-operator` | sonnet | Operate autonomous loops, monitor and intervene |
| `performance-optimizer` | sonnet | Bottleneck analysis, bundle size, runtime optimization |
| `planner` | opus | Complex feature and refactoring planning |
| `pr-test-analyzer` | sonnet | PR test coverage quality and completeness |
| `python-reviewer` | sonnet | Python PEP 8, type hints, security, performance |
| `react-build-resolver` | sonnet | React build failures across Vite/webpack/Next/etc. |
| `react-reviewer` | sonnet | React hooks, render perf, server/client boundaries, a11y |
| `refactor-cleaner` | sonnet | Dead code cleanup with analysis tools (knip, depcheck) |
| `rust-build-resolver` | sonnet | Rust cargo/borrow checker error resolution |
| `rust-reviewer` | sonnet | Rust ownership, lifetimes, unsafe review |
| `security-reviewer` | sonnet | OWASP Top 10, secrets, injection, SSRF detection |
| `spec-miner` | opus | Extract behavioral specs from codebases for OpenSpec |
| `tdd-guide` | sonnet | TDD enforcement: write-tests-first, 80%+ coverage |
| `type-design-analyzer` | sonnet | Type design: encapsulation, invariants, enforcement |
| `typescript-reviewer` | sonnet | TypeScript/JS type safety, async, security review |
| `vue-reviewer` | sonnet | Vue Composition API, reactivity, template security |

## Non-Slash CLI Surfaces

| CLI surface | Primary skill/runtime | Notes |
|-------------|-----------------------|-------|
| `ecc memory init` | unified-memory / `scripts/memory.js` | Initialize project, team, or user Markdown vault scopes |
| `ecc memory save` | unified-memory / `scripts/memory.js` | Create unreviewed memory; body must come from stdin or a regular file |
| `ecc memory handoff` | unified-memory / `scripts/memory.js` | Create a targeted, cross-harness handoff |
| `ecc memory search` | unified-memory / `scripts/memory.js` | Bounded lexical search over selected vault scopes |
| `ecc memory read` | unified-memory / `scripts/memory.js` | Read one memory plus derived backlinks |
| `ecc memory doctor` | unified-memory / `scripts/memory.js` | Audit malformed files, duplicate IDs, broken links, and symlinks |
| `ecc-memory-mcp` | unified-memory / `scripts/memory-mcp.mjs` | Optional stdio MCP adapter; exposes save/search/read/doctor only |

## Skills Referenced by Commands

| Skill | Commands |
|-------|----------|
| continuous-learning | `/learn` |
| continuous-learning-v2 | `/learn-eval`, `/evolve`, `/promote`, `/projects` |
| verification-loop | `/checkpoint` |
| security-scan | `/security-scan` (runs AgentShield) |
| session-management | `/save-session`, `/resume-session` |
| plan-canvas | `/plan-canvas` |
| unified-memory | `ecc memory ...` and `ecc-memory-mcp` |

## How to Use This Map

- **Discoverability:** Find which command triggers which agent (e.g. "use `/code-review` for code-reviewer").
- **Refactoring:** When renaming or removing an agent, search this doc and the command files for references.
- **CI/docs:** The catalog script (`node scripts/ci/catalog.js`) outputs agent/command/skill counts; this map complements it with command–agent relationships.
