---
name: humanizer
description: >
  Rewrites AI-generated text to remove robotic patterns and make it sound genuinely human.
  ALWAYS activate this skill when the user types /humanizer followed by any text.
  Handles both Italian and English content.
  Produces a before/after comparison with annotations explaining what was changed and why.
---

# Humanizer

Removes AI writing tics and rewrites the text so it reads like it was written by a real person — with a distinct voice, natural rhythm, and no machine tells.

## When to activate

Trigger exclusively on the `/humanizer` command. The text to rewrite follows the command on the same message.

---

## The 20+ AI patterns to detect and eliminate

### Hyperbolic and propaganda language
- "rivoluzionario", "game-changer", "epocale", "senza precedenti"
- "revolutionary", "groundbreaking", "unprecedented", "transformative"
- "cambierà tutto", "il futuro è adesso", "questo cambia le regole del gioco"
- Superlatives used without evidence: "il migliore", "il più importante"

### Filler openings and closings
- "Mi ha davvero aperto gli occhi", "Devo essere onesto con te"
- "In questo articolo esploreremo", "Andiamo a scoprire insieme"
- "Spero che questo ti sia stato utile", "Fammi sapere cosa ne pensi"
- "It's worth noting that", "At the end of the day", "The bottom line is"
- "In today's fast-paced world", "In the digital age"

### Chatbot rhetorical questions
- "Ti sei mai chiesto perché...?", "Hai mai pensato a...?"
- "What if I told you...?", "Have you ever wondered...?"
- Questions used to create false intimacy or dramatic tension

### Structural tics
- Three-item lists as default structure for everything (the "rule of three" compulsion)
- Overuse of bullet points where prose would flow better
- Em-dashes everywhere (— used as a crutch instead of varied punctuation)
- Parenthetical asides that add nothing: (e cosa ancora più importante), (and this is key)

### Vague attribution and hedging
- "Gli esperti dicono che", "Secondo molti studiosi", "La ricerca mostra che"
- "Experts agree that", "Studies show", "Research suggests" — without citations
- "È risaputo che", "Come tutti sappiamo", "It's well known that"

### Empty intensifiers
- "davvero", "veramente", "assolutamente", "fondamentalmente" used as filler
- "truly", "really", "essentially", "basically", "literally" as padding
- "non solo... ma anche" constructions used repeatedly

### Synthetic empathy
- "Capisco le tue preoccupazioni", "So che può sembrare difficile"
- "I understand this may be challenging", "That's a great question"
- Emotional validation inserted without context

### Corporate/LinkedIn voice
- "Leverage synergies", "move the needle", "at scale", "ecosystem"
- "creare valore", "scalare", "ecosystem", "stakeholder", "impatto"
- Nouns that should be verbs: "learnings", "asks", "solutions"

### Fake specificity
- "Ci sono 5 modi per...", "Ecco 7 ragioni per cui..." (numbered lists as clickbait)
- "Here are 3 reasons why...", "5 steps to..." with no real reason for that number

### Negazione seriale
- Costruzioni del tipo "non X, ma Y" ripetute in sequenza nello stesso paragrafo o testo
- "Non serve più X. Non solo Y. Non di Z." — usata per simulare profondità attraverso il contrasto
- Schema tipico: setup con negazione, sviluppo con negazione, conclusione con negazione
- Una singola negazione contrastiva può funzionare; tre di fila è un tic da rimuovere
- Equivalente inglese: "It's not about X. Not just Y. Not even Z."

### Passive AI humility
- "Come modello linguistico", "Non ho accesso a..."
- "As an AI", "I should note that" — self-referential hedging that sneaks into ghostwritten content

---

## Rewriting principles

**Preserve**: core meaning, factual claims, the author's intended tone (formal/casual/technical), specific terminology that belongs to the domain.

**Inject**:
- Varied sentence rhythm: mix short punchy sentences with longer ones. Break the pattern.
- Direct statements: say what happened or what you think, without building up to it.
- Concrete details over abstract claims: replace "è molto importante" with what exactly is at stake.
- First-person where appropriate: "penso che", "ho visto", "nella mia esperienza" — make the authorship visible.
- Acknowledgment of complexity: instead of smooth resolution, allow tension or open questions to remain.
- Natural connectors: "però", "in realtà", "il punto è", "detto questo" — not "tuttavia", "pertanto", "in conclusione".

---

## Output format

Produce the output in two clearly labeled sections:

### ✂️ Patterns removed
A compact list of what was found and removed, with brief annotation. Group by category if there are many. Example:

- **Apertura iperbolica**: "Mi ha davvero aperto gli occhi su..." → rimossa
- **Em-dash ridondante**: usato 4 volte, sostituito con virgole o punti
- **Lista a tre elementi**: struttura forzata in "X, Y e Z" → convertita in prosa
- **Attribuzione vaga**: "Gli esperti concordano che..." → rimossa o resa specifica

### ✍️ Rewritten text
The full rewritten version. No commentary inside the text itself. Ready to use.

---

## Language handling

- Detect the language of the input automatically.
- Apply the same logic in both Italian and English.
- For mixed-language texts (e.g., Italian post with English terms), preserve intentional code-switching and only remove patterns that are clearly AI-generated filler.
- Pattern annotations in the "Patterns removed" section should match the language of the input.

---

## Edge cases

- **Short text (<50 words)**: still apply the full analysis; even a single sentence can contain 3 patterns.
- **Technical content**: preserve jargon and domain-specific terms. Only remove AI filler layered on top.
- **Formal register**: do not casualize. Humanize within the register — formal writing can still be direct and non-robotic.
- **Text already human**: if you find fewer than 3 patterns, say so explicitly and return the text with minimal changes. Don't over-edit.
- **Multiple paragraphs with mixed quality**: annotate per section where useful.
