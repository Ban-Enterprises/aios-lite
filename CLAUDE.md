# CLAUDE.md — AIOS Lite

> This file is automatically loaded by Claude Code. It's your AI instruction manual.

---

## What is this

This is **AIOS Lite** — your personal AI system. Claude Code acts as your assistant who knows your projects, remembers context between sessions, and helps you work faster.

**You don't need to be a programmer.** Just describe what you need — Claude will handle it.

---

## How it works

Claude reads files in this folder and based on that knows:
- Who you are and what you do
- What you're currently working on
- What was done recently

This means you don't have to re-explain context from scratch every time.

---

## Three rules

1. **Just Ask** — Describe what you need in plain language. Claude does the rest.
2. **Talk, Don't Type** — Hold FN and speak. Claude converts to text. 3x faster than typing.
3. **One step at a time** — Don't try everything at once. One thing at a time.

---

## Commands

Type in chat to run:

| Command | What it does |
|---------|-------------|
| `/install-aios` | **Start here.** Step-by-step setup. |
| `/prime` | Start a session — Claude gets up to speed on your context. |
| `/status` | Quick overview — what's happening, what's next. |
| `/brainstorm [topic]` | Think through any topic strategically. |
| `/plan [what you want to do]` | Make a plan before you start building. |
| `/research [topic]` | Search for information online. |
| `/commit` | Save changes to git (local only). |
| `/end-session` | Close session and save state. |

---

## Context — Your knowledge for Claude

Files in `.context/` are Claude's memory about you and your projects:

| File | What it contains |
|------|-----------------|
| `ROOT.md` | Who you are, what you do, priorities |
| `SESSION-STATE.md` | What happened recently, what's next |
| `domains/projects.md` | Your projects and activities |
| `domains/tools.md` | Tools and platforms you use |
| `CHANGELOG.md` | Change history |
| `DECISIONS.md` | Important decisions |

---

## Rules for Claude

- Write naturally and directly — not like a robot
- Don't do anything that wasn't asked for
- Ask if something is unclear
- At the start of each session, read ROOT.md + SESSION-STATE.md

---

## Folder structure

```
.
├── CLAUDE.md           # This file — instruction manual
├── .context/           # Memory about you and projects
│   ├── ROOT.md
│   ├── SESSION-STATE.md
│   ├── domains/
│   ├── CHANGELOG.md
│   └── DECISIONS.md
├── .claude/commands/   # Commands (slash commands)
├── outputs/            # Brainstorm and research results
├── plans/              # Plans for execution
└── docs/               # Documentation
```

---

## Session Workflow

1. Launch Claude Code
2. `/prime` — Claude gets oriented
3. Work — ask, plan, build
4. `/commit` — save changes
5. `/end-session` — close session
