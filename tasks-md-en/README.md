# tasks-md

A lightweight backlog for local software work: tasks that need to be resumed,
tracked, or documented. Small fixes finished in the same working session do not
need a task file unless the decision is worth keeping.

## Layout

- `tasks-md/`: open tasks.
- `tasks-md/TEMPLATE.md`: model for new tasks.
- `tasks-md/notes/`: working notes — investigations, command outputs, comparisons,
  environment results. Create when needed.
- `tasks-md/archived/`: done tasks. Create when needed.
- `tasks-md/deleted/`: cancelled tasks. Create when needed.

## Existing tasks

Use this standard for new tasks. Existing tasks may keep their format, file names,
fields, and status values; do not reformat the backlog in bulk just to match it.
For legacy tasks, keep status and location consistent with the project's existing
conventions (for example, `closed` in `archived/` and `tombstone` in `deleted/`).
When intentionally migrating a task, use the current template and status values,
preserve useful content and external issue references, and update affected links.

## Workflow

1. Before creating a task, search `tasks-md/` for a related one.
2. If it exists, update the same file.
3. If it does not, copy `TEMPLATE.md` to a short descriptive slug, e.g.
   `fix-upload-timeout.md` or `corrigir-timeout-de-upload.md`.
4. Keep `Current state` short and current. Put detailed material in `notes/`
   and link it from the task.
5. To finish: update `Current state` with the outcome and validation, set
   `status: done`, move the file to `archived/`.
6. To cancel: record the reason briefly in `Current state`, set
   `status: cancelled`, move the file to `deleted/`.

Whenever a task or note moves or is renamed, update relative paths inside it
and references to it in other files. For example, after archiving a task, its
reference to an open task changes from `other-task.md` to `../other-task.md`.

## Task file

Three sections, in this order:

- **Purpose** — the problem or desired outcome, and the limit of the work.
  Keep it relatively stable; it explains *what* and *how far*.
- **Done when** — verifiable completion criteria.
- **Current state** — a replaceable summary of what is true now and the next
  step. Update it whenever the task state changes; remove superseded decisions.
  When closing, it becomes the outcome, the validation performed, and any
  relevant limitation.

Do not create extra sections by default. If there is material that does not fit,
that is what `notes/` is for.

## Front matter

Minimum fields, already present in `TEMPLATE.md`:

```yaml
title: "Short clear title"
status: "open"
created_at: "YYYY-MM-DD"
updated_at: "YYYY-MM-DD"
```

- `status` is one of `open`, `deferred`, `done`, `cancelled`.
  `done` pairs with `archived/`, `cancelled` with `deleted/`.
- Dates are `YYYY-MM-DD`. When exact timestamps matter, `git log` already has them.
- Update `updated_at` whenever the task file changes.

Optional fields — add only when they are actually useful:

```yaml
labels: [api, bug]      # helps grouping/search
tracker: AX-123         # external issue ID (Jira, Linear, ...)
```

Do not add empty fields. `priority`, `owner`, and `issue_type` are intentionally
not part of the standard.

## Notes (`notes/`)

Notes are free-form Markdown with no template and no front matter.

- Use them for anything too big for a task: extended investigations, command
  output, alternatives compared, results specific to a machine or environment.
- Link from the task with a relative path: `notes/upload-timeout-investigation.md`.
- Do not duplicate: the task states goal, criteria, and current state; the note
  holds the supporting material. The note does not repeat the task's live state.
- When a task is archived or deleted, move its notes to `archived/notes/` or
  `deleted/notes/` if they are worth keeping and no open task still uses them.
  Keep shared notes in `notes/` while open tasks need them; archived or cancelled
  tasks can reference them as `../notes/<note>.md`.

## Naming

- Short descriptive slugs, lowercase, in the language the project works in.
  `fix-upload-timeout.md`, `corrigir-timeout-de-upload.md` — both are fine.
- No random IDs, no sequential numbers, no status in the file name.
- If a task has an external issue ID, the ID belongs in the front matter
  (`tracker:`), not in the file name.

## Association between tasks

- Link tasks by relative path only when the relation clarifies scope, dependency,
  or history (relative to the task file, e.g. `archived/larger-task.md`):
  - `Related: `other-task.md``
  - `Split from: `archived/larger-task.md``
- Do not link tasks that merely share a vague theme.

## Validation

For changes inside `tasks-md/` only, validate by reading the files. Git status
does not verify Markdown content.
