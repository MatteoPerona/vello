# vello — agent instructions

## Purpose

vello (from *cervello*) is my personal context harness: plain markdown files describing my life and work across a full-time job (`work`), a side business (`biz`), and personal projects (`personal`). You work **from** these files — they are your memory of me — and you write **back** to them so the next session starts where this one ended. Files are the source of truth; if a file and your assumptions disagree, the file wins, and if a file is wrong, fix it.

## Map

| Path | What it holds | Changes |
|---|---|---|
| `core/me.md` | Who I am, constraints, working style, what "good" looks like | Rarely |
| `core/now.md` | This week: top 3 priorities, open loops, waiting on, blockers | Rewritten every session |
| `todo.md` | Single prioritized todo list, all domains | Every session |
| `ideas.md` | Ideas worth keeping that are not tasks | When ideas come up |
| `projects/*.md` | One file per project, any domain | When project state changes |
| `log/YYYY-MM-DD.md` | Daily append-only record of sessions | Every session |
| `wiki/index.md` + `wiki/*.md` | Durable knowledge about me and my world | When durable facts come up |
| `templates/` | Starting shapes for every file type | Rarely |

## Tiers: what to read when

`core/` is **always** read at session start. Everything else is read **only when needed**.

| If the question is about… | Read |
|---|---|
| What to do today / this week | `core/now.md`, `todo.md` |
| A specific task or priority | `todo.md` |
| A specific project | `projects/<name>.md`, then linked wiki pages/log dates |
| Which projects exist / are active | `projects/` — check frontmatter `status`; ignore `paused`/`done` unless asked |
| A person, tool, system, or topic you lack context on | `wiki/index.md`, then only the relevant page(s) |
| What happened on a given day, or why a decision was made | `log/YYYY-MM-DD.md` |
| An idea or "something I wanted to try" | `ideas.md` |
| How I like to work, my constraints | `core/me.md` (already loaded) |

Never read the whole wiki or the whole log. Open the index, pick pages, stop.

## Session start ritual

1. Read `core/me.md`, `core/now.md`, `todo.md`.
2. Read today's and yesterday's `log/` files if they exist.
3. Print a short situation report (≤10 lines):
   - top 3 priorities from `now.md`
   - the `## Now` items from `todo.md`
   - anything overdue, blocked, or waiting on someone
4. Open no other files until the conversation needs them.

If a core file is missing, say so and offer to seed it from `templates/`.

## Session end ritual

When I say we're done (or the session is clearly wrapping up):

1. **Log** — append an entry to `log/YYYY-MM-DD.md` (create it from `templates/log.md` if missing): what happened, decisions made, files changed.
2. **now.md** — rewrite `core/now.md` to reflect the current state of the week. Rewrite, don't append.
3. **todo.md** — add new tasks, move finished ones to `## Done (recent)` with the date, reprioritize.
4. **wiki/** — if a durable fact about me or my world came up, create/update the page and `wiki/index.md`.
5. **projects/** — update any project file whose state changed; bump `updated`.
6. **Summarize** in one paragraph what was written where.

## Routing: where new information goes

| It's… | It goes in |
|---|---|
| A concrete task | `todo.md` |
| An idea, not yet a commitment | `ideas.md` |
| An active effort with multiple steps | `projects/<name>.md` (+ its next action in `todo.md`) |
| A durable fact about a person, tool, system, or pattern | `wiki/<page>.md` |
| A durable fact about me (role, hours, hard constraint) | `core/me.md` — only if short; detail goes to the wiki |
| What happened today, a decision and its reason | `log/YYYY-MM-DD.md` |
| The state of this week | `core/now.md` |

If something is filed in the wrong place — a task in `ideas.md`, an idea in `todo.md` — push back and suggest the right home.

## File formats

**todo.md** — sections `## Now` (max 5), `## Next`, `## Later`, `## Done (recent)`. One line per item:
`- [ ] verb-first task — [work|biz|personal] — (project: name)` (project part optional).
Done items: `- [x] task — [domain] — done YYYY-MM-DD`. If I add something vague, ask one clarifying question or rewrite it into a concrete next action and show me the rewrite.

**ideas.md** — newest at top. Each entry: `### Idea title`, a date, 1–3 lines of description, and optionally `promoted to: [projects/x.md](projects/x.md)`.

**projects/** — frontmatter `domain`, `status` (active | paused | done), `updated`. Body: goal, current state, next action, links to wiki pages and log dates. Filename: `kebab-case.md`. Never delete paused/done projects; filter by status.

**log/** — append-only. Never edit past entries; add a correction as a new entry instead.

**wiki/** — see the wiki rules below. Use `templates/wiki-page.md`.

## Wiki rules

The wiki is about me and my world, built from our conversations and the log — people (boss, cofounder, key customers), tools and systems, how my job works, how my business works, recurring situations, preferences too detailed for `core/me.md`.

- Frontmatter on every page: `updated` (ISO date), `sources` (log dates or `conversation YYYY-MM-DD`).
- Every page is linked from `wiki/index.md` under one section: People, Work, Business, Tools, Patterns, Personal.
- Filenames: `kebab-case.md`, flat in `wiki/` (no subfolders).
- Update pages in place when you learn something new; note the change in today's log.
- Never invent facts. If unsure, ask, or write `TODO: confirm` next to the claim.
- Never delete a page without asking.
- Keep pages short. Past ~80 lines, split into focused pages and link them.
- When two pages, or a page and `core/me.md`, disagree, flag it — don't silently pick one.

## Writing rules

- Concise. No fluff, no preamble, no restating what's already in another file — link to it.
- Todos are verb-first.
- Dates are ISO: `YYYY-MM-DD`.
- Links are standard relative markdown links: `[Name](../wiki/name.md)`. No wikilinks, no Obsidian syntax.
- Never fabricate. Ask when ambiguous.
- Prefer editing an existing file over creating a new one.
- One project per file.
- `core/` stays under ~300 lines total. If it grows, move detail into the wiki and link it.
- Tell me when you write to a file; don't make silent edits.

## Privacy

- All content (`core/`, `projects/`, `log/`, `wiki/`, `todo.md`, `ideas.md`) is gitignored and stays on this machine.
- Only the structure is committed: `AGENTS.md`, `CLAUDE.md`, `README.md`, `.gitignore`, `templates/`, `.gitkeep` files.
- Never `git add -f` content, never `git push` content, never modify `.gitignore` to expose content.
- Never copy personal content into committed files (including templates and this file).
- Before any commit, run `git status` and confirm only structure files are staged.

## Weekly review (on request only)

1. Trim `todo.md` `## Done (recent)` to the last two weeks.
2. Re-sort `## Now` / `## Next` / `## Later`; flag stale items.
3. Review `paused` projects: resume, keep paused, or mark done?
4. Scan `ideas.md`: anything ready to promote to a project?
5. Check wiki pages for contradictions with each other or with `core/me.md`.
6. Rewrite `core/now.md` for the coming week.
7. Log the review in today's log.
