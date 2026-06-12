# Making it automatic

The article's "Daily Dover" lands at 4 a.m. without anyone lifting a finger.
Here are the realistic paths to that, from zero-setup to fully wired:

## 1. One tap each morning (works today)

Open this repo in Claude Code (claude.ai/code or the mobile app) and run
`/daily`. ~60 seconds later the briefing is in chat and a ready-to-send draft
is in Gmail. The Gmail and Google Calendar connectors must be enabled for the
session — they already are if you're reading a fresh briefing.

## 2. Scheduled task in Claude Cowork / Claude Code Desktop (recommended)

This is how the original "Daily Dover" runs unattended. Both Claude Cowork
and Claude Code Desktop support scheduled recurring tasks (shipped Feb 2026):

1. On the desktop app, clone this repo locally and open it (Cowork: point a
   session at the folder; Claude Code Desktop: open the repo).
2. Type `/schedule` and create a weekday task for your chosen time with the
   standing instruction: *"Run git pull, then follow .claude/commands/daily.md
   to produce The Jackson Daily."* The `git pull`/`push` steps keep the
   memory files in sync with GitHub.
3. Make sure the Gmail and Google Calendar connectors are enabled for the app.

**The one real caveat:** scheduled tasks only run while the computer is awake
with the app open. If the machine is asleep at 4 AM, the task runs when it
wakes — fine if the laptop opens before coffee, not fine if you want the
briefing on your phone from bed. For a true 4 AM delivery, leave a desktop
awake (or see option 3).

Docs: https://support.claude.com/en/articles/13854387-schedule-recurring-tasks-in-claude-cowork
and https://code.claude.com/docs/en/desktop-scheduled-tasks

## 3. Fully headless via GitHub Actions (most setup, true 4 AM)

A cron workflow can run `claude` (the CLI) on a schedule with
`anthropics/claude-code-action`. The catch: the runner has no Gmail/Calendar
connectors, so you'd need to provide credentials yourself:

- `ANTHROPIC_API_KEY` repo secret
- A Google Cloud service account (or OAuth refresh token) with Calendar
  read + Gmail compose scopes, wired in as an MCP server or small script
- For true *sending* (not drafts), Gmail API `send` scope or an SMTP app
  password

This is a weekend project, not a blocker — the briefing itself works
today via paths 1–2. If you want path 3, ask the chief of staff to build it
and it will scaffold the workflow and walk you through the Google Cloud side.

## A note on sending

By design the assistant only creates **drafts** (operating rule #1 in
CLAUDE.md). If you ever automate actual sending, keep that rule for every
email *except* the briefing itself.
