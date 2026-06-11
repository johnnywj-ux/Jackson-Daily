# Making it automatic

The article's "Daily Dover" lands at 4 a.m. without anyone lifting a finger.
Here are the realistic paths to that, from zero-setup to fully wired:

## 1. One tap each morning (works today)

Open this repo in Claude Code (claude.ai/code or the mobile app) and run
`/daily`. ~60 seconds later the briefing is in chat and a ready-to-send draft
is in Gmail. The Gmail and Google Calendar connectors must be enabled for the
session — they already are if you're reading a fresh briefing.

## 2. Scheduled cloud session (recommended next step)

Claude Code on the web supports re-running a session against this repo.
Set a phone reminder/shortcut for 6 AM that deep-links to claude.ai/code with
this repo and the prompt `/daily` — effectively one-tap-zero-thought.
If/when Anthropic ships native scheduled tasks for Claude Code on the web,
point the schedule at `/daily` and delete this section.

## 3. Fully headless via GitHub Actions (most setup)

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
