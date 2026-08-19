---
name: feature-spec
description: Working specs in .shed/specifications, written up to docs/explanations/implementation when done, plus the task format that goes with them. Use when starting non-trivial feature work or a redesign, when picking work back up mid-feature, when a feature is finished and needs writing up, and when writing a task for a tracker or for .shed/tasks.
---

# Feature spec

Non-trivial work gets a spec before code. The spec is a living working document
during the feature, and produces a permanent explanation document at the end.

Trivial work does not need a spec. A bug fix, a rename, a one-file change: skip
this. If the work needs an approach discussion, it needs a spec.

## Layout

```
.shed/
  specification-template.md   # project override, optional
  task-template.md            # project override, optional
  specifications/             # in progress
  done/                       # shipped, written up
  tasks/                      # local task tracking, when there is no tracker
docs/explanations/implementation/   # permanent write-ups
```

Create these directories as you need them, and make sure `.shed` is in the
`.gitignore` file, if it exists. Always ask before creating these.

## Starting

1. Resolve the template. Use `.shed/specification-template.md` if the project
   has one. Otherwise copy this skill's `specification-template.md` into
   `.shed/` and use that, so the project has it from now on.
2. Write `.shed/specifications/<kebab-case-name>.md` from the template.
3. Fill in Context/Problem, Goal, Scope and Open questions. Leave Approach thin
   until the approach is agreed.
4. Show the spec and get approval before writing code.

## While working

The spec is the working document, not a record of what was decided once. Update
it as the design changes: move settled items out of Open questions into
Approach, correct Scope when it shifts, note rejected designs and why. A spec
that still describes the plan from three days ago is worse than no spec.

Break the work into chunks, each with a clear commit message.

## Finishing

When the feature ships:

1. Write `docs/explanations/implementation/<snake_case_name>.md`. This is a
   higher level overview than the spec: background context, what was built, and
   any non-obvious considerations. Length follows the feature. A simple feature
   needs a few paragraphs. A complex one, or one with awkward trade-offs, needs
   more.
2. The write-up explains the shipped system to someone who was not in the
   conversation. It is not a changelog and not a copy of the spec.
3. Move the spec to `.shed/done/`.

## Tasks

Work that falls out of a spec but is not part of it becomes a task only when
the project already tracks tasks, or when asked for one. Otherwise it belongs
in the spec's Open questions or nowhere. Do not file tasks unprompted.

Tasks go wherever the project already tracks them: Notion, ClickUp, Linear,
GitHub issues. Where there is no tracker, `.shed/tasks/<kebab-case-name>.md`.
Use the same structure either way, so tasks stay comparable.

Resolve the template as with the spec one. Use `.shed/task-template.md` if the
project has one, otherwise copy this skill's `task-template.md` into `.shed/`
and use that.

Keep every heading even when a section is one line. "Nothing open" beats a
missing heading. Name the file, function or column the task concerns in the
title where one exists.
