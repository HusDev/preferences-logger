---
name: preferences-logger
description: Keeps a living PREFERENCES.md in the project that records every decision and preference the user states while working (product, design, technical, workflow, writing), with dates, so later sessions follow them instead of asking again. Use at the start of work in a project that has a PREFERENCES.md (read it first), and whenever the user makes, changes or reverses a decision, picks one of several options, corrects how something was done, or says things like "I prefer", "from now on", "always", "never", "let's go with", "no, do it like this", "remember that".
---

# Preferences logger

People make dozens of small decisions while working with an assistant: a colour, a library, a naming rule, "don't do X", "option B". Most are never written down, so the next session asks again or quietly undoes them. This skill keeps one file, `PREFERENCES.md`, that records each decision the moment it is made, so it holds across sessions, tools and collaborators.

## When to act

**Read** `PREFERENCES.md` before your first change in a project that has one, and again before you propose designs, options or anything the file may already have settled. Follow what it says. Don't ask again about something it records unless the user brings it up.

**Write** to it in the same turn as the work whenever the user:

- states a preference or rule ("I prefer tabs", "always use British spelling", "never commit to main");
- chooses between options you offered ("A", "go with the second one", "mix A and C");
- corrects or rejects how something was done ("this looks bad", "no, put it on the right", "that's wrong, only when…"), as long as the correction says how it should be;
- changes or reverses an earlier decision;
- tries something tentatively ("let's try this"): record it marked as a trial.

**Don't record:**

- one-off instructions that only apply to the current task ("rename this variable");
- facts the code or history already holds (file layout, which library is installed);
- secrets, credentials, tokens, or personal data about anyone (addresses, ID numbers, health). Record the decision, not the private value: "use the user's real name in the footer", never the name itself if it is sensitive;
- your own suggestions the user hasn't accepted.

If you are unsure whether something is a lasting decision, record it: a short extra line costs less than a forgotten choice.

## Where the file lives

`PREFERENCES.md` at the root of the project, unless the project's agent instructions (`CLAUDE.md`, `AGENTS.md`, or similar) name another path. Without a project (a one-off chat), don't create a file; just follow what the user says.

If there is no file yet, create it from `templates/PREFERENCES.md` (next to this file) with the first decision. Then, if the project has a `CLAUDE.md` or `AGENTS.md`, add one line near the top so every future session reads it:

> Read `PREFERENCES.md` first and keep it updated: whenever a decision is made or changed, edit its line and add a dated change-log entry, in the same turn.

## The format

```markdown
# <Project> — decisions

One line on what this file is.

## <Topic>
- **<Short name of the decision>:** what was decided, in plain words. Why, when the user said why. (Earlier: what it replaced, and when.)

## Change log
- 17 Oct 2026 — <what was decided or changed, in one line> (their words: "…").
```

Rules that keep it useful:

1. **One line per decision, grouped by topic.** Pick topics that fit the project (Product, Design, Stack, Workflow, Writing, …). Start with few and add one when a decision fits none of them.
2. **Edit in place.** When a decision changes, rewrite its line to say what holds now, and keep the old choice in a short "Earlier: …" note. Never leave two lines that disagree.
3. **Add a change-log entry for every change,** newest at the bottom, with an absolute date ("17 Oct 2026", never "today" or "yesterday"). Convert relative dates when you write them.
4. **Keep the user's own words** for the important part, quoted and short: they settle what was meant later. Don't put words in their mouth or make a remark sound stronger than it was.
5. **Say why** when the user gave a reason. A reason lets a later session handle a case the rule didn't foresee.
6. **Link what the decision points at:** a design, an issue, a mockup, a commit.
7. **Mark trials and unknowns:** "(trying this)", "(not final)". Remove the mark when it's confirmed.
8. **Write plainly.** Short sentences, no jargon the user didn't use. Use the person's name or "they" unless they have said which pronouns to use; don't guess from a name.

## When a request conflicts with the file

The newest explicit statement wins. If the user now asks for something the file rules out, do what they ask and update the line and the change log. If it's ambiguous whether they meant to change the rule, ask in one short question, quoting the recorded line.

## Tell the user briefly

After you update the file, mention it in one short clause at the end of your reply ("I recorded this in PREFERENCES.md"), not a summary of the file. Show the full file only when asked.

## Example

The user is choosing between three sidebar designs you showed and answers "A, but the buttons should be icons". In the same turn as building it:

```markdown
## Design
- **Sidebar:** compact menu; the folder list fills the remaining height and scrolls; Settings and the privacy switch are icon buttons in one bottom row (chose A from the three options, with icon buttons).

## Change log
- 17 Oct 2026 — Sidebar: option A, with the bottom actions as icon buttons (their words: "A, but the buttons should be icons").
```

A week later the user says "put the labels back on those buttons":

```markdown
- **Sidebar:** … Settings and the privacy switch are buttons with labels in one bottom row. (Earlier: icon-only, 17 Oct 2026.)

- 24 Oct 2026 — Sidebar bottom buttons get their labels back (their words: "put the labels back on those buttons").
```
