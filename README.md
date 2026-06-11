# The Jackson Daily 📰

A family "chief of staff" for the Jackson household, built with Claude Code.

Inspired by the Ford exec who built "Claudette" — an assistant that sends her
family a morning briefing (the "Daily Dover") covering school schedules,
childcare, appointments, birthdays, and trash day, plus pre-drafted reminder
texts for her husband and au pair.

This repo is the Jackson family version. Open it in Claude Code (web, mobile,
or CLI) with the Gmail and Google Calendar connectors enabled, and Claude
becomes the household chief of staff.

## How to use it

| Command | What it does |
|---|---|
| `/daily` | Builds **The Jackson Daily** — today's briefing — and saves it as a Gmail draft to John & Michelle |
| `/weekly` | Sunday-evening week-ahead preview: every commitment for the next 7 days, conflicts flagged |

You can also just talk to it: *"What's on for Lucas this weekend?"*,
*"Add Emma's follow-up to the Family calendar"*, *"Anything in my inbox I need
to act on before Friday?"*

## What the daily briefing covers

- Today's events from the **Family** calendar, John's **Main Calendar**, and the **WP Travel Schedule**
- Kid logistics: Lucas's preschool (Loving Earth), soccer, Goldfish swim, water days; Emma's appointments
- Houseguests and family travel
- Household ops: service appointments, road-repaving parking rules, recurring chores
- Heads-up section: birthdays and important dates in the next 14 days
- An inbox sweep: action-needed emails from the last 24 hours
- Two pre-drafted texts (one for Michy, one for whoever needs the day's logistics), each with a little affirmation — per the original article's best feature

## Repo layout

```
CLAUDE.md                  # The chief-of-staff persona + operating instructions
family/profile.md          # Who's who (people, contacts, address)
family/routines.md         # Recurring weekly schedule
family/important-dates.md  # Birthdays, anniversaries, recurring reminders
family/household.md        # Home, vendors, services, ongoing projects
templates/daily-briefing.md# The Jackson Daily format
briefings/                 # Archive of generated briefings
.claude/commands/          # /daily and /weekly
docs/automation.md         # Options for making this fully automatic
```

## Keeping it smart

The `family/` files are the assistant's memory. When life changes — new
activity, new sitter, school year schedule — edit the files (or just tell
Claude to update them). Everything inferred from calendars/email on first
setup is marked with `(confirm)` so you can correct it.
