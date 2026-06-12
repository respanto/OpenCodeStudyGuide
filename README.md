# OpenCode Study Guide

A personal, structured curriculum for learning [OpenCode](https://opencode.ai) — the open-source AI coding agent.

**Start here:** [`OPENCODE_STUDY_GUIDE.md`](OPENCODE_STUDY_GUIDE.md)

---

## What's in this repo

| Path | Description |
|------|-------------|
| [`OPENCODE_STUDY_GUIDE.md`](OPENCODE_STUDY_GUIDE.md) | Full study guide — 6 modules, exercises, checkpoints |
| [`my-notes/`](my-notes/) | Your personal notes folder (create files as you learn) |

---

## Quick start

1. Read Module 1 in [`OPENCODE_STUDY_GUIDE.md`](OPENCODE_STUDY_GUIDE.md)
2. Install OpenCode: `curl -fsSL https://opencode.ai/install | bash`
3. Create `my-notes/session-log.md` (template below)
4. Log every study session — even 15 minutes counts

---

## My learning profile

| Field | Your answer |
|-------|-------------|
| **Date started** | |
| **Goal** | |
| **Current tools** | (e.g. Cursor, VS Code, terminal) |
| **Provider I use** | (e.g. OpenCode Zen, Gemini, Copilot) |
| **Default model** | |
| **Target finish date** | |

---

## Progress tracker

| Module | Topic | Status | Date completed |
|--------|-------|--------|----------------|
| 1 | Install & first session | ⬜ | |
| 2 | Plan vs Build workflow | ⬜ | |
| 3 | Project context (`AGENTS.md`) | ⬜ | |
| 4 | Prompting & file references | ⬜ | |
| 5 | Configuration & models | ⬜ | |
| 6 | Power features | ⬜ | |

Status key: ⬜ not started · 🟡 in progress · ✅ done

---

## Recommended files in `my-notes/`

| File | Purpose |
|------|---------|
| `session-log.md` | Daily log — what you tried, results, time spent |
| `prompts-that-work.md` | Reusable prompts that gave good results |
| `mistakes.md` | Agent errors you caught — learn from them |
| `config-snippets.md` | Your `opencode.json`, `AGENTS.md`, MCP configs |
| `questions.md` | Things you don't understand yet — research later |

Create files as you need them. Don't over-plan.

---

## Templates

### `my-notes/session-log.md`

```markdown
# Session Log

## YYYY-MM-DD — Module X

**Time spent:** 45 min
**Project used:** /path/to/project
**Mode:** plan / build

### What I did
-

### What worked
-

### What failed / confused me
-

### Next time
-
```

### `my-notes/prompts-that-work.md`

```markdown
# Prompts That Work

## Explain a file
Review @src/path/to/file.ts and explain:
1. What it does
2. Main dependencies
3. One improvement (don't implement)

## Plan then build
[plan mode] How would you add <feature>? List files to change.
[build mode] Implement step 1 only. Run tests after.

## Safe refactor
In @src/foo.ts, refactor only the `bar()` function.
Don't change exports or other files. Minimal diff.
```

### `my-notes/mistakes.md`

```markdown
# Mistakes & Lessons

## YYYY-MM-DD — Agent edited wrong file

**What I asked:**
**What it did instead:**
**What I should have said:**
**Lesson:**
```

### `my-notes/config-snippets.md`

```markdown
# Config Snippets

## opencode.json (project)
(paste your config here — use {env:VAR} for secrets, never raw keys)

## AGENTS.md highlights
(paste rules that actually changed agent behavior)
```

---

## Session checklist

Before ending a study session:

- [ ] Logged the session in `my-notes/session-log.md`
- [ ] Saved any good prompts to `my-notes/prompts-that-work.md`
- [ ] Checked off items in the study guide
- [ ] Reviewed diffs before keeping agent changes
- [ ] Ran tests if the agent edited code

---

## Useful links

| Resource | URL |
|----------|-----|
| Study guide | [`OPENCODE_STUDY_GUIDE.md`](OPENCODE_STUDY_GUIDE.md) |
| Official docs | https://opencode.ai/docs |
| Install | https://opencode.ai/install |
| OpenCode source | https://github.com/anomalyco/opencode |
