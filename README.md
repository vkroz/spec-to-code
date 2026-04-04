# GearLoop

Claude Code plugin for AI-assisted SDLC: definition, architecture, planning, implementation, QA.


## Install


## Getting started

1. Install the plugin. 

```bash
/plugin install gl@<marketplace-name>
```

or install from local directory:
```bash
claude --plugin-dir /path/to/GearLoop
```

2. The `gl` agent activates automatically and loads behavioral rules. If your setup cannot use the `gl` agent, run `/gl:init` at session start instead.

3. Use plugin skills to run the workflows. Run `/gl:define` to start a new product, or `/gl:task-define` for a one-off task. See "Skills" section below for more details.

## Skills

### SDLC workflow (run in order for new products)

| Step | Command | What it does |
|------|---------|--------------|
| 0. Init (if no agent) | `/gl:init` | Load rules into session context |
| 1. Definition | `/gl:define` | Vision, spec, requirements in `docs/` |
| 2. Architecture | `/gl:design` | `docs/architecture.md` |
| 3. Planning | `/gl:plan` | `docs/implementation-plan.md` + task files in `tasks/backlog/` |
| 4. Implementation | `/gl:implement-task <task>` | One task: detailed design, code, tests |
| | `/gl:implement-phase <N>` | All tasks in phase N (sequential) |
| | `/gl:implement-all` | Full plan, phase by phase |
| 5. Integration test | `/gl:qa-integration-test` | Verify phase or ad-hoc work + regression |
| 6. System test | `/gl:qa-system-test` | Full product test, release gate |

### Task and maintenance

| Command | What it does |
|---------|--------------|
| `/gl:task-define` | New task file in `tasks/backlog/` (defects, refactors, chores) |
| `/gl:codebase-review` | Read-only audit, produces backlog tasks |

### Utilities

| Command | What it does |
|---------|--------------|
| `/gl:commit-code` | Staging and git commit guidance |
| `/gl:comment-code` | Add explanatory comments to code |

## Workflows supported

- **New product** — `/gl:define` → `/gl:design` → `/gl:plan` → `/gl:implement-*` → `/gl:qa-system-test`
- **Bug fix** — `/gl:task-define` (defect) → `/gl:implement-task` → `/gl:qa-integration-test` → `/gl:qa-system-test`
- **Maintenance** — `/gl:task-define` → `/gl:implement-task` → `/gl:qa-integration-test`
- **Incremental feature** — same as new product, but `/gl:define` amends existing docs
- **Codebase optimization** — `/gl:codebase-review` → `/gl:plan` → `/gl:implement-phase` → `/gl:qa-system-test`

## Project layout created by workflows

```
docs/vision.md
docs/spec.md
docs/requirements.md
docs/architecture.md
docs/implementation-plan.md
tasks/backlog/ | active/ | done/
```

Created incrementally as you run each stage — no upfront scaffolding.

## How rules are loaded

| Mechanism | How | Survives compaction | When to use |
|-----------|-----|---------------------|-------------|
| `gl` agent (default) | Automatic via `settings.json` | Yes | Recommended for most users |
| `/gl:init` | Manual, run once per session | No | When agent conflicts with another plugin |

Rules live in `rules/first-principles.md` and `rules/task-management.md`. The agent inlines them in its system prompt; `/gl:init` injects them via `!cat`.

## Development and testing

```bash
# Load the plugin locally without installing:
claude --plugin-dir ./

# After making changes, reload inside Claude Code:
/reload-plugins
```

See [`docs/GearLoop-specification.md`](docs/GearLoop-specification.md) for the full product vision and functional specification.
