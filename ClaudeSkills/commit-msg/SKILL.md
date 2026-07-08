---
name: commit-msg
description: "Generate a semantic commit message from staged git changes and commit them. Use this skill whenever the user says 'write a commit message', 'generate a commit', 'commit my changes', 'commit this', or runs /commit-msg — even if they don't spell out the format. Follows a strict type(scope)[#taskId]: summary convention."
---

# Commit Message Generator

Generate a commit message in my semantic format from staged changes, then commit.

## Workflow

1. **Check for staged changes** with `git diff --staged --stat`. If nothing is staged, **stop** and tell me to stage my changes first (e.g. `git add`). Do not stage anything yourself.
2. **Read the staged diff** with `git diff --staged` to understand what changed.
3. **Generate a commit message** in the format below.
4. **Commit** with `git commit -m "<subject>" -m "<body>"` (omit the second `-m` if there's no body). **Never** add a `Co-Authored-By` trailer or any Claude/AI attribution.

## Format

```
type(scope)[#taskId]: summary

- optional body bullet
- optional body bullet

footer
```

### Subject line
- `type` — lowercase, from the list below.
- `scope` — the exact area modified, in round brackets, PascalCase (e.g. `MainMenu`, `Player`, `JobSystem`).
- `[#taskId]` — task ID in square brackets, if known. If I haven't provided one, ask me for it or leave it out — do not invent one.
- `summary` — starts lowercase, no trailing period, brief description of the change in **past simple** tense (e.g. "added", "disabled", "moved" — not "add", "disable", "move").
- **Whole subject line must be under 60 characters.** Keep it tight.

### Body (optional but encouraged)
- Bullet points, written in **past simple** tense (e.g. "added", "disabled", "moved").
- Brief and informative. Explain *what* changed and *why* if not obvious.
- Always in English.

### Footer (optional)
- Link to the issue/story in the tracker if applicable.

## Types

| type | when to use |
|---|---|
| `feat` | new feature, changed mechanic or behavior — not content itself |
| `fix` | fixes/restores behavior introduced by a `feat` |
| `content` | new content or changes to existing assets or their in-engine representation |
| `refactor` | same behavior: script refactors, stylistic code changes, directory restructure, renaming, convention changes |
| `balance` | changed parameter values in existing scriptable objects, prefabs, or settings |
| `external` | changes in external plugins/editors/tools outside this project's scope |
| `merge` | use git's default merge message |
| `docs` | documentation changes, including in-script docs |
| `version` | engine, project, or tool version bump (tag the commit for project versioning) |

## Language rules
- Always English.
- Body comments in **past simple**.
- Brief and informative.

## Examples

```
content(CutScenes)[#66j00w]: added new voice overs for cut scenes
```
```
fix(Rat)[#6t30hw]: disabled rat's collider after first use
```
```
feat(TextBoard)[#84j0fs]: added dictionary for text variables in TextBoard
```

## Hard rules
- If nothing is staged → stop, ask me to stage first.
- Subject under 60 characters.
- Never a `Co-Authored-By` trailer or AI attribution.
- Don't invent task IDs.
- Use Past Simple in both summary and body
