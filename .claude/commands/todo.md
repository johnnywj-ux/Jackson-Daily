---
description: Manage the family to-do list (add, complete, review)
---

Manage `family/todos.md`. Request: $ARGUMENTS

- **No arguments** → show the list, grouped as in the file, with ages
  ("added 12 days ago") and anything overdue flagged first.
- **"add ..."** → file it in the right section (🔥 if due/needed within 7
  days, 📋 otherwise, 🌴 if explicitly someday). Infer *who* from context;
  default to *John/Michy* (shared). Ask only if a due date seems implied but
  unclear.
- **"done ..."** → move the matching item to ✅ Done with completion date.
- **"sweep"** → search Gmail for `subject:todo newer_than:7d` from John or
  Michelle, add any items not already on the list, then label those threads
  with the `JacksonDaily` label (create it if missing) so they aren't
  re-imported.

Always: prune Done items older than 30 days, commit with a short message,
and push (to main, so the file is current on GitHub mobile).
