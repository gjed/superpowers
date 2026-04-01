# OpenSpec Integration Reference

Read this file after detecting OpenSpec state (detection happens inline in each skill).

## State: Not Installed

When `command -v openspec` fails, show the user:

> OpenSpec is not installed. To use OpenSpec integration, run:
> `npm install -g @fission-ai/openspec@latest`
> Then run `openspec init` in your project root and restart this session. Continuing with standard superpowers output.

Use standard fallback paths (see below).

## State: Not Initialized

When `command -v openspec` passes but `test -d openspec` fails, show the user:

> OpenSpec is installed but not initialized in this project. To enable OpenSpec integration, run:
> `openspec init`
> in your project root and restart this session. Continuing with standard superpowers output.

Use standard fallback paths (see below).

## State: Ready (OpenSpec mode)

When both checks pass, use the artifact mapping below.

## Artifact Mapping (OpenSpec mode)

| Superpowers concept | OpenSpec path |
|---|---|
| Change name | Derived from the brainstorming topic in kebab-case (e.g. topic "Add dark mode" → `add-dark-mode`) |
| Change folder | `openspec/changes/<name>/` — create if absent |
| Proposal / motivation | `openspec/changes/<name>/proposal.md` |
| Specs (one file per area) | `openspec/changes/<name>/specs/<area>/spec.md` — `<area>` is a short label for the concern being specified (e.g. `ui`, `api`, `auth`) |
| Design | `openspec/changes/<name>/design.md` |
| Implementation tasks | `openspec/changes/<name>/tasks.md` |

After writing all artifacts, commit the files to git. OpenSpec does not manage versioning automatically.

## Standard Fallback Paths

In standard mode (OpenSpec absent), the brainstorming spec and writing-plans plan are written as single documents:

| Artifact | Standard path |
|---|---|
| Brainstorming output (proposal + specs + design combined) | `docs/superpowers/specs/YYYY-MM-DD-<topic>-design.md` |
| Writing-plans output (tasks) | `docs/superpowers/plans/YYYY-MM-DD-<feature-name>.md` |
