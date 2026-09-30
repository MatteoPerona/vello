# 🧠 vello

*From* cervello *(Italian for brain).* A plain-markdown context harness that gives an AI agent the right context about my work, side business, and personal projects.

🏗️ The **structure** lives in git. 🔒 The **content** (todos, notes, logs, wiki) stays local and is gitignored. No tooling, no scripts, no databases: just 📝 markdown, 🔗 relative links, and 🌱 git.

👉 Start with [AGENTS.md](AGENTS.md); it's the router the agent follows. `CLAUDE.md` just imports it.

## 🗺️ Layout

```
🧭 AGENTS.md    router: what's here, when to read what, how to write back
✅ todo.md      single prioritized todo list          (local only)
💡 ideas.md     index of ideas that aren't tasks      (local only)
🌿 ideas/       one file per fleshed-out idea         (local only)
🎯 core/        me.md + now.md, read every session    (local only)
📁 projects/    one file per project                  (local only)
📓 log/         YYYY-MM-DD.md, append-only            (local only)
📚 wiki/        agent-maintained wiki about my world  (local only)
🧩 templates/   starting shapes for all of the above
```

## 🚀 Set up on a new machine

```sh
git clone <remote> vello && cd vello

cp templates/me.md         core/me.md
cp templates/now.md        core/now.md
cp templates/todo.md       todo.md
cp templates/ideas.md      ideas.md
cp templates/wiki-index.md wiki/index.md
```

🎤 Then start a session from the `vello/` directory and ask the agent to interview you to fill in the seeded files: `core/me.md` first, then `core/now.md`, `todo.md`, and any active projects. For example:

> Interview me to fill in `core/me.md`. Ask one question at a time, then write the file.

⚠️ Don't fill the templates by hand; the interview surfaces the details the agent actually needs.

🔄 Content doesn't sync through git. To move it between machines, copy the folder or use a private sync of your choice.
