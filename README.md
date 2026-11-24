# Academic Presentations Skill for Codex

A Codex skill for creating high-quality academic presentations: conference
talks, seminar slides, thesis defenses, and grant briefings. It includes a
PDF summary of the presentation advice, but the PDF is optional.

## What It Does

This skill gives Codex communication-first standards appropriate for academic
and analytical contexts. When active, Codex will:

- Write every slide title as a **complete sentence stating the takeaway** ("action title"), not a topic label
- Structure the deck as a **logical argument** (situation → complication → resolution), not a collection of independent slides
- Apply the **ghost deck test**: the action titles alone, read in sequence, should tell the full story
- Place **one exhibit per results slide** and annotate the key finding directly on the chart
- Apply **citation standards**: in-text citations on every borrowed figure, a References slide at the end
- End on a **Conclusions slide** that stays on screen during Q&A — never on "Thank You" or a blank
- Apply minimal, communication-first design: white backgrounds, single sans-serif font, three colours maximum, no decorative icons

## Installation

Codex skills are directories containing `SKILL.md` and any supporting files.
For a project-only installation, place this repository's contents at
`.agents/skills/academic-pptx/` in the project root. For a user-level
installation, place them at `$CODEX_HOME/skills/academic-pptx/`; when
`CODEX_HOME` is unset, Codex uses `~/.codex/skills/`.

The copy must include `SKILL.md`, `content_guidelines.md`, `slide_patterns.md`,
and `agents/openai.yaml`. Exclude the clone's `.git` metadata. After
installing, start a new Codex turn so the skill index can refresh. The
copy-and-verify prompts below automate both variants.

### Prompt: install as a project-level skill

Paste this prompt into an AI agent from the root of the project where the
skill should be available:

```text
Install the academic-pptx Codex skill for this project.

1. Clone https://github.com/ayananerv/academic-pptx-skill-codex.git into a
   temporary directory (shallow clone is fine).
2. Copy the skill files, including SKILL.md, content_guidelines.md,
   slide_patterns.md, and agents/openai.yaml, into
   .agents/skills/academic-pptx/ relative to the current project root.
   Exclude the clone's .git metadata.
3. Do not create a nested academic-pptx-skill-codex directory inside the
   destination. Do not overwrite an existing destination without first
   inspecting it and receiving explicit approval.
4. Verify that .agents/skills/academic-pptx/SKILL.md exists and that its
   frontmatter name is academic-pptx.
5. Report the installed path and remind me to start a new Codex turn.

Use only the repository files needed by this skill; do not modify unrelated
project files.
```

### Prompt: install as a user-level skill

Paste this prompt into an AI agent when the skill should be available across
projects for the current user:

```text
Install the academic-pptx Codex skill for my user account.

1. Clone https://github.com/ayananerv/academic-pptx-skill-codex.git into a
   temporary directory (shallow clone is fine).
2. Set the destination to
   ${CODEX_HOME:-$HOME/.codex}/skills/academic-pptx and create its parent
   directory if needed.
3. Copy the skill files, including SKILL.md, content_guidelines.md,
   slide_patterns.md, and agents/openai.yaml, into that destination.
   Exclude the clone's .git metadata.
4. Do not create a nested academic-pptx-skill-codex directory inside the
   destination. Do not overwrite an existing destination without first
   inspecting it and receiving explicit approval.
5. Verify that
   ${CODEX_HOME:-$HOME/.codex}/skills/academic-pptx/SKILL.md exists and that
   its frontmatter name is academic-pptx.
6. Report the installed path and remind me to start a new Codex turn.

Use only the repository files needed by this skill; do not modify unrelated
files.
```

## Usage

Just ask Codex naturally:

- *"Make slides for my conference paper on X"*
- *"Build a deck for my thesis defense"*
- *"Create a seminar presentation about my research on Y"*

Codex can detect the academic context and load this skill automatically when
it is installed and discoverable. You do not need to give any special
instructions.

This skill handles content, argument structure, and design standards. Use a
compatible PPTX skill or the project's existing PPTX toolchain for technical
file generation and visual QA.

## File Structure

```
academic-pptx/
├── SKILL.md                  # Entry point: routing logic and design standards
├── content_guidelines.md     # Argument structure, action titles, citations, deck architecture
├── slide_patterns.md         # Per-slide-type implementation patterns with PptxGenJS code
├── agents/openai.yaml        # Optional Codex UI metadata
└── README.md                 # This file (repository documentation)
```

## Background

The guidelines in this skill draw on:
- Barbara Minto's *Pyramid Principle* (structured argument, action titles)
- Naegle (2021), "Ten simple rules for effective presentation slides," *PLOS Computational Biology*
- Standard consulting and academic presentation practice (McKinsey, conference norms)
- Community feedback on common AI presentation behaviour in professional contexts

## License

MIT — free to use, adapt, and share.
