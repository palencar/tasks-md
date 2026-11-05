# tasks-md

Read this README in [Brazilian Portuguese](README.pt-BR.md).

A lightweight, file-based convention for tracking local software development tasks.

Each task is a single Markdown file. The directory is plain text, has no tooling
dependencies, and can be read and updated equally well by humans and coding agents.
It keeps just enough structure to stay useful over time and deliberately avoids
anything that feels like project-management overhead.

## What it is

- **One file per task**, in the `tasks-md/` directory at your project root.
- **A minimal template**: purpose, done-when criteria, and a living "current state"
  summary. Nothing more is required.
- **A minimal flow**: create, update, close. Closed tasks move to `archived/`,
  cancelled ones to `deleted/`.
- **A place for working notes** that are too detailed for the task but worth
  keeping: `tasks-md/notes/`.

## What it is not

- Not a task manager. There is no database, no CLI, no sync.
- Not a substitute for issue trackers. It complements them; a Jira/Linear ID can
  live in the file, but it is optional.
- Not a log. Progress history is optional. If you want dated audit entries, just
  write them in the file — but a short "current state" is the default.

## How to adopt it

Choose a language and copy that directory into your project root as `tasks-md/`:

- [English](tasks-md-en/README.md): copy `tasks-md-en/` as `tasks-md/`.
- [Português do Brasil](tasks-md-pt-BR/README.md): copy `tasks-md-pt-BR/` as `tasks-md/`.

Read `tasks-md/README.md` in the copied directory. Each language directory contains
the whole standard and can be adopted independently. Both versions use the same
rules, front matter field names and status values; the prose and section headings
are translated. All paths inside them use the adopted name, `tasks-md/`.

If your project already has `tasks-md/`, merge the conventions into its README
and template while preserving project-specific guidance. Follow the compatibility
rules in `tasks-md/README.md` for existing tasks.

Keep `tasks-md/README.md` as the shared guide for people and coding agents.
In your project's root `AGENTS.md`, add this instruction so agents know where
to find the task conventions:

```md
Before creating or updating local tasks, read `tasks-md/README.md` and follow
its conventions.
```

For projects using Brazilian Portuguese, the equivalent instruction is:

```md
Antes de criar ou atualizar tarefas locais, leia `tasks-md/README.md` e siga
suas convenções.
```

```
your-project/
  tasks-md/
    README.md     # conventions and workflow
    TEMPLATE.md   # template for new tasks
    # notes/      # working notes (create when needed)
    # archived/   # done tasks (create when needed)
    # deleted/    # cancelled tasks (create when needed)
```

Adapt freely: rename sections, add a field, drop one. The bar is that a new task
still takes under a minute to create and a task from three months ago is still
easy to pick up.

## Design principles

- **Text first.** Markdown files in a directory. Any editor, agent, or `grep` works.
- **Small files.** A task states the goal, when it is done, and what is true now.
  Everything bigger goes to `notes/`.
- **State over ceremony.** "Current state" is a replaceable summary of what matters
  today — not a formal status workflow.
- **No fake IDs.** File names are short descriptive slugs in the language the
  project works in. No random prefixes, no sequential numbers.
- **Close it and move it.** `archived/` and `deleted/` are created only when the
  first task needs them.

## License

This project is available under [CC0 1.0 Universal](LICENSE). You may copy,
adapt, and redistribute it, including for commercial purposes, without requiring
permission or attribution.

Attribution is appreciated but not required.
