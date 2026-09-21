# Level 1 — Explorer

**Goal:** pick a skill, make it yours.

*Roadmap: Level 1/5 · Next → Level 2 — Practitioner*

---

## What you'll need

- Access to a skill library — wherever your team keeps its shared AI skills (a shared repo, a wiki page, a shared drive). If you don't know where yours is, that's your first question to a teammate.
- Your AI assistant open, with a way to add a personal/custom skill.
- 15 minutes, and something throwaway to test on — not a real deliverable.

## First, what is a "skill"?

A skill is just a markdown file (sometimes a small folder of them) that tells the AI how to do one specific job well: write a spec, run a competitive benchmark, summarize meeting notes, whatever. It usually has two parts:
- A short **description** at the top — what it's for, when to use it.
- A body of **instructions** — the steps, the questions to ask, the format to output in.

That's it. No code, no install — it's a prompt someone already refined, saved as a file.

---

## Step 1 — Find a skill library, and pick one

Go wherever your team's skills live, and open the list. Pick **any skill that sounds closest to something you actually do** — writing a spec, running a competitive benchmark, summarizing feedback. It doesn't need to be the "right" one; there's no wrong pick for this level.

Before doing anything else, read it once, top to bottom. Its description tells you what it's for; its instructions tell you what kind of output to expect. That's the shape you're aiming for once you run it.

## Step 2 — Copy it into your app, as your own

A skill only does something once your AI assistant knows about it. Copy the skill's full text, then add it as a personal skill — look for a "Skills" or "Custom instructions" section in your app's settings, and add it there (paste the text, or upload the file; terminal-based assistants usually expect it saved as a file in a specific personal-skills folder — check the docs if you're not sure where).

You now have your own copy. Editing it later never touches the original shared version, and nothing you do here affects your teammates.

## Step 3 — Run it once, as-is

Pick a throwaway topic — something fake, low-stakes, unrelated to real work. Run the skill on it exactly as you copied it. Don't tweak anything yet.

Read the output against what you expected from Step 1. Does it match the shape the skill promised? If it asks you questions before producing anything, that's normal — answer them, even with made-up details. You're here to see how it behaves, not to produce something real.

## Step 4 — Make it yours

This is the step most people skip — and the one that turns "a tool someone gave me" into "my tool."

Open your copy and change something:
- The tone (more direct, less formal — whatever matches how you actually write).
- The output format (bullets instead of prose, a section you always want, one you never need).
- The questions it asks first, if it asks too many or too few.

Save your edit.

## Step 5 — Run it again, and compare

Same throwaway topic (or a new one), your edited version. Put the two outputs side by side. The second one should sound noticeably more like you — that's the whole point of this level.

---

## Common snags

- **You don't know where your skill library is.** Ask a teammate — every team that uses skills has one, even if it's informal.
- **You can't find where to add a custom skill in your app.** Search its docs for "custom skill," "custom instructions," or "personal prompt library" — the concept exists under slightly different names depending on the tool.
- **You're worried about breaking something.** You can't — you're working on your own copy, on a fake topic. Nothing here touches anything shared.

---

## You're done with this level when

- [ ] You've run a skill twice — once as-is, once after editing it.
- [ ] The second output actually sounds like you.
- [ ] You can name one concrete thing you changed, and why.

*Roadmap: Level 1/5 · Next → Level 2 — Practitioner*

---
_OLD_
# Level 1 — Explorer

**Goal: pick a skill, make it yours.**

> Roadmap : [index](README.md) · Niveau 1/5 · Suivant → [Level 2 — Practitioner](02-practitioner.md)

---

## What to do

Go to the skill library, choose *any* skill — it doesn't matter which one, pick whatever sounds closest to something you actually do (writing a spec, running a competitive benchmark). Run it in Claude Code or Cowork on a throwaway topic. No stakes, no real project yet.

Then personalize it: open the skill, tweak the wording, adjust the output format to match how you actually write. This is the step most people skip, and it's the one that turns "a tool someone gave me" into "my tool."

## What "good" looks like

The [Specs (fake)](notion) and [Benchmarks (fake)](notion) pages in the demo are exactly the shape a skill produces — read them before you run anything, so you know what you're aiming for.

## You're done with this level when

You've run a skill twice — once as-is, once after editing it — and the second output actually sounds like you.

---

➡️ Next : [Level 2 — Practitioner](02-practitioner.md)
