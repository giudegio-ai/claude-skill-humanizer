# claude-skill-humanizer

A Claude Code skill that finds and removes the tells of AI-generated writing, in Italian and English.

Most "make it sound human" prompts are one line: *"rewrite this so it doesn't sound like AI."* That line does almost nothing, because it gives the model no definition of what to look for. This skill replaces the vague instruction with a concrete taxonomy: **26 named pattern categories**, a 70-term banned vocabulary list, an anti-fabrication guardrail, and a 14-point self-check the model runs against its own output before returning it.

## The problem

AI-generated text has a recognizable fingerprint: reframe constructions ("It's not about X, it's about Y"), decorative metaphors, three-item lists everywhere, colon-reveal sentences, fake-profound closing lines, inanimate subjects performing human actions, faux-insight setups that flatter the writer as the lone expert. Individually these are just tics. Together they read as unmistakably synthetic, even when the underlying content is good.

Telling a model to "sound more human" doesn't fix this, because the model has no fixed idea of what "robotic" means — it's pattern-matching against a fuzzy concept it wasn't trained to name. Naming the patterns explicitly turns a vague aesthetic judgment into a checklist the model can actually execute against.

## What it does

```diff
- It's not about writing faster. It's about writing that actually sounds like you.
- This isn't just another editing tool — it's a complete rethinking of how AI writing works.
- Furthermore, it seamlessly adapts to your unique voice, whether formal or casual.
+ This tool edits toward your own voice, formal or casual, and does it fast.
```

The rewrite above removes: a negative-parallelism opener, a reframe construction, a decorative "seamlessly," and a dead transition — four tells in three sentences, which is typical.

## How it works

**26 named pattern categories**, each with concrete trigger phrases in both languages and a stated fix — not "avoid clichés" but "these specific constructions, replaced this specific way":

| # | Category | Example tell |
|---|----------|--------------|
| 1 | Negative parallelism & reframes | "Non si tratta di X. Si tratta di Y." |
| 2 | Hyperbolic / propaganda language | "rivoluzionario", "game-changer" |
| 3 | Filler openings & closings | "Let's dive in", "Spero che questo ti sia utile" |
| 4 | Dead transitions | "Furthermore", "That said" |
| 5 | Bloated verbs & nominalizations | "serves as" → "is", "made a decision" → "decided" |
| 6 | Decorative metaphors & abstract jargon | "scaffold the strategy" → "organize", "substrate" → "base" |
| 7 | Chatbot rhetorical questions | "Have you ever wondered...?" |
| 8 | Structural tics | forced three-item lists, em dashes (zero-tolerance), inline-header lists, curly quotes |
| 9 | Colon reveals | "The best part: it learns." |
| 10 | Fake-profound kickers | "That's it. That's the whole thing." |
| 11 | Vague attribution & hedging | "Studies show..." (no citation) |
| 12 | Empty intensifiers | "davvero", "essentially", "basically" |
| 13 | Synthetic empathy | "I understand this may be challenging" |
| 14 | Corporate/LinkedIn voice | "leverage synergies", "move the needle" |
| 15 | Fake specificity | "5 ways to...", "7 reasons why..." |
| 16 | Passive AI humility | "As an AI, I should note that..." |
| 17 | Vibe claims instead of mechanism | "SQL you can read" → name the actual mechanism or number |
| 18 | False agency | "the complaint becomes a fix" → name who does it |
| 19 | Distant narrator | "Nobody designed this" → speak to "you" |
| 20 | Wh-word openers | "What makes this work is the cache." → "The cache makes this work." |
| 21 | Vague absolutes | "always", "never" used with no evidence behind them |
| 22 | Faux-insight setups | "What most people get wrong is..." |
| 23 | Superficial -ing clauses | "highlighting...", "underscoring..." tacked on to fake an explanation |
| 24 | Synonym cycling | "protagonist / main character / central figure / hero" in one paragraph |
| 25 | Interpretive metadiscourse | "The key point is...", "As you can see..." |
| 26 | Summary-recap endings | "In conclusion,", "Overall," restating what was just said |

**A 70-term banned vocabulary list** — delve, harness, tapestry, paradigm, leverage, seamless, robust, and the rest of the words that flag a paragraph as machine-written on sight.

**An anti-fabrication guardrail.** Making text more concrete is one of this skill's core moves — replace "è molto importante" with what's actually at stake. Left unchecked, that instruction alone can push a rewrite toward inventing a plausible-sounding number, date, or anecdote just to kill vagueness. The skill blocks that explicitly: specificity has to come from the source material, never from thin air. If the original is vague and there's no real detail to recover, the rewrite either stays vague or flags the gap ("[dato mancante: quale numero?]") instead of filling it with something invented. Fabricated specificity is worse than honest vagueness — it reads as good writing while being a lie.

**A self-check loop, not a single pass.** Before returning output, the skill runs its own draft against 14 pass/fail checks (meaning preserved? nothing fabricated? every banned term gone? reframes eliminated? rhythm varied? register matched? false agency and distant-narrator voice gone? no faux-insight setups or summary-recap endings?) and revises until it passes — the same discipline a careful human editor applies, made explicit instead of implicit. The loop ends with a deliberately blunt self-audit question: *"what makes this obviously AI generated?"* — if anything still answers that, it gets fixed before the draft goes out.

**Two modes.** *Rewrite* (default) returns an annotated before/after. *Detect* audits text for the same 26 patterns without touching it — useful for reviewing writing you don't want rewritten, only diagnosed. Detect deliberately doesn't score "AI-ness" as a probability; named patterns are checkable evidence, and the skill treats that distinction as a feature, not a limitation.

### Why these specific patterns

The taxonomy isn't a one-off list — it grew by comparison against other AI-writing-cleanup skills (cursor's `unslop`, `stop-slop`, `no-ai-slop`), keeping only what survived scrutiny: patterns this skill already covered more thoroughly were left alone; patterns confirmed independently by more than one source (superficial -ing clauses, synonym cycling) were added with more confidence; proposals that risked over-editing legitimate writing (a blanket ban on all adverbs, a generic "could this sentence belong to any project" cut test) were deliberately left out.

## Usage

```
/humanizer <your text here>
```

Produces:
- **Patterns removed** — annotated list of what was found and changed, grouped by category
- **Rewritten text** — the clean version, ready to use

### Detect mode

```
/humanizer detect <your text here>
```

Lists every pattern found (quoted line, category, one-line fix) without rewriting anything.

## Installation

Copy `skills/humanizer/SKILL.md` into your Claude Code skills directory:

```
~/.claude/skills/humanizer/SKILL.md
```

## Languages

Italian and English, including mixed-language text — intentional code-switching is preserved, only the AI-filler layered on top gets removed.
