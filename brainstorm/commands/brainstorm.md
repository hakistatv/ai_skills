---
description: Run the five-voice brainstorm adversarial review panel on a topic
argument-hint: [what you want reviewed]
---

Run the `brainstorm` skill on the following, exactly as if the user's message had started with the `brainstorm:` prefix:

$ARGUMENTS

If no topic was given, treat it as an empty prefix and ask what they want reviewed rather than guessing.

This command running at all **is** the explicit invocation — do not re-check whether the message text starts with `brainstorm:`, skip straight past that gate. Load `SKILL.md` (and `references/personas.md`) from the `brainstorm` skill if you haven't already, and follow it exactly: Phase 0a (context question), Phase 0 (the Charge), Phase 1 (the Drawing), optional Phase 1.5 (the Inquiry), Phase 2 (the Contest), and Phase 3 (the Ruling).
