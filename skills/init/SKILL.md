---
name: init
description: Load GearLoop rules into the current session. Run this once at session start if you are not using the gl agent. Rules persist until context compaction.
disable-model-invocation: true
---

# GearLoop Rules

The following rules govern all GearLoop SDLC skills. They are loaded into your session context now.

---

## Core Principles
!`cat ${CLAUDE_SKILL_DIR}/../../rules/first-principles.md`

---

## Task Management Standard
!`cat ${CLAUDE_SKILL_DIR}/../../rules/task-management.md`

---

Rules loaded. You can now use any `/gl:*` skill with these rules active. If the session compacts, run `/gl:init` again.
