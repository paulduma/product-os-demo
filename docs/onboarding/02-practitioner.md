# Level 2 — Practitioner

**Goal:** bring it into your real work.

*Roadmap: Level 2/5 · Previous → Level 1 — Explorer · Next → Level 3 — Shipper*

---

## What's different at this level

Level 1 happened inside your AI app, on a throwaway topic — no real folder, no real stakes. Level 2 moves to your **terminal-based coding assistant** (Claude Code or equivalent), which changes one thing that matters a lot: it reads whatever folder you launch it from, plus anything else you explicitly attach. That's what lets a skill act on real files — a real codebase, a real set of drafts — instead of just answering in a chat window.

This is also the first level with real stakes: real code, real constraints, no more sandbox.

## What you'll need

- The skill you built in Level 1 (or a new one) — same file, no changes needed to run it here.
- A terminal-based AI coding assistant installed.
- 20–30 minutes, and a real (but low-risk) topic: something you actually want, but wouldn't be upset about redoing.

---

## Step 1 — Set up your working folder(s)

Before you run anything, decide how much of your real work this skill should be able to see. Two cases — pick the one that's actually you:

### Case A — You don't touch the codebase (specs, protos, benchmarks only)

```
workspace/
├── skills-repo/      (optional — only needed for extras beyond the skill file itself: templates, reference docs, examples)
├── project-a/          (one deliverable — a spec, a proto)
└── project-b/          (a second, kept separate on purpose)
```

Each initiative gets its own folder. You never point the assistant at a real codebase — there's nothing there for you to accidentally touch, and nothing for the assistant to wander into. Add as many project folders as you have initiatives; two are shown here just as an example.

### Case B — You touch the codebase (skills read or act on real code)

```
workspace/
├── skills-repo/      (optional)
└── codebase/           (the real repo — skills point straight at it)
```

No separate project folder: your output lives alongside or inside the codebase itself, and any skill that grounds itself in real code (e.g. a spec that checks existing behavior before proposing a change) reads it directly.

**`skills-repo/` in both cases is optional** — cloning it locally only buys you the extras that don't fit in a single skill file (templates, shared reference material, examples). If all you need is the skill itself, you already have it from Level 1; skip this folder entirely.

**Not sure which case you are?** Default to Case A. It's the safer setup, and nothing stops you from adding a codebase folder later once you actually need one.

## Step 2 — Point your assistant at the right folder(s)

Launch your terminal assistant from the folder that matters most for this task (your project, or your codebase). If you need a second folder attached at the same time — say, `skills-repo` alongside `codebase` — most tools support attaching extra folders at launch, commonly with a flag like `--add-dir <path>`.

If you find yourself typing the same combination of folders every time, save it as a shortcut (a shell alias, or your tool's equivalent) instead of retyping it — a one-time setup that saves you from repeating it.

## Step 3 — Call the skill

Same as Level 1: invoke it the same way you did there (as a slash command if it's set up as one, or by pointing your assistant at the file). The only difference now is what it can see — real files instead of nothing.

## Step 4 — Run it on something real

Pick a real problem, low enough stakes that redoing it costs you nothing. Run the skill on it. This time, don't fake the details — the point is to see what the skill does with your actual constraints, not a made-up scenario.

## Step 5 — Know how to refresh

If you edit the skill file while a session is already running, the change usually won't apply until you start a new session — close and reopen rather than assuming it picked up your edit live. If your skill library comes from a shared repo, pull its latest version occasionally so you're not working off a stale copy; if it's installed through your tool's plugin system, check for a reload/sync command (most terminal assistants have one).

---

## What "good" looks like

A spec or benchmark you produce here should hold the same structure and level of detail as the one you produced in Level 1 — just now about something you actually care about shipping, not a throwaway topic.

## Common snags

- **The assistant can't see the folder you meant.** Check you launched from the right folder, or that you attached the extra one — it only sees what you point it at.
- **Your edit to the skill doesn't seem to apply.** Start a fresh session rather than assuming a running one picked it up.
- **You're not sure if you're Case A or B.** Default to Case A — you can always add a codebase folder later.

## You're done with this level when

- [ ] A skill has produced something — a spec, a benchmark — about a real problem you have.
- [ ] You'd be willing to show the output to a colleague.
- [ ] You know which of the two folder setups is yours, and why.

*Roadmap: Level 2/5 · Previous → Level 1 — Explorer · Next → Level 3 — Shipper*

--- OLD
# Level 2 — Practitioner

**Goal: bring it into your real work.**

> Roadmap : [index](README.md) · Niveau 2/5 · Précédent → [Level 1 — Explorer](01-explorer.md) · Suivant → [Level 3 — Shipper](03-shipper.md)

---

## What to do

Same skill (or a new one), but this time point it at your own codebase — personal project or something at work. This is the first level with real stakes: real code, real constraints, no more sandbox.

## What "good" looks like

This is also where the shape of the demo starts to matter for real: a spec you write here should look like something that could become the [tickets](linear) in the demo — same structure, same level of detail, just about something you actually care about shipping.

## You're done with this level when

A skill has produced something — a spec, a benchmark — about a real problem you have, and you'd be willing to show it to a colleague.

---

⬅️ Previous : [Level 1 — Explorer](01-explorer.md) · ➡️ Next : [Level 3 — Shipper](03-shipper.md)
