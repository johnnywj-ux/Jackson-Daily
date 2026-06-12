---
description: Generate The Jackson Daily morning briefing and save it as a Gmail draft
---

Build today's edition of **The Jackson Daily**. If an argument like
"tomorrow" or a date is given, build it for that date instead: $ARGUMENTS

Steps:

0. **Import corrections from the last briefing.** Search Gmail for replies to
   the most recent Jackson Daily from John or Michelle:
   `in:inbox newer_than:10d from:(johnnywj@gmail.com OR mgauthreaux91@gmail.com) subject:"Jackson Daily"`.
   If a reply contains corrections, preferences, or new durable facts, apply
   them to the relevant `family/*.md` file and/or `templates/daily-briefing.md`
   and commit BEFORE composing today's edition, then label the thread
   `JacksonDaily` so it isn't imported twice. No reply = skip silently.
1. **Read the knowledge base**: `family/*.md` and `templates/daily-briefing.md`.
2. **Pull the day** (timezone America/New_York) from all calendars listed
   in CLAUDE.md — Family, John's Main, Michelle's, WP Travel, US Holidays,
   and Birthdays (query the Birthdays calendar by ID; it's not in
   list_calendars). Also pull the next 14 days from Family + Main +
   Michelle's + Birthdays for the Heads-up section.
3. **Sweep the inbox — two passes:**
   - *New:* `newer_than:1d in:inbox` (plus `from:procaresoftware.com
     newer_than:1d` for Lucas's daycare summary). Keep only action-needed
     items; ignore marketing and newsletters.
   - *Open loops:* `in:inbox newer_than:21d -category:promotions` — find
     threads where the **last message is from a real person** (vendor, school,
     doctor, family — not a noreply/marketing sender) that asks John or
     Michelle a question or awaits a decision, with no later reply from
     johnnywj@ or mgauthreaux91@. Surface each with its age ("Roy, contract
     terms — waiting 2 days"). Any open loop older than 3 days also gets
     added to Todoist (priority `p1`) so it cannot age out silently.
     **Exception:** skip anything marked Parked (a `p4` task whose description
     says PARKED) in Todoist or marked "Parked" in `family/household.md` — the
     family is deliberately not replying yet. Mention a parked item only
     when its unblock condition appears met.
   Also run the to-do email import (`subject:todo newer_than:2d` from John or
   Michelle → add to the Todoist "Family To Do" project, label thread
   `JacksonDaily`).
3b. **To-dos**: from Todoist (Family To Do, id `6gr7rPCVrMp3QRjM`; use
   `find-tasks-by-date` with startDate `today` and overdue included), pull
   overdue items, items due in ≤3 days, and up to 3 sensible "today" picks
   given the day's shape. Complete anything the calendar/email shows as done.
4. **Get weather** for Winter Park, FL (web search or wttr.in). If
   unavailable, skip the weather line — never invent it.
5. **Check for conflicts**: overlapping events, travel vs. appointments,
   anything in `family/household.md` flagged "raise in every briefing."
6. **Compose** the briefing exactly per the template. Remember the texting
   rules in CLAUDE.md: short, no micromanaging, one affirmation.
7. **Deliver**:
   - Create a Gmail draft — to: johnnywj@gmail.com, cc: mgauthreaux91@gmail.com,
     subject per template. Use a clean HTML body (simple headings, lists; no
     heavy styling) plus a plain-text alternative.
   - Save a markdown copy to `briefings/YYYY-MM-DD.md`, commit, and push.
8. **Report back** in chat with the briefing content and a note that the
   draft is in Gmail ready to send.
