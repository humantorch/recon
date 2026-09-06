# Recon

A [Blackglass](https://blackglass.me) project.

A job search operating system for Claude Code. Assesses roles honestly against your criteria, tracks your pipeline, and drafts your materials.

Built for technical people who are serious about their search and want a system that tells them the truth.

---

## What It Does

- **Assesses roles** against your specific criteria — compensation, location, domain fit, experience match — and gives you a clear go/no-go with reasoning
- **Tracks your pipeline** across flagged, applied, interviewing, and closed stages
- **Drafts application materials** — answers to application questions, cover letters, resume tailoring notes
- **Prepares you for interviews** with role-specific talking points and questions to ask
- **Thinks through decisions** with you when you need a sounding board

## Requirements

- [Claude Code](https://claude.ai/code) — this is a Claude Code workspace, not a standalone app
- [`gh` CLI](https://cli.github.com), authenticated — only if you want the optional GitHub Project board (see below)
- Otherwise, that's it

## Setup

Click **Use this template** above, or:

```sh
gh repo create my-job-search --template humantorch/recon --clone
cd my-job-search
claude  # open Claude Code in this directory
```

This gives you your own independent repo, not a fork, so your profile, salary details, and application history stay in a repo you control with no link back to this one.

Then run:

```
/setup
```

This walks you through filling in your profile and search criteria. Takes about 10 minutes. Do it once.

---

## Commands

| Command | What it does |
|---------|-------------|
| `/setup` | First-run onboarding — fill in your profile and criteria |
| `/assess [url, JD text, or file]` | Evaluate a role for fit. Takes a URL, pasted JD text, or a local file (text or PDF) — keeps the canonical URL where one exists. |
| `/apply [company or role]` | Application assistance for a specific role |
| `/status` | Pipeline overview — what's active, what needs attention |
| `/prep [company or role]` | Interview preparation for a role |
| `/coach [situation]` | Thinking partner for decisions and tricky conversations |

For `/apply` and `/prep`, just type the company name or role title, no need to know the exact filename.

---

## Optional: GitHub Project Board

The markdown files in `roles/` are always the source of truth, but if you want a visual Kanban view of your pipeline, `/setup` can create a GitHub Project board with a status field that mirrors your role files (Flagged → Applied → Screen → Interviewing → Offer / Rejected / Withdrawn). Once it's set up, `/assess` and `/apply` keep it in sync automatically, and status changes that happen in conversation, a rejection email, a recruiter update, get synced too.

Purely optional, skip it during `/setup` and everything works exactly the same, just without the board. Configured in `context/github-project.md`.

---

## How It Works

Everything lives in plain markdown files. Claude Code reads them automatically when you open the workspace. Your profile and search criteria inform every assessment. Your application history is tracked in `context/applications.md`. Job descriptions are archived in `jd-archive/` before postings go dark.

No database. No backend. No account. Just files, Claude, and your job search.

---

## Workspace Structure

```
recon/
├── CLAUDE.md                   # Loaded automatically — the brain of the workspace
├── .claude/commands/           # Slash commands
├── context/                    # Your profile, criteria, application log, optional GitHub Project config
├── resumes/                    # Your resume versions (PDFs not tracked in git)
├── roles/                      # Per-role tracking files (flagged → applied → closed)
├── jd-archive/                 # Raw job descriptions, preserved
├── outputs/                    # Cover letters, application answers, drafts
└── interview-prep/             # Interview notes and prep materials
```

---

## Works Great with Glass

Recon's workspace is already plain markdown, so if you use Obsidian, just open this directory as a vault, no configuration needed. Pair it with [Glass](https://community.obsidian.md/plugins/blackglass) to run Claude Code sessions from inside Obsidian against that same vault — assess a role, take notes, and update your pipeline without switching apps.

---

## A Blackglass Project

Recon is part of [Blackglass](https://blackglass.me) — tools for technical people who think carefully about how they work. If you're an engineering manager rather than a job seeker, check out [Cadence](https://github.com/humantorch/cadence), the same kind of Claude Code workspace built for running an EM practice.
