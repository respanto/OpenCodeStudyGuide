# My OpenCode Study Notes

Personal workspace for learning [OpenCode](https://opencode.ai). Pair this folder with the main guide: [`../OPENCODE_STUDY_GUIDE.md`](../OPENCODE_STUDY_GUIDE.md).

---

## Quick start

1. Read Module 1 in the study guide
2. Create `session-log.md` (template below)
3. Log every study session — even 15 minutes counts
4. Copy prompts that work into `prompts-that-work.md`

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

## Recommended files in this folder

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

### `session-log.md`

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

### `prompts-that-work.md`

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

### `mistakes.md`

```markdown
# Mistakes & Lessons

## YYYY-MM-DD — Agent edited wrong file

**What I asked:**
**What it did instead:**
**What I should have said:**
**Lesson:**
```

### `config-snippets.md`

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

- [ ] Logged the session in `session-log.md`
- [ ] Saved any good prompts to `prompts-that-work.md`
- [ ] Checked off items in the study guide
- [ ] Reviewed diffs before keeping agent changes
- [ ] Ran tests if the agent edited code

---

## Useful links

| Resource | URL |
|----------|-----|
| Study guide (this repo) | [`OPENCODE_STUDY_GUIDE.md`](../OPENCODE_STUDY_GUIDE.md) |
| Official docs | https://opencode.ai/docs |
| Install | https://opencode.ai/install |
| GitHub repo | https://github.com/anomalyco/opencode |

---

## Repo

Published at: https://github.com/respanto/OpenCodeStudyGuide
