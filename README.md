# Agentic Hack Rome: Hacker Manual

**April 11, 2026 | Urbe Hub, Rome**

50 builders. 5 hours. AI agents for Rome.

---

## Two layers, one manual

This hackathon is about building with AI agents. So the manual itself is built for AI agents.

**Human layer:** Visit the website at **https://agentic-hack-rome.vercel.app** for the full visual guide: schedule, tracks, rules, prizes, logistics.

**Agent layer:** Drop `CLAUDE.md` (or `.cursorrules`) into your project root and your AI coding assistant becomes your hackathon teammate. It knows the tracks, the rules, the APIs, the judging criteria, and how to help you prepare your submission.

---

## Quick setup

### Claude Code

```bash
cp CLAUDE.md your-project/CLAUDE.md
```

### Cursor

```bash
cp .cursorrules your-project/.cursorrules
```

### Windsurf, Copilot, and others

`CLAUDE.md` is plain markdown. Any AI tool that reads a context file from your project root will work. Point it to `CLAUDE.md`.

---

## What your AI can do once loaded

- Help you understand the tracks and brainstorm a project direction
- Suggest specific APIs and datasets for your idea
- Check your project against the judging criteria before you pitch
- Fill out the submission template from your project description

Try these prompts:
- "What track fits my skills? I'm good at [backend/LLM/data/mobile]"
- "Help me brainstorm a project for the Muoviti track"
- "Check my project against the judging criteria"
- "Help me prepare the submission"

---

## Files in this repo

| File | What it is |
|------|-----------|
| `CLAUDE.md` | Agent-readable hacker manual (Claude Code, Windsurf) |
| `.cursorrules` | Same content, for Cursor users |
| `index.html` | Visual website version of the manual |
| `agentic-hack-submit.md` | Submission assistant: drop into your project, tell your AI "help me prepare the submission" |
| `README.md` | This file |

---

## Deployments

| What | URL |
|------|-----|
| Website (Vercel) | https://agentic-hack-rome.vercel.app |
| GitHub repo | https://github.com/WERsrl/agentic-hack-rome |

---

Built by [Urbe Hub](https://urbe.build) for Agentic Hack Rome 2026.
