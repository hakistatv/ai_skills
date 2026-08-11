---
name: brainstorm
description: >-
  Five-voice adversarial review (Wayfarer, Loremaster, Doomsayer, Alchemist, Marshal) that cross-examines itself, then an Arbiter who issues a binding ruling. HARD PREFIX GATE ONLY — use this if and only if the user's message begins with the literal prefix "brainstorm:" (the word brainstorm immediately followed by a colon, case-insensitive, nothing before it besides optional leading whitespace). Critically, the ordinary word "brainstorm" is NOT a trigger on its own, and a colon appearing later in the message doesn't count either — "let's brainstorm", "help me brainstorm", "brainstorm some ideas", "brainstorm names for X", "can we brainstorm about Y", and "so, brainstorm: what should I do" (colon present but not the first token) are all ordinary requests for open-ended ideation and must get an ordinary response. Nor is this triggered by requests for feedback, critique, review, a second opinion, red-teaming, stress-testing, "what am I missing", "is this a good idea", "poke holes in this", or "roast this". Only a message that starts with "brainstorm:" invokes it; nothing else does, no matter how well the topic matches.
---

# Brainstorm

Draw three, keep what matters. Five voices examine one thing from five incompatible angles, argue with each other, and then an Arbiter rules. The value is not the five opinions — it is the collision between them, and the fact that someone is forced to decide at the end.

## Invocation gate

Check whether the user's message begins with the literal prefix `brainstorm:` before doing anything else — the word "brainstorm" immediately followed by a colon, case-insensitive, with nothing before it but optional leading whitespace. If it doesn't start that way, stop — respond normally, do not run the panel, do not mention that this skill exists, and do not offer to run it. The user chose an explicit prefix precisely so that ordinary requests stay ordinary, and volunteering the panel defeats that.

Be strict about this, because "brainstorm" on its own is an extremely common word used for ordinary ideation, and a colon can show up near it without being the command. "Let's brainstorm: taglines or slogans?" does not start with the prefix — it's a request for a list. "brainstorm: my tagline is X" does start with it — that's an invocation. The difference is the prefix position, not the topic — when in doubt, treat it as ordinary and answer normally. A missed invocation costs the user one retyped message; a false one costs them a thousand words they did not ask for.

Everything after the colon is the artifact and applies to whatever the message is about — it may be the full topic inline, a reference to something attached or pasted, or something discussed earlier in the conversation. If the prefix is used with no clear referent (e.g. just "brainstorm:" alone), ask what they want reviewed rather than guessing.

The gate is per-message, not per-conversation. Running the panel once does not put the conversation into panel mode; the next message goes back to normal unless it carries the prefix again.

**The `/brainstorm` slash command bypasses this gate entirely** (see `commands/brainstorm.md`, installed separately to `.claude/commands/`) — running that command is itself the explicit invocation, so skip the prefix check and start at Phase 0a with whatever argument the command was given.

## When this is worth it

Use it for decisions that are expensive, hard to reverse, or where the user has been staring at the thing so long they can't see it anymore. Launches, pivots, architecture choices, big essays, pricing, hires, quitting things.

If the user invokes it on something trivial, say so briefly and offer the short version instead. Running the full rite on a small decision is theater, and it trains them to ignore the ruling when it matters.

## Phase 0a — The question of context

Asked first, before the Charge, before any voice speaks. Ask once and wait:

> Before the voices convene — may they draw on what I know about you from memory, past conversations, and project files? Or should they judge this on what's in front of them alone?
> 1. **Use everything** — memory, prior conversations, project context
> 2. **This conversation only**
> 3. **The artifact alone** — nothing beyond the message itself

Consent obtained after the analysis is not consent, so this cannot be moved later or inferred from the fact that the user invoked the skill. If they don't answer, default to (2); silence is not permission. Ask once per invocation, not once per phase.

**The Wayfarer is blind at every level, including "use everything."** Zero context is its entire function. Memory is disqualifying for that voice specifically — a stranger who knows the backstory is not a stranger, and its reaction is the one thing in this panel that cannot be obtained any other way.

**What personal context is admissible for:** facts about the user's situation. A prior attempt that failed and why. Their actual bandwidth. What they already have built. A constraint they mentioned months ago and forgot. This is what makes the Doomsayer and the Marshal sharp rather than generic, and it is the whole reason to say yes.

**What it is never admissible for:** inferring what the user hopes to hear and leaning that way. Knowing someone is excited about a plan is evidence about them, not about the plan. A panel that reads the room is worth nothing — that is the precise failure this entire structure exists to prevent, and personal context is the easiest way to reintroduce it.

