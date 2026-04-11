---
name: think
description: >
  Organize complex, multi-threaded thinking. Dump raw thoughts fast,
  then get an AI-structured breakdown with threads, open questions,
  and action items. Use when asked to "think through something",
  "organize my thoughts", "brain dump", or "I need to work through a problem".
metadata:
  author: felix
  version: "0.1.0"
---

# Think — Thought Organizer

Help the user organize complex thinking by separating capture from structure.
The user dumps raw thoughts fast. You organize them into a structured breakdown.
Sessions are saved as portable markdown files in `~/.thinking-sessions/`.

## Modes

Determine the mode from the user's request. If unclear, default to **New Session**.

### New Session

The user wants to think through something new.

**Step 1 — Capture.**
Ask the user:

> What are you thinking through? Dump everything in one go.
> Fragments, sentences, bullet points, whatever comes to mind.

Collect the user's full response. Do not interrupt, ask clarifying questions,
or organize anything yet. This is their space.

If the response is empty or very short (under ~20 words),
ask again: "I didn't get enough to work with. Try dumping your thoughts again."

**Step 2 — Organize.**
Read all the captured thoughts and produce a **Breakdown**:

- **Problem** — one-sentence framing of what the user is thinking through
- **Threads** — numbered list of distinct threads. Each thread gets a bold title
  and a 1-2 sentence description. Group related thoughts into the same thread.
- **Open Questions** — gaps you spotted, things the user hasn't addressed,
  considerations worth raising. These are things the AI identifies, not just
  questions the user explicitly asked.
- **Action Items** — concrete next steps extracted from the thinking. Format as
  a checkbox list (`- [ ] ...`).

Present the Breakdown inline.

**Step 3 — Generate metadata.**
From the content, generate:
- **Title:** a short descriptive title for the session (used in frontmatter and filename)
- **Slug:** 3-5 words, lowercase, hyphenated, derived from the problem statement
- **Tags:** 2-5 lowercase hyphenated tags from the domain, client/project context, and topic

**Step 4 — Refine.**
After presenting the Breakdown, ask:

> Want to refine? You can:
> - Add more thoughts
> - Ask me to dig deeper on a specific thread
> - Request a different framing
> - Say "save" to finalize

If the user adds more thoughts: append them to the Raw Thoughts section,
re-generate the full Breakdown, and present the updated version.

If the user asks to expand a thread: elaborate on that thread with more detail,
implications, and questions. Replace the thread's 1-2 sentence description in
the Breakdown with the expanded version (persistent, not ephemeral).

If the user says "save" or "done": proceed to Step 5.

Repeat Step 4 until the user says save or done.

**Step 5 — Save.**
Ensure the directory `~/.thinking-sessions/` exists (create it if not).

Write the session file to `~/.thinking-sessions/YYYY-MM-DD-<slug>.md` where
YYYY-MM-DD is today's date and `<slug>` is from Step 3. If a file with that
name already exists, append `-2` (or `-3`, etc.) to the slug to avoid collision.

The file format:

```
---
title: "<title from Step 3>"
created: <current ISO 8601 timestamp>
updated: <current ISO 8601 timestamp>
status: active
tags: [cloud-migration, rollback, infrastructure]
---

## Raw Thoughts

<each thought as a bullet point, preserving the user's original wording>

## Breakdown

### Problem
<problem statement>

### Threads
<numbered thread list>

### Open Questions
<bullet list>

### Action Items
<checkbox list>
```

Tell the user: "Session saved to `~/.thinking-sessions/<filename>`."

### List Sessions

The user wants to see their past thinking sessions.

List all `.md` files in `~/.thinking-sessions/`. For each file, read the YAML
frontmatter. Only include files that have both `title` and `status` fields
(skip non-session files).

Sort by filename (newest first). Show max 20 entries.

Output format, one line per session:
```
YYYY-MM-DD  [status]  title
```

Example:
```
2026-04-11  active    Cloud migration rollback strategy
2026-04-10  resolved  Auth system redesign
2026-04-09  active    Client X onboarding flow
```

If the directory doesn't exist or is empty, say:
"No thinking sessions yet. Start one by saying 'I need to think through something.'"

### Continue Session

The user wants to continue an existing session.

Find the session file matching the user's description. Search filenames in
`~/.thinking-sessions/` for a partial match on the slug.

- If exactly one file matches: load it.
- If multiple files match: list them and ask the user to pick.
- If no files match: say "No session found matching that. Run 'list sessions' to see available sessions."

Once loaded:
1. Read the file and present the existing Breakdown to the user.
2. Enter the Capture phase (Step 1 from New Session): ask for more thoughts.
3. Append new thoughts to the Raw Thoughts section.
4. Re-generate the full Breakdown incorporating all thoughts (old and new).
5. Enter the Refine phase (Step 4 from New Session).
6. On save: overwrite the file with updated content. Update the `updated`
   timestamp in frontmatter.

### Resolve Session

The user wants to mark a session as done.

Find the session file (same matching logic as Continue Session).

Once found:
1. If the session is already `status: resolved`, tell the user it's already resolved and take no action.
2. Update the frontmatter: set `status: resolved` and add `resolved: <current ISO 8601 timestamp>`.
3. Update the `updated` timestamp.
4. Save the file.
5. Tell the user: "Session '<title>' marked as resolved."
