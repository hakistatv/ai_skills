# ai_skills

A collection of [Claude Agent Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills) — reusable `SKILL.md` packages that work in both Claude Code and the Claude app.

## Structure

Each top-level folder is one self-contained skill:

```
<skill-name>/
├── README.md        # human-facing: what it does, when to use it
├── SKILL.md          # Claude-facing: name, description, instructions
└── references/       # optional supporting files SKILL.md points to
```

## Skills

| Skill | Trigger | What it does |
|---|---|---|
| [`brainstorm/`](brainstorm/) | exact phrase "Brainstorm this" | Five-voice adversarial review panel with a binding Arbiter ruling |

Add a row here whenever a new skill folder is added.

## Getting the zips

Every push to `main` runs the **Build skill zips** GitHub Actions workflow. It auto-discovers every top-level folder containing a `SKILL.md` and packages each one into two zips:

1. Go to the [Actions tab](https://github.com/hakistatv/ai_skills/actions/workflows/build-skill-zips.yml).
2. Open the latest successful run.
3. Under **Artifacts**, download `<skill-name>-claude-code` or `<skill-name>-claude-app` for the skill you want (both contain the same files — pick either).
4. Unzip it — you'll get a `<skill-name>/` folder.

You can also trigger a build manually from that same page with **Run workflow**.

## Using a skill in Claude Code

Copy the unzipped `<skill-name>/` folder into your skills directory:

```bash
# Available in every project
cp -r <skill-name> ~/.claude/skills/<skill-name>

# Or, available only in one project
cp -r <skill-name> /path/to/your/project/.claude/skills/<skill-name>
```

Restart Claude Code (or start a new session) and it will pick up the skill automatically.

## Using a skill in the Claude app

1. Open the Claude app and go to **Settings → Capabilities → Skills**.
2. Click **Upload skill** and select the downloaded `<skill-name>-claude-app.zip` directly — no need to unzip first.
3. Enable the skill for the conversation or project where you want it available.

## Adding a new skill

1. Create a new top-level folder named after the skill (kebab-case).
2. Add `SKILL.md` with frontmatter (`name`, `description`) and instructions — see [`brainstorm/SKILL.md`](brainstorm/SKILL.md) for a full example.
3. Add a short `README.md` in the same folder — see the [skill README template](#skill-readme-template) below, or copy [`brainstorm/README.md`](brainstorm/README.md).
4. Put any supporting files (personas, scripts, templates) in `references/` (or `scripts/`, `assets/`, etc.) and point to them from `SKILL.md`.
5. Add a row to the skills table above.
6. Push to `main` — the zip workflow picks up the new folder automatically, no workflow changes needed.

## Skill README template

Each skill folder should have its own `README.md` aimed at a human reader — `SKILL.md` is instructions for Claude, this is the plain-English version for you:

```markdown
# <skill name>

One paragraph: what problem this solves and when to reach for it.

## Trigger

How you invoke it — exact phrase, slash command, or "just describe X and it kicks in."

## What it does

A short human-readable walkthrough of the phases/behavior. `SKILL.md` is the
authoritative instructions Claude follows; this section is the plain-English
summary for you.

## Files

- `SKILL.md` — the skill definition
- `references/...` — what's in here and why

## Example

A short example invocation and the kind of output to expect.
```