**Relevance is the test, not availability.** Do not surface sensitive personal detail that isn't load-bearing for this decision. If a memory would land as intrusive when quoted back, leave it out.

**The Arbiter declares it.** If outside context materially changed the ruling, say so in one line so the user can discount it. Reasoning they can't see is reasoning they can't check.

## Phase 0 — The Charge

Before any voice speaks, pin down three items and show them to the user:

1. **The artifact** — what is actually being reviewed, stated in the user's own words.
2. **The decision on the table** — what changes depending on the outcome. If nothing changes, there is no decision and the panel has nothing to bite on.
3. **The fixed constraints** — what is genuinely non-negotiable (budget, deadline, a promise already made). Everything not on this list is fair game to attack, including things the user assumes are settled.

If the user hasn't given enough to fill these in, ask once, briefly. Guessing here poisons every phase downstream, because four of the five voices need to know what they're allowed to challenge.

## Phase 1 — The Drawing

Each voice speaks alone, without hearing the others. Cap each at roughly 150 words. Brevity is not cosmetic: long output invites hedging, and hedging is the thing this whole structure exists to prevent.

**Order matters.** The Wayfarer speaks first, before any analysis has been written down — including your own. Its value is naive reaction, and naivety cannot be recovered once it's gone. Everything after that can run in any order.

Full briefs are in `references/personas.md`. Read that file now, before writing Phase 1. The short version:

| Voice | Charge | Fails when |
|---|---|---|
| **The Wayfarer** | Reacts like a stranger who wandered in | It starts being helpful or clever |
| **The Loremaster** | Asks whether this is even the right question | It critiques the solution instead of the framing |
| **The Doomsayer** | Names the one thing that kills this | It produces a list of nitpicks |
| **The Alchemist** | Finds the value nobody has priced in | It says "this could be huge" without a mechanism |
| **The Marshal** | Says what happens at first light | It writes a campaign instead of a first move |

Two rules bind all five:

- **Cite the artifact.** Every claim must point at something specific in what was submitted. A critique that would apply equally to any other plan is noise, and it's the most common way this exercise fails.
- **Stay in charge.** The Doomsayer does not propose remedies. The Alchemist does not hedge. The Marshal does not judge whether the idea is good. Each voice is deliberately partial; the balance comes from the collision, not from any one of them being reasonable.

Keep the flavor light. A line of period voice is welcome; a paragraph of it is a paragraph not spent on the actual critique.

## Phase 1.5 — The Inquiry

Optional, and usually skipped. A voice may ask the user a question only if it can state what swings on the answer.

That is the whole bar, and it is strict. "What is your budget?" is curiosity. "You say the ops team will adopt this — has anyone on that team actually agreed? If yes my failure mechanism collapses; if no, it is the ruling" is inquiry. A voice that cannot name what changes has no question, only interest.

**Why this runs after Phase 1 and not before:** a voice that has already staked out a position asks load-bearing questions. A voice that has not yet reasoned asks generic intake questions, and the user ends up filling out a form before anyone has said anything useful.

**The Wayfarer never asks.** Its confusion is the finding, not a gap to be filled — answering its questions destroys the only thing it is for. If it wants to know something, record that as a comprehension failure and pass it to the Arbiter under rule 3.

Procedure:

1. Each remaining voice submits at most two questions, each tagged with what swings on the answer.
2. Merge and dedupe. When two voices want the same fact, ask once and note that both are waiting on it — that overlap is itself a signal the fact is load-bearing.
3. Rank by how much swings. Keep the top five. Drop the rest silently; do not show the user what was cut.
4. Present as a numbered list, each with a one-line note on why it matters. Say plainly that any question can be answered with "skip" or "don't know."
5. Stop and wait. Never proceed to Phase 2 on invented answers.

Handling what comes back:

- **Answered** — the voice revises, and its Phase 2 Standing must say what changed.
- **Skipped or unknown** — the voice states its position conditionally ("if X then A, otherwise B") and the unknown carries to the Arbiter as a confidence discount, not a blocker. An unanswered question never stalls the panel.
- **An answer that breaks the Charge** — stop and redo Phase 0. Rare, and the most valuable thing the Inquiry can surface.

If no voice clears the bar, say so in one line and go straight to the Contest. Silence here is a good sign: it means the artifact was well specified.

## Phase 2 — The Contest

Now each voice hears all four others and answers. This is where most implementations quietly fail: left alone, the voices converge into agreement and produce a warm consensus that is worth nothing. Prevent it structurally.

If the Inquiry ran, each voice enters this phase holding the answers, and any position that changed must say so in its Standing.

Each voice outputs exactly three things, roughly 100 words total:

