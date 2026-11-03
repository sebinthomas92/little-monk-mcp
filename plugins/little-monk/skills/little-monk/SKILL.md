---
name: little-monk
description: Use when the person asks about their plan, tasks, deep work, focus sessions, notes, quotes, highlights or ideas in Little Monk, or asks to add, move, complete or delete them.
---

# Little Monk

Little Monk is the person's daily planner. The `little-monk` MCP server reads and changes their own library; everything you save reaches their iPhone, iPad and Mac at the next sync.

## Words

- **Task**: something the person intends to do. A *quick task* has its own time and length on the timeline. A task without a time waits in **Unscheduled**.
- **Deep work** (a **session**): one reserved attempt at a task, with a time, a length and an optional intention. A task can have several attempts. Planning a session is a plan, not a record that work happened.
- **Done**: only the person decides a task is done. Ending a session never completes its task.
- **Captures**: Notes, Quotes, Highlights, Links and Ideas. An **Idea** can be built from other captures; their words are copied into it as evidence.

## How to work

1. Start with `get_overview` for "what's on today" questions, or `find_tasks` / `find_captures` / `search` to find items. Use ids from those results; never invent ids.
2. Times are resolved in the person's time zone and echoed back. Confirm the resolved time in your reply ("Saved for Tue 3 Nov, 09:00–09:30").
3. Batch: add or update several tasks in one `add_tasks` / `update_tasks` call. Pass an `idempotency_key` to `add_tasks`, `plan_deep_work` and `add_captures`, and reuse it if you retry.
4. Overlapping plans are allowed; mention overlaps the tool reports, don't refuse them.
5. Mark tasks done with `complete_tasks` only when the person says so.
6. `delete_items` is permanent on every device. A session with recorded time or a review needs `confirm_history_loss: true`; ask the person first and say what will be lost.
7. When a tool refuses (a running session, recorded history, no Pro), pass its message on; it says what to do.
8. Say "saved to your Little Monk library", not "synced": devices apply changes when they next sync.
