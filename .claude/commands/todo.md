---
description: Manage the family to-do list (add, complete, review)
---

Manage the family to-do list, which lives in **Todoist** — the "Family To Do"
project (id `6gr7rPCVrMp3QRjM`), shared between John (uid `59404117`) and
Michelle (uid `59404029`). Use the `mcp__Todoist__*` tools. Request: $ARGUMENTS

- **No arguments** → show the open list. Lead with overdue, then items due
  within 7 days, then the rest. Note each task's owner (assignee) and priority.
  Pull with `find-tasks-by-date` (startDate `today`, overdue included) and
  `find-tasks` (projectId `6gr7rPCVrMp3QRjM`) for the backlog.
- **"add ..."** → create it with `add-tasks` in the Family To Do project.
  Infer the owner from context and set `responsibleUser` (John `59404117` or
  Michelle `59404029`; leave unassigned only if truly shared). Set priority by
  urgency: `p1` due/needed within 7 days, `p3` otherwise, `p4` someday/parked.
  Put a due date (`dueString`) when one is implied; put extra detail (phone
  numbers, addresses, "done when…") in the description. Ask only if a due date
  seems implied but unclear.
- **"done ..."** → find the matching task and `complete-tasks` it.
- **"sweep"** → search Gmail for `subject:todo newer_than:7d` from John or
  Michelle, add any items not already in Todoist, then label those threads
  with the `JacksonDaily` label (create it if missing) so they aren't
  re-imported.
- **"review"** → surface stale tasks (no activity in 21+ days, via
  `find-activity`) and ask whether each is still real or should be deleted.

Todoist syncs on its own — no commit/push needed for to-do changes.
(`family/todos.md` is a deprecated archive; don't read or write it.)
