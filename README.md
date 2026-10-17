# preferences-logger

A skill for Claude (and other agents that read Agent Skills) that keeps a living **`PREFERENCES.md`** in your project: every decision and preference you mention while working, written down the moment you make it, with the date.

You say "option A", "no, put it on the right", "always use pnpm", "let's try tabs for every screen". Without a record, the next session asks again or quietly undoes it. With this skill, the assistant:

- **reads** `PREFERENCES.md` before working, and follows it instead of asking again;
- **writes** each new decision in the same turn: one line per decision, grouped by topic, in your own words;
- **edits in place** when you change your mind, keeping a short "Earlier: …" note, and adds a **dated change-log** entry;
- **leaves out** one-off instructions, secrets and personal data.

It isn't tied to any language, framework or kind of project: product decisions, design choices, code conventions, writing style and how you like to work all fit.

## What the file looks like

```markdown
# Acme app — decisions

## Design
- **Sidebar:** compact menu; folders fill the rest and scroll; Settings is an icon in the bottom row (chose A of three options).
- **Theme:** Auto, Light or Dark in Settings; the sidebar stays dark in both. (Earlier: a switch in the sidebar, removed 12 Oct 2026: "looked bad".)

## Workflow
- **Show design options before building anything visual,** as a page of mockups.

## Change log
- 12 Oct 2026 — Theme switch moved to Settings (their words: "the sidebar switch looks bad").
- 17 Oct 2026 — Sidebar: option A (their words: "A").
```

## Install

**Claude Code, as a plugin** (recommended):

```
/plugin marketplace add HusDev/preferences-logger
/plugin install preferences-logger@preferences-logger
```

**Claude Code, by hand:** copy `skills/preferences-logger` into `~/.claude/skills/` (all your projects) or `.claude/skills/` in one project.

**Claude apps (claude.ai, desktop):** zip the `skills/preferences-logger` folder and upload it under Settings › Capabilities › Skills.

**Other agents:** the skill is a plain `SKILL.md` with a template; point your agent at it, or paste its rules into your agent instructions (`AGENTS.md`).

## Tips

- Add one line to your `CLAUDE.md` or `AGENTS.md` so every session starts by reading the file. The skill offers to do this when it creates `PREFERENCES.md`.
- Commit `PREFERENCES.md` with your code. It doubles as a design log for collaborators and reviewers.
- Keep personal data out of it: the skill records the decision, never the private value.

## Origin

Grew out of building an app with Claude over many sessions, where keeping a dated `PREFERENCES.md` turned out to be the single most useful habit: designs stopped regressing, and new sessions picked up exactly where the last one left off.

## License

MIT, see [LICENSE](LICENSE).