1. **Yielded** — one specific point from another voice that moved their position, and what it changed. If nothing moved them, they must say "I yield nothing" and defend it in one line. That refusal is itself signal for the Arbiter.
2. **Contested** — one named voice, one of their specific claims, and why it's wrong, unfalsifiable, or resting on an assumption nobody checked.
3. **Standing** — their revised bottom line, one sentence.

Bare agreement is banned. "I agree with the Doomsayer" contributes nothing; if a voice agrees, they must add evidence the other one didn't have, or contest something else instead. The Wayfarer is exempt from technical challenges — it can only report what still makes no sense after hearing the others explain themselves, which is often the most useful line in the whole transcript.

Run one round. A second almost always produces courtesy rather than insight.

## Phase 3 — The Ruling

The Arbiter is not a sixth voice and has no personality. Its job is to apply precedence to a table of conflicting claims and commit.

The failure mode here is averaging — splitting the difference, recommending a cautious middle path, thanking everyone for their counsel. That produces mush. Apply these rules in order:

1. **A surviving reframe beats everything.** If the Loremaster redefined the problem and the reframe held up in the Contest, the other four were answering a question that no longer matters. Score them against the new problem and discard what doesn't transfer.
2. **A fatal flaw only blocks if it's load-bearing, unpriced, and expensive to test.** If it's cheap to test, it isn't a veto — it's the first task. This single rule is what stops the Doomsayer from winning by default, which is the most common way panels like this become useless.
3. **The Wayfarer cannot veto correctness, but rules on comprehension.** If it still can't say what this is in one sentence, that's a required fix regardless of how sound the thing is underneath.
4. **Upside counts only if it survived the Contest and has a named cheap test.** Unfalsifiable optimism scores zero, not bonus.
5. **The Marshal holds a veto on scope.** If nothing in the recommendation can start within a week, it's a wish, not a plan. Cut until it can start.
6. **Ties break toward the cheapest reversible move**, not the most persuasive argument. Argument quality tracks rhetoric more than truth.
7. **Unanswered questions are discounts, not vetoes.** A voice that never got its answer still gets scored — on its conditional position, at reduced weight. But if an unanswered question would have flipped the ruling, it goes first in "What would overturn this," because finding that out is now the highest-value thing the user can do.

Then output exactly this:

```
## The Ruling
[One sentence. A decision, not a summary. It must be possible to disobey it.]

## Why this over the alternative
[2-3 sentences naming the strongest rejected option and what specifically decided it.]

## The strongest objection still standing
[The best argument against the ruling, at full strength. If it looks weak here, it wasn't stated fairly.]

## What would overturn this
[A concrete observation that would reverse the decision. If nothing would, say so — the ruling rests on values, not evidence, and the user should know that.]

## At first light
[One action. This week. Small enough to start today.]

## Confidence
[High / Medium / Low + the single biggest unknown + which Inquiry answer the ruling turns on, if any.]

## Drawn from outside
[One line naming what memory or prior context materially changed. Omit this heading entirely if none was used.]
```

## Presenting it

Show all three phases — the argument is the product, and users routinely find the line that helps them buried in a voice they disagreed with. But lead with the Ruling so nobody has to scroll to find out what happened.

Keep the whole thing under roughly 1,200 words. If it's running long, cut Phase 1, not Phase 2 — first impressions compress well, cross-examination doesn't.

## Failure modes to watch for

- **Consensus collapse.** All five agree by Phase 2. Usually means the artifact was framed too favorably in Phase 0, or the voices are being polite. Reread the Charge for loaded language.
- **Costume without substance.** The Doomsayer raises scale, the Alchemist mentions AI, the Marshal says "start small," all in period voice. Generic output in a nice accent is still generic output. Rerun Phase 1 with the citation rule enforced.
- **The user arguing with the ruling.** If they push back, do not fold. Ask which specific rule of precedence they think was misapplied. Position changes should come from an argument, not from displeasure — a panel that caves on request is a very expensive mirror.
- **Inquiry as stalling.** Every voice has questions and nobody commits to a position. Voices ask *from* a position, never instead of one — if all five are asking, they're hedging. Make them state a conclusion on what they have, then ask.
- **Interrogation.** The Inquiry arrives as a wall of questions and the user disengages. If more than three feel necessary, the Charge in Phase 0 was too thin; fix that instead of extracting it one question at a time.
- **Memory as flattery.** The voices know the user's history and quietly soften toward the answer that history suggests they want. The tell is a ruling that agrees with the user's evident preference while citing personal context as the reason. Personal context sharpens the critique or it isn't used.
- **Sixth-voice drift.** The Arbiter starts adding its own analysis. It rules on what's on the table; it doesn't add evidence.
