---
name: task-define
description: Define a new task file in tasks/backlog/ — problem, scope, acceptance criteria. Invoke with /gl:task-define. Use type defect for bug reports.
---

# Task Define (`/gl:task-define`)

## Usage
```
/gl:task-define <short title or topic>
/gl:task-define   # then collaborate to name the file
```

You may also target a path explicitly: `/gl:task-define @tasks/backlog/YYYYMMDD_description.md`

## Objective
Collaborate with the user to **define a task** with clear, executable requirements — **product-manager style**, not implementation design.

**This skill does not implement code.** It may only create/update the task markdown file (and minimal scaffolding if needed).

## Output
A task file under `tasks/backlog/` named `YYYYMMDD[_NN]_<description>.md`:

```yaml
---
status: backlog
---
```

Include: problem, scope, acceptance criteria, quality gates, optional constraints, risks.

### Defect tasks (`type: defect` in body or title)
Capture:
- Observed problem, **expected** vs **actual**
- Reproduction steps
- Environment, logs, links as available

## Collaboration Process

1. **Problem** — Current situation, evidence, impact, cost of inaction.
2. **Scope** — In-scope / out-of-scope, dependencies, constraints, assumptions.
3. **Success** — Acceptance criteria (observable), validation steps, rollback if relevant.
4. **Write file** — Use naming convention; `status: backlog`.
5. **Confirm** — User agrees the task is ready for **`/gl:implement-task`** (or planning if part of a larger plan).

## Discipline
- Do not choose implementation solutions here; capture requirements and validation only.
- For maintenance types (`refactor`, `upgrade`, `chore`), same structure; scope tightly.
