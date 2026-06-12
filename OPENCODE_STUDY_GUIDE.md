# OpenCode Personal Study Guide

> **Your goal:** Go from zero to confident daily use of [OpenCode](https://opencode.ai) — the open-source AI coding agent.
>
> **How to use this guide:** Work through modules in order. Check off items as you complete them. Fill in the **My Notes** sections — that's what makes this *your* study guide.

---

## What Is OpenCode? (Read This First)

**OpenCode** is an open-source AI coding agent. Unlike a chatbot where you paste code snippets, OpenCode:

- **Reads your real project** — files, imports, tests, config
- **Edits files and runs commands** — tests, linters, builds
- **Works with any LLM** — Claude, GPT, Gemini, local models (Ollama), GitHub Copilot, and more

**Where you can use it:**

| Surface | How to start | Best for |
|---------|--------------|----------|
| Terminal (TUI) | `opencode` | Daily coding in your repo |
| Desktop app | [opencode.ai/download](https://opencode.ai/download) | GUI preference |
| IDE extension | VS Code, Cursor, Zed, Windsurf | Stay in your editor |
| Headless / CI | `opencode run "..."` | Scripts and automation |

**Key mental model:** OpenCode is like a junior developer with terminal access. You direct it; you review every diff.

**Official docs:** [opencode.ai/docs](https://opencode.ai/docs) · **Source:** [github.com/anomalyco/opencode](https://github.com/anomalyco/opencode)

### My Notes — Why I'm Learning OpenCode

```
Date started:
Goal (be specific — e.g. "refactor my side project", "learn AI-assisted dev"):
Current editor/tool I use today:
```

---

## Study Roadmap Overview

| Module | Topic | Time | Outcome |
|--------|-------|------|---------|
| 1 | Install & first session | 1–2 hrs | OpenCode runs; you sent your first prompt |
| 2 | Plan vs Build workflow | 2–3 hrs | You use Tab to plan before editing |
| 3 | Project context (`AGENTS.md`) | 2 hrs | Your project has house rules the agent follows |
| 4 | Prompting & file references | 3 hrs | You reference files with `@` and undo mistakes |
| 5 | Configuration & models | 2–3 hrs | You picked a provider and understand `opencode.json` |
| 6 | Power features | 4+ hrs | Commands, skills, agents, MCP (optional depth) |

**Suggested pace:** 2–3 sessions per week → finish in ~3–4 weeks.

---

## Module 1: Install & First Session

### Learning objectives

- [ ] Install OpenCode on your machine
- [ ] Connect at least one AI provider
- [ ] Start the TUI in a project folder
- [ ] Ask one question about the codebase
- [ ] Understand what Plan and Build modes are (don't need to master yet)

### 1.1 Install

Pick one method:

```bash
# Recommended (macOS/Linux)
curl -fsSL https://opencode.ai/install | bash

# Or via npm
npm install -g opencode-ai

# macOS Homebrew (most up-to-date tap)
brew install anomalyco/tap/opencode
```

**Windows:** WSL is recommended, or use `scoop install opencode` / `choco install opencode`.

Verify:

```bash
opencode --version
```

### 1.2 Connect a provider

**Beginner-friendly option — OpenCode Zen** (curated models, one API key):

1. Run `opencode` in terminal
2. Type `/connect`
3. Choose **OpenCode Zen** → sign in at [opencode.ai/auth](https://opencode.ai/auth)
4. Paste your API key

**Free alternatives:**

- Google Gemini API key (free tier) — good for learning
- GitHub Copilot login (if you have a subscription)
- Local models via Ollama (offline, privacy-first)

### 1.3 First session

```bash
cd /path/to/any/project   # even a small personal repo
opencode
```

Try these prompts (copy one at a time):

1. `What does this project do? Give me a 5-bullet summary.`
2. `What is the tech stack here?`
3. `List the main entry points of this codebase.`

### 1.4 Essential TUI concepts

| Key / Command | What it does |
|---------------|--------------|
| `Tab` | Switch between **plan** (read-only) and **build** (can edit) agents |
| `@filename` | Attach a file to your prompt (fuzzy search with `@`) |
| `/help` | Show available commands |
| `/undo` | Revert the last change OpenCode made |
| `/redo` | Re-apply undone change |
| `ctrl+x` then `?` | Leader key + shortcuts (see docs) |

### Module 1 checkpoint

Answer without looking:

1. What are the three surfaces OpenCode runs on?
2. What does `Tab` switch between?
3. How do you attach a file to a prompt?

### My Notes — Module 1

```
Install method I used:
Provider I connected:
First project I tried:
What surprised me:
What confused me:
```

---

## Module 2: Plan → Build Workflow

### Learning objectives

- [ ] Use **plan** mode to explore without file changes
- [ ] Review a plan, give feedback, then switch to **build**
- [ ] Use `/undo` when the agent did something wrong
- [ ] Practice one small real change (e.g. README, comment, tiny fix)

### 2.1 Why Plan first?

| Mode | Agent | File edits | Best for |
|------|-------|------------|----------|
| **plan** | Analysis | Disabled by default | Understanding code, designing approach |
| **build** | Implementation | Full access | Writing code, running tests |

**Workflow:**

```
1. Press Tab → indicator shows "plan"
2. Ask: "How would you add X to this project?"
3. Read the plan; refine: "Also handle edge case Y"
4. Press Tab → "build"
5. Say: "Go ahead and implement that plan."
6. Review the diff; run tests yourself
```

### 2.2 Hands-on exercise

Pick a **safe, small** task on a non-production project:

**Exercise A — README**
- [ ] Plan: `How would you add a "Contributing" section to README?`
- [ ] Build: `Implement that. Keep it under 10 lines.`
- [ ] Review diff before accepting

**Exercise B — Explain then fix**
- [ ] Plan: `@src/some-file.ts explain what this file does and one improvement`
- [ ] Build: `Make only that one improvement. Don't refactor anything else.`

**Exercise C — Undo practice**
- [ ] Ask build mode to make a change you don't want
- [ ] Run `/undo`
- [ ] Rephrase the prompt and try again

### Module 2 checkpoint

- [ ] I used plan mode at least 3 times before building
- [ ] I used `/undo` at least once
- [ ] I reviewed a diff before keeping changes

### My Notes — Module 2

```
Best plan prompt I wrote:
Mistake I caught with /undo:
Rule I'll follow from now on (e.g. "always plan refactors"):
```

---

## Module 3: Project Context (`AGENTS.md`)

### Learning objectives

- [ ] Run `/init` to generate `AGENTS.md`
- [ ] Customize it with your project's commands and rules
- [ ] Commit it to git
- [ ] See how agent behavior improves with clear instructions

### 3.1 Generate baseline

Inside OpenCode TUI:

```
/init
```

This analyzes your repo and creates `AGENTS.md` at the project root.

### 3.2 What to put in `AGENTS.md`

Use this template and adapt:

```markdown
# AGENTS.md

## Commands
- install: `npm install`
- dev:     `npm run dev`
- test:    `npm test`
- lint:    `npm run lint`

## Conventions
- (your language/framework rules)
- (naming, export style, test patterns)

## Architecture
- (1–3 sentences: what this app does, main folders)

## Don't
- Don't edit `node_modules/` or generated files
- Don't run destructive git commands without asking
- Don't commit secrets or .env files
```

**Tip:** Coming from Claude Code? OpenCode reads `CLAUDE.md` as fallback if no `AGENTS.md` exists.

### 3.3 Hands-on exercise

- [ ] Run `/init` on a real project
- [ ] Add your actual build/test/lint commands
- [ ] Add 3 "Don't" rules specific to your repo
- [ ] Commit `AGENTS.md`
- [ ] Ask: `Run the tests and fix any failures` — notice if it uses your commands

### Module 3 checkpoint

- [ ] My project has a committed `AGENTS.md`
- [ ] I can explain why persistent context beats repeating instructions every session

### My Notes — Module 3

```
Commands I documented:
Rules the agent kept breaking before AGENTS.md:
Rules that fixed the behavior:
```

---

## Module 4: Prompting & File References

### Learning objectives

- [ ] Use `@` to reference specific files
- [ ] Use `!command` to inject shell output into prompts
- [ ] Write prompts like you're talking to a junior dev (specific, scoped)
- [ ] Share a session with `/share` (optional)

### 4.1 Reference syntax

| Syntax | Example | Effect |
|--------|---------|--------|
| `@file` | `Review @src/auth.ts for SQL injection` | Attaches file content |
| `!cmd` | `!git diff` then `Summarize these changes` | Runs shell, injects output |
| Image drop | Drag image into terminal | Visual reference for UI work |

### 4.2 Prompt quality checklist

Good prompts include:

- [ ] **What** to do (verb + outcome)
- [ ] **Where** (`@` files or folders)
- [ ] **Constraints** ("don't change public API", "minimal diff")
- [ ] **How to verify** ("run tests after", "show me the diff first")

**Weak:** `Fix the auth bug`

**Strong:** `In @src/auth/login.ts, users with expired tokens get a 500 instead of 401. Match the error handling in @src/auth/middleware.ts. Run tests after.`

### 4.3 Hands-on exercises

- [ ] **Exercise 1:** Ask about one file using `@` — no paste
- [ ] **Exercise 2:** `!git log -5 --oneline` then ask for a summary
- [ ] **Exercise 3:** Give a multi-file task with explicit "do not touch" boundaries
- [ ] **Exercise 4 (optional):** `/share` a session link and review what's exposed

### Module 4 checkpoint

Write one prompt you could reuse as a template:

```
My reusable prompt template:


```

### My Notes — Module 4

```
Prompts that failed (too vague):
Prompts that worked well:
```

---

## Module 5: Configuration & Models

### Learning objectives

- [ ] Understand global vs project config
- [ ] Set a default model
- [ ] Know how to switch models in TUI (`/models` or `ctrl+x m`)
- [ ] Store API keys safely (env vars, not in git)

### 5.1 Config locations

| File | Scope |
|------|-------|
| `~/.config/opencode/opencode.json` | Global (all projects) |
| `./opencode.json` | Project-specific (overrides global) |

Minimal project example:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "model": "opencode/claude-sonnet-4-6",
  "provider": {
    "opencode": {
      "options": {
        "apiKey": "{env:OPENCODE_API_KEY}"
      }
    }
  }
}
```

Use `{env:VAR_NAME}` for secrets — never commit raw API keys.

### 5.2 Model strategy (beginner)

| Task type | Model tier | Why |
|-----------|------------|-----|
| Exploration, grep, read | Cheaper/faster (Haiku, mini models) | Lots of tokens, low risk |
| Implementation, refactor | Stronger (Sonnet, Opus, GPT-5) | Better tool use and reasoning |
| Plan mode | Can use cheaper model | No edits happening |

### 5.3 Hands-on exercises

- [ ] Run `/models` and switch models once
- [ ] Create `opencode.json` in a test project with your preferred default model
- [ ] Store API key in environment variable, reference with `{env:...}`

### Module 5 checkpoint

- [ ] I know where my global config lives
- [ ] API keys are not in git
- [ ] I have a default model chosen for daily work

### My Notes — Module 5

```
Default model I chose:
Monthly budget concern (if any):
Provider setup notes:
```

---

## Module 6: Power Features (Pick Your Depth)

Complete **6A** if you want daily productivity. Add **6B–6D** based on interest.

### 6A — Slash commands (recommended)

Built-in commands to know:

| Command | Purpose |
|---------|---------|
| `/init` | Generate `AGENTS.md` |
| `/connect` | Add/switch providers |
| `/sessions` | List and resume sessions |
| `/undo` / `/redo` | Change control |
| `/share` | Share session link |
| `/help` | Command reference |

**Custom commands:** Create `.opencode/commands/my-command.md` for reusable prompt templates.

- [ ] Read [Custom Commands docs](https://opencode.ai/docs/commands)
- [ ] Create one custom command for a task you repeat (e.g. `/review`, `/test-fix`)

### 6B — Custom agents

Agents = roles with different permissions/models. Toggle with `Tab` or define in `.opencode/agents/`.

- [ ] Read [Agents docs](https://opencode.ai/docs/agents)
- [ ] Scaffold one: `opencode agent create` (if available in your version)

### 6C — Agent skills

Skills = instructions the model auto-discovers (like Cursor skills). Live in `.opencode/skills/<name>/SKILL.md`.

- [ ] Read [Skills docs](https://opencode.ai/docs/skills)
- [ ] Compare to how you use skills in Cursor (if applicable)

### 6D — MCP servers

MCP connects external tools (Notion, databases, APIs) to the agent via `opencode.json`.

- [ ] Read [MCP docs](https://opencode.ai/docs/mcp)
- [ ] Add one MCP server you already use elsewhere

### 6E — Headless & CI (optional)

```bash
opencode run "summarize open TODOs in this repo"
opencode run --format json "list failing tests" > report.json
opencode serve --port 4096   # headless API
```

- [ ] Run one `opencode run` one-shot command
- [ ] Read [CLI docs](https://opencode.ai/docs/cli)

### My Notes — Module 6

```
Features I use weekly:
Features I'll skip for now:
Custom command/agent I built:
```

---

## Glossary

| Term | Meaning |
|------|---------|
| **TUI** | Terminal User Interface — interactive terminal app |
| **Agent** | A role/profile (plan, build, or custom) with tool permissions |
| **Plan mode** | Read-only analysis; won't edit files by default |
| **Build mode** | Full tool access; makes changes |
| **AGENTS.md** | Project instructions OpenCode reads every session |
| **Zen** | OpenCode's curated model gateway (pay-as-you-go) |
| **MCP** | Model Context Protocol — plug-in external tools |
| **Skill** | Auto-discovered instruction file for specific workflows |
| **LSP** | Language Server Protocol — real-time code intelligence for the LLM |
| **Provider** | LLM backend (Anthropic, OpenAI, Google, Ollama, etc.) |

---

## Weekly Practice Log

Copy this table each week:

| Week | Modules completed | Hours | Best win | Blocker |
|------|-------------------|-------|----------|---------|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |

---

## Final Project — Prove You Know It

Complete this capstone on a real (non-critical) repo:

1. [ ] Install OpenCode and connect a provider
2. [ ] Run `/init` and customize `AGENTS.md`
3. [ ] Use **plan** mode to design a small feature or fix
4. [ ] Switch to **build** and implement it
5. [ ] Use `@` to reference at least 2 files in prompts
6. [ ] Run tests (yourself or via agent) and verify
7. [ ] Use `/undo` or reject at least one bad change
8. [ ] Write a 5-sentence retrospective in **My Notes** below

### Capstone retrospective

```
What I built/fixed:
What I would do differently:
Am I ready to use OpenCode on work projects? Why or why not:
Next skill I want to learn (MCP, custom agents, CI, etc.):
```

---

## Reference Links

| Resource | URL |
|----------|-----|
| Official docs | https://opencode.ai/docs |
| Install | https://opencode.ai/install |
| Zen models & pricing | https://opencode.ai/docs/zen |
| GitHub repo | https://github.com/anomalyco/opencode |
| Community mega-guide | https://github.com/wesammustafa/OpenCode-Everything-You-Need-to-Know |
| Real Python tutorial | https://realpython.com/opencode-guide/ |
| Privacy | https://opencode.ai/docs/privacy |

---

## Quick Start (If You Only Have 30 Minutes Today)

1. Install: `curl -fsSL https://opencode.ai/install | bash`
2. `cd` into any project → run `opencode`
3. `/connect` → set up Zen or Gemini
4. Ask: `Explain this project in 5 bullets`
5. `Tab` → plan mode → ask how you'd improve one file
6. `Tab` → build → ask for one small safe change
7. Check off Module 1 in this guide

**You're studying. Start small, review every diff, and fill in the notes as you go.**
