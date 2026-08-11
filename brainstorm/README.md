# brainstorm

A structured adversarial review for decisions that are expensive, hard to reverse, or that you've been staring at too long to see clearly anymore — launches, pivots, architecture calls, pricing, big essays, quitting things. Five voices attack the idea from incompatible angles, argue with each other, and an Arbiter is forced to issue a ruling instead of a mushy consensus.

## Trigger

The exact phrase **"Brainstorm this"**, anywhere in the message. Ordinary use of the word "brainstorm" (e.g. "let's brainstorm some names") is *not* a trigger and gets a normal response — this is deliberate, so the panel never shows up uninvited.

## What it does

1. **Context check** — asks once whether the voices may use memory/prior context, or judge the artifact cold.
2. **The Charge** — pins down what's being reviewed, what decision is on the table, and what's actually non-negotiable.
3. **The Drawing** — five voices react independently, each capped at ~150 words:
   - **Wayfarer** — a stranger's naive first reaction
   - **Loremaster** — is this even the right question?
   - **Doomsayer** — the one mechanism that kills this
   - **Alchemist** — the value nobody has priced in
   - **Marshal** — what happens at first light
4. **The Inquiry** *(optional)* — a voice may ask the user one load-bearing question if it can name what swings on the answer.
5. **The Contest** — each voice reads the other four and yields, contests, and restates its standing. Bare agreement is banned.
6. **The Ruling** — an Arbiter (no personality of its own) applies a fixed precedence order and commits to one decision, the strongest objection against it, what would overturn it, and the first concrete action to take this week.

See [`SKILL.md`](SKILL.md) for the full mechanics and [`references/personas.md`](references/personas.md) for each voice's full brief.

## Files

- `SKILL.md` — the skill definition Claude reads: invocation gate, all five phases, the Ruling format, and failure modes to watch for
- `references/personas.md` — full first-person briefs for each of the five voices, what they're forbidden from doing, and notes on which pairings produce the sharpest contests

## Example

> **You:** Brainstorm this: I want to quit my job and go all-in on a solo SaaS product. I have 8 months of runway.

Claude asks once whether it may use what it knows about you, pins down the Charge, runs all five voices through the Drawing and Contest, then closes with a Ruling — a one-sentence decision, the strongest case against it, what would overturn it, and a concrete first move for this week.
