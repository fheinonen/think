# Think

`think` helps you get messy thoughts out of your head and into a useful shape.

It is for the moment when you have too many threads open at once, you do not
want to structure them yet, and you need the AI to turn the dump into something
you can work with.

## Install

```bash
npx skills add fheinonen/think
```

## First Use

Invoke `/think`.

Then do the simplest possible thing: dump the problem in one go.

You do not need neat bullets. You do not need a plan. Fragments are fine.
This works especially well with speech-to-text, whether that is your OS dictation,
Wispr Flow, or a local speech-to-text model setup such as Handy for macOS.

Example:

```text
/think

I need to migrate a client system next month. The database sync might be the
real bottleneck. We only have a 4 hour maintenance window. I am worried about
rollback if DNS cutover fails. Running both environments in parallel could get
expensive. I also do not know who owns the final go/no-go call.
```

The skill will turn that into a breakdown with:

- A clear problem statement
- Distinct threads
- Open questions you have not resolved yet
- Action items you can actually do next

## What The Workflow Feels Like

1. You dump everything on your mind.
2. `think` organizes it into a structured breakdown.
3. You add more thoughts, ask to go deeper on one thread, or reframe it.
4. When it looks right, you save the session.

Sessions are stored as markdown files in `~/.thinking-sessions/`.

## Common Prompts

- Start a session: "I need to think through something"
- Continue dumping: add more thoughts after the first breakdown
- Go deeper: "Expand thread 2"
- Reframe: "Give me a different framing"
- Save: "save"
- List sessions: "List my thinking sessions"
- Resume: "Continue the migration session"
- Finish: "Mark the migration session as done"

## What This Is Good For

- Untangling a complex decision
- Breaking down a problem with too many moving parts
- Capturing thoughts before they disappear
- Turning vague concern into concrete next steps

## License

MIT
