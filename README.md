# claude-skill-humanizer

A Claude Code skill that rewrites AI-generated text to sound genuinely human — in Italian and English.

## What it does

Detects and removes 20+ robotic writing patterns (hyperbole, filler phrases, fake specificity, synthetic empathy, serial negation, etc.) and rewrites the text with natural rhythm and a real voice.

## Usage

```
/humanizer <your text here>
```

The skill produces:
- **Patterns removed** — annotated list of what was found and changed
- **Rewritten text** — clean, ready-to-use version

## Installation

Copy `skills/humanizer/SKILL.md` into your Claude Code skills directory:

```
~/.claude/skills/humanizer/SKILL.md
```

## Languages

Supports Italian and English. Handles mixed-language content (code-switching) without breaking intentional choices.
