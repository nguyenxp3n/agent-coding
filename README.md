# Agent-Coding: Universal Behavioral Rules & Engineering Skills Kit for AI Coding Agents

[![AI Compatibility: Claude Code](https://img.shields.io/badge/Claude%20Code-Compatible-6366f1.svg)](#claude-code)
[![AI Compatibility: Cursor](https://img.shields.io/badge/Cursor-Compatible-000000.svg)](#cursor)
[![AI Compatibility: Windsurf](https://img.shields.io/badge/Windsurf-Compatible-0ea5e9.svg)](#windsurf)
[![Discipline: Senior-Level](https://img.shields.io/badge/Discipline-Senior--Level-10b981.svg)](#core-philosophy)
[![License: MIT](https://img.shields.io/badge/License-MIT-gray.svg)](#license)

An enterprise-ready, battle-tested behavioral framework, procedural skill library, and specialized auditor persona kit for autonomous AI software engineering agents (Claude Code, Cursor, Windsurf, Codex, Aider).

---

## Executive Summary

Raw LLMs deployed as autonomous coding agents frequently succumb to predictable software engineering failure modes:
- **Speculative Boilerplate:** Creating unnecessary abstractions, mock files, and configuration scaffolding before validating real needs.
- **Context Bloat:** Slurping massive codebases into prompt windows, driving up latency and degrading reasoning precision.
- **Silent Failures:** Wrapping operations in empty `try/catch` blocks or swallowing promises, masking fatal defects.
- **Scope Creep & Collateral Churn:** Modifying adjacent formatting or refactoring working code outside the requested diff boundary.
- **Untracked Hallucinations:** Introducing unverified third-party dependencies when simple standard library implementations suffice.

**Agent-Coding** solves this through a deterministic, 3-tier operational architecture:
1. **Tier 1: Behavioral Directives & Core Rules (`rules/` & `AGENTS.md`)** — Immutable boundaries enforcing YAGNI, surgical edits, and linear workflows.
2. **Tier 2: Standardized Procedural Skills (`skills/`)** — Reproducible runbooks for onboarding, planning, TDD, systematic debugging, and verification.
3. **Tier 3: Specialized Auditor Personas (`agents/`)** — Multi-perspective reviewer specifications for security, database, performance, and language-specific correctness.

---

## Repository Structure

```text
Agent-coding/
├── .gitignore               # Strict exclusion of caches, vendor bloat, and secrets
├── AGENTS.md                # Master behavioral specification and rule index
├── README.md                # Industrial system overview and integration guide
│
├── agents/                  # Specialized Reviewer & Auditor Personas (Markdown Prompts)
│   ├── analyst.md               # Requirements refinement & edge-case exploration
│   ├── architect.md             # System boundaries, contract design & data modeling
│   ├── database-reviewer.md     # PostgreSQL, indexing strategy, query optimization
│   ├── doc-updater.md           # Living documentation & token-efficient codemaps
│   ├── performance-optimizer.md # Profiling, bundle splitting, memory leak hunting
│   ├── plan-reviewer.md         # Pre-execution plan validation & risk assessment
│   ├── planner.md               # Linear/Jira task breakdown & dependency ordering
│   ├── react-reviewer.md        # Component lifecycles, hook deps, render cycles
│   ├── refactor-cleaner.md      # Dead-code elimination, unused import cleanup
│   ├── security-reviewer.md     # OWASP Top 10, sanitization, secret leakage audits
│   ├── silent-failure-hunter.md # Try/catch swallowing, unhandled rejections
│   └── typescript-reviewer.md   # Strict type enforcement, zero-`any` compliance
│
├── rules/                   # Deterministic Engineering Constraints & Style Guidelines
│   ├── core/
│   │   ├── coding-style.md      # Idiomatic patterns, naming, and error semantics
│   │   ├── docs.md              # Documentation maintenance criteria
│   │   ├── file-creation.md     # Zero-speculative file creation rules
│   │   ├── linear-workflow.md   # Sequential milestone execution
│   │   ├── patterns.md          # Architectural anti-patterns and guardrails
│   │   └── workflow.md          # Iterative development and verification loops
│   ├── docs/
│   │   └── living-docs.md       # Synchronization of specs with codebase reality
│   ├── react/
│   │   └── patterns.md          # Idiomatic React component and state conventions
│   └── typescript/
│       ├── coding-style.md      # Type-safety primitives and structural patterns
│       └── patterns.md          # Modern TypeScript design patterns
│
└── skills/                  # Standardized Runbooks & Procedural Skills
    ├── brainstorm/              # Issue/ticket-driven spec discovery
    ├── brainstorming/           # Collaborative intent classification and design
    ├── codebase-onboarding/     # Rapid repository mapping and architectural survey
    ├── context-budget/          # Token rationing, selective reading, diff-minimization
    ├── diagnosing-superpowers/  # Agent harness diagnostic and capability self-test
    ├── dispatching-parallel-agents/ # Multi-subagent fan-out orchestration
    ├── docs-drift/              # Drift detection between documentation and codebase
    ├── executing-plans/         # Checkpoint-based plan execution with proof gates
    ├── explain/                 # Architectural reasoning, tradeoffs, and rationale
    ├── finishing-a-development-branch/ # Git cleanup, commit curation, and PR prep
    ├── frontend-design-bar/     # Production UI/UX design tokens and heuristics
    ├── hand-off/                # Multi-session handoff documentation
    ├── interview-me/            # Socratic requirement elicitation
    ├── log-wiki/                # Architecture Decision Record (ADR) and wiki logging
    ├── planning/                # Linear issue breakdown and subtask sequencing
    ├── prototype/               # Throwaway spikes for risk reduction
    ├── receiving-code-review/   # Structured, defensible review remediation
    ├── requesting-code-review/  # PR review briefing and diff packaging
    ├── review/                  # General-purpose peer code review rubric
    ├── review-change/           # Scope-creep and collateral diff auditor
    ├── review-experience/       # Interaction smoothness and UX validation
    ├── review-health/           # Codebase health, maintainability, and tech debt
    ├── review-release/          # Release-readiness checklist and gates
    ├── security-review/         # Proactive vulnerability, secret, and auth scanning
    ├── subagent-driven-development/ # Isolated worker agent execution
    ├── systematic-debugging/    # 4-phase root-cause isolation protocol
    ├── test-driven-development/ # Strict Red-Green-Refactor implementation cycles
    ├── using-git-worktrees/     # Zero-risk execution in temporary git worktrees
    ├── using-superpowers/       # Meta-skill dispatcher and discovery engine
    ├── verification-before-completion/ # Proof-of-correctness before marking tasks complete
    ├── writing-plans/           # Machine-executable implementation blueprints
    └── writing-skills/          # Meta-authoring framework for new procedural skills
```

---

## Core Philosophy: The 4 Non-Negotiables

All agent operations governed by this kit follow four non-negotiable principles:

| Principle | Rule | Agent Enforcement |
|:---|:---|:---|
| **1. Think Before Coding** | No implementation without alignment | Surface assumptions explicitly. Reject vague briefs. Ask clarifying questions instead of guessing. |
| **2. Simplicity First** | YAGNI & Stdlib-first | Prefer platform-native APIs. No premature abstractions or speculative configurations. Shortest working diff wins. |
| **3. Surgical Changes** | Minimal blast radius | Only touch code directly required by the prompt. Never touch unrelated whitespace, comments, or working code. |
| **4. Goal-Driven Execution** | Red-Green-Refactor verification | Turn tasks into verifiable test gates. Never declare victory without reproducible execution evidence. |

---

## Integration Guide

### 1. Claude Code CLI

Claude Code recognizes global or repository-level instructions and agent configurations:

#### Method A: Direct Project Instruction Link (`CLAUDE.md`)
Add the following line to your project's `CLAUDE.md`:
```markdown
# Agent Instructions
@../Agent-coding/AGENTS.md
```
Or symlink `AGENTS.md` directly into your workspace:
```bash
ln -s /path/to/Agent-coding/AGENTS.md ./CLAUDE.md
```

#### Method B: Skills & Agents Registration
Copy or link `skills/` and `agents/` to your `.claude` configuration directory:
```bash
# Register skills
mkdir -p .claude/skills
cp -r /path/to/Agent-coding/skills/* .claude/skills/

# Register specialized personas
mkdir -p .claude/agents
cp -r /path/to/Agent-coding/agents/* .claude/agents/
```

---

### 2. Cursor IDE

Cursor operates via `.cursorrules` or the modular `.cursor/rules/` directory:

#### Method A: Global Rules File (`.cursorrules`)
Create or append to `.cursorrules` in your project root:
```markdown
# Behavioral Directives
You must strictly follow the behavioral standards and surgical change discipline defined below:

- Simplicity First: Minimum viable code. YAGNI. No speculative abstractions.
- Surgical Edits: Do not touch lines outside the required diff scope.
- Think Before Coding: Elicit ambiguous requirements before modifying files.
- Verification: Always verify your changes with explicit unit checks or terminal commands.

For detailed rules and specialized personas, reference:
- Core Rules: path/to/Agent-coding/rules/core/
- Specialized Reviewers: path/to/Agent-coding/agents/
```

#### Method B: Modular Cursor Rules (`.cursor/rules/*.mdc`)
Create `.cursor/rules/agent-coding.mdc`:
```markdown
---
description: Universal engineering standards and surgical edit rules
globs: *
---
@path/to/Agent-coding/AGENTS.md
```

---

### 3. Windsurf IDE

Windsurf uses `.windsurfrules` located at the root of the workspace:

Create `.windsurfrules`:
```markdown
# Universal Agent-Coding Guidelines

1. Socratic Alignment: If requirements are ambiguous, clarify before editing.
2. Minimal Blast Radius: Never reformat adjacent code or make cosmetic refactors.
3. Silent Failure Prevention: Never catch exceptions silently. Always handle or rethrow.
4. Test-Driven Verification: Write or execute an automated verification check for every change.

Refer to:
- Rules: path/to/Agent-coding/rules/core/coding-style.md
- Persona Rubrics: path/to/Agent-coding/agents/
```

---

## Specialized Agent Personas (`agents/`)

When reviewing code, planning architectures, or performing audits, activate specialized personas for deterministic evaluation:

| Persona | Focus Domain | Key Check |
|:---|:---|:---|
| **`security-reviewer.md`** | AppSec / OWASP | Injection, broken auth, unescaped HTML, exposed secrets |
| **`silent-failure-hunter.md`** | Robustness | Empty `catch`, swallowed promises, unlogged errors |
| **`performance-optimizer.md`** | Runtime & Bundle | N+1 queries, bundle bloat, unnecessary re-renders |
| **`database-reviewer.md`** | Data Layer | Missing indexes, sequential scans, unmigrated schemas |
| **`react-reviewer.md`** | Frontend Correctness | Hook dependency completeness, state tearing, key stability |
| **`typescript-reviewer.md`** | Type Safety | Elimination of `any`, unsafe type casting, exhaustiveness |
| **`refactor-cleaner.md`** | Hygiene | Dead imports, orphaned functions, leftover debug code |
| **`plan-reviewer.md`** | Execution Risk | Plan soundness, missing rollback steps, circular dependencies |

---

## Procedural Engineering Skills (`skills/`)

Skills provide turn-by-turn guidance for complex developer workflows:

- **Systematic Debugging (`skills/systematic-debugging`):** A strict 4-phase protocol preventing random "trial-and-error" fixes:
  1. *Root Cause Isolation:* Reproduce consistently and trace state backwards.
  2. *Hypothesis Formulation:* Validate exact failure conditions.
  3. *Minimal Fix:* Apply the single smallest modification.
  4. *Defensive Verification:* Prove bug resolution without regressions.

- **Test-Driven Development (`skills/test-driven-development`):** Red-Green-Refactor workflow ensuring code is testable by design.

- **Context Budgeting (`skills/context-budget`):** Guidelines to prevent LLM context exhaustion, keeping responses fast, focused, and cheap.

- **Git Worktrees (`skills/using-git-worktrees`):** Isolate risky agent spikes and exploratory tasks from your working branch.

---

## Security & Privacy Guarantee

- **Zero Hardcoded Secrets:** This repository strictly prohibits secrets, API tokens, passwords, or personal credentials.
- **Path Agnostic:** All paths and references are designed to work across POSIX and Windows environments without hardcoded local user directories.
- **Enterprise Safe:** Contains zero telemetry, tracking scripts, or unauthorized network calls.

---

## License

Distributed under the MIT License. Free for open-source, commercial, and personal use.
