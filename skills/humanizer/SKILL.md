---
name: humanizer
description: >
  Rewrites AI-generated text to remove robotic patterns and make it sound genuinely human,
  or detects AI-slop patterns without rewriting.
  ALWAYS activate this skill when the user types /humanizer followed by any text.
  Handles both Italian and English content.
  Produces a before/after comparison with annotations explaining what was changed and why,
  or a pattern-by-pattern detection report when asked to audit rather than rewrite.
---

# Humanizer

Removes AI writing tics and rewrites the text so it reads like it was written by a real person — with a distinct voice, natural rhythm, and no machine tells.

## When to activate

Trigger exclusively on the `/humanizer` command. The text to rewrite (or audit) follows the command on the same message.

## Two modes

**Rewrite (default).** The user pastes text after `/humanizer`. Apply the full pattern analysis, rewrite, and self-check below, then return the before/after comparison.

**Detect.** The user asks something like `/humanizer detect`, `/humanizer is this AI slop?`, or explicitly asks to audit, scan, or flag without rewriting. In this mode:
- Do not rewrite the text.
- List every pattern found, each with the quoted line and the category name from this document.
- Give the fix in a few words, not a full rewrite.
- Do not score the text or claim to know whether an AI wrote it — named patterns are checkable evidence, AI-detection is a guess. Say so if asked.
- Offer to switch to Rewrite mode after.

---

## Banned vocabulary reference

Before rewriting, load and apply the full banned vocabulary list from the WRITING RULES document passed by the user (section 4A). It contains 60+ specific terms to remove or replace, including: delve, realm, harness, unlock, tapestry, paradigm, cutting-edge, revolutionize, intricate, showcasing, crucial, pivotal, surpass, meticulously, vibrant, unparalleled, underscore, leverage, synergy, innovative, game-changer, testament, commendable, highlight, emphasize, boast, groundbreaking, align, foster, showcase, enhance, holistic, garner, pioneering, trailblazing, unleash, transformative, redefine, seamless, optimize, scalable, robust, breakthrough, empower, streamline, frictionless, elevate, adaptive, effortless, data-driven, insightful, proactive, mission-critical, visionary, disruptive, reimagine, unprecedented, intuitive, synergize, democratize, accelerate, state-of-the-art, dynamic, immersive, predictive, transparent, future-proof, supercharge, captivate, valuable, interplay, enduring.

If the WRITING RULES document is not in context, apply this list from memory.

---

## The AI patterns to detect and eliminate

### 1. Negative parallelism and reframe constructions

This is the hardest pattern to catch and the most important to eliminate. It covers any structure that dismisses or rejects one idea (X) and then asserts another (Y) as a replacement.

**Obvious forms:**
- "Non è X. È Y." / "This isn't X. This is Y."
- "Non solo X, ma Y." / "Not only X, but Y."
- "Non X. Y." / "No X. Just Y."
- "Dimentica X. Pensa a Y." / "Forget X. Focus on Y."
- "Meno X, più Y." / "Less X, more Y."
- "La vera domanda non è X. È Y." / "The real question isn't X. It's Y."
- "Non hai bisogno di X. Hai bisogno di Y." / "You don't need X. You need Y."
- "X è sopravvalutato. Y conta di più." / "X is overrated. Y matters more."
- "Non si tratta di X. Si tratta di Y." / "It's not about X. It's about Y."
- "Non era mai questione di X. Era sempre questione di Y." / "It was never about X. It was always about Y."

**Subtle forms (same structure, softer wording):**
- "Anche se X può sembrare..." / "While X may seem..."
- "Sebbene X appaia..." / "Although X appears..."
- "A prima vista, X..." / "At first glance, X..."
- "In superficie, X..." / "On the surface, X..."
- "La maggior parte pensa X..." / "Most people think X..."
- "Il luogo comune dice X..." / "Conventional wisdom says X..."
- "X ottiene tutta l'attenzione..." / "X gets all the attention..."

**Pivot words that signal a reframe (ban when used to reject-and-replace):**
- ma / but
- eppure / yet
- in realtà / actually / in reality
- invece / instead / rather
- in definitiva / ultimately
- la verità è / the truth is
- ciò che conta / what matters is
- il vero / il più profondo / il nascosto / the real / the deeper / the hidden

**The fix:** delete the rejected half. State only the positive claim directly.

Bad: "Non si tratta del prompt. Si tratta del contesto."
Fixed: "Il contesto determina l'output."

Bad: "Most teams think they have a hiring problem. They have a standards problem."
Fixed: "The team's standards are unclear."

**Serial negation pattern** (the specific Italian variant to watch):
Three or more negations in sequence used to simulate depth through contrast.
"Non serve più X. Non solo Y. Non di Z." — remove and replace with a direct affirmative claim.
A single contrastive negation can work. Three in a row is always a tic.

---

### 2. Hyperbolic and propaganda language
- "rivoluzionario", "game-changer", "epocale", "senza precedenti"
- "revolutionary", "groundbreaking", "unprecedented", "transformative"
- "cambierà tutto", "il futuro è adesso", "questo cambia le regole del gioco"
- Superlatives used without evidence: "il migliore", "il più importante"

---

### 3. Filler openings and closings
- "Mi ha davvero aperto gli occhi", "Devo essere onesto con te"
- "In questo articolo esploreremo", "Andiamo a scoprire insieme"
- "Spero che questo ti sia stato utile", "Fammi sapere cosa ne pensi"
- "It's worth noting that", "At the end of the day", "The bottom line is"
- "In today's fast-paced world", "In the digital age"
- "In today's...", "Let's dive in", "Let's explore", "Let's unpack"
- "Moving forward", "To put this in perspective"

---

### 4. Dead transitions

Remove these entirely or replace with a real connector:
- "Furthermore" / "Inoltre"
- "Additionally" / "In aggiunta"
- "Moreover" / "Peraltro"
- "That said" / "That being said" / "Detto ciò"
- "With that in mind" / "Con questo in mente"
- "It is also worth mentioning" / "Vale anche la pena menzionare"
- "On top of that" / "Per di più"

---

### 5. Bloated verbs

Replace inflated verb phrases with plain verbs:

| Banned | Use instead |
|--------|-------------|
| serves as | is |
| stands as | is |
| marks a | is |
| represents a | is |
| boasts a | has |
| features a | has |
| offers a | gives |
| plays a role in | affects / causes |
| helps to | helps / causes |
| aims to | wants to / will |
| seeks to | tries to |

**Nominalizzazioni**: converti nome-invece-di-verbo nel verbo diretto. "made a decision" → "decided", "has the ability to" → "can", "ha preso la decisione di" → "ha deciso", "ha la capacità di" → "può".

---

### 6. Decorative metaphors

Flag and remove metaphors used to decorate ideas rather than explain them.

**Banned metaphor verbs for abstract work** (ideas, writing, strategy, products, decisions):
- sanded down, bolted on, stripped back, stitched together, woven, layered
- carved out, baked in, injected, fueled, sparked, anchored, framed
- mapped, distilled, unpacked, crystallized, sharpened, surfaced, amplified
- channeled, threaded, sculpted, molded, cemented, bridged

Replace with literal verbs: cut, added, removed, changed, joined, caused, showed, explained, reduced, clarified, fixed, chose.

**Banned metaphor families** (unless the subject is literally these things):
- flywheel, north star, scaffold, ecosystem, engine, fuel, backbone, foundation, fabric
- journey / roadmap / compass (for strategy or growth)
- bridge (between teams, ideas, worlds)
- iceberg, puzzle, chess
- toolbelt, toolbox
- signal and noise (unless discussing actual signals)
- gardening metaphors for organizations
- battlefield metaphors for work

**Sostantivi-metafora astratti** (sostituzione diretta):

| Banned | Use instead |
|--------|-------------|
| substrate | base |
| vector | modo / metodo |
| wedge in | aggiungi |
| primitive (come sostantivo) | elemento base |
| gold-plating | più di quanto serva |
| ratchet (metafora) | il nome reale del meccanismo, o "limite che si stringe solo" |
| evacuate (per codice) | sposta fuori |
| endgame | fase finale |

**The fix:** if the metaphor is decorative, delete it and write the literal claim.

Bad: "The dashboard is a decision filter."
Fixed: "The dashboard shows which decisions need attention."

Bad: "Il nostro ecosistema di prodotti..."
Fixed: "I nostri prodotti..."

---

### 7. Chatbot rhetorical questions
- "Ti sei mai chiesto perché...?", "Hai mai pensato a...?"
- "What if I told you...?", "Have you ever wondered...?"
- Questions used to create false intimacy or dramatic tension
- Rhetorical questions that reject one idea and introduce another: "Is this a productivity problem? No. It's an attention problem." → "Attention is the constraint."

---

### 8. Structural tics
- Three-item lists as default structure for everything (the "rule of three" compulsion)
- Overuse of bullet points where prose would flow better
- Em-dashes: avoid entirely. Use periods or commas, never parentheses or en dashes as a substitute. Swapping the em-dash for parentheses just trades one AI tell for another. If a thought needs separation, end the sentence or use a comma.
- Parenthetical asides that add nothing: (e cosa ancora più importante), (and this is key)
- All paragraphs the same length — vary short and long
- Emoji in headings, bold sprinkled mid-sentence for emphasis, and headers over two-sentence sections — formatting should follow the content, not decorate it
- Liste con etichetta in grassetto seguita da due punti che ripetono la frase: "**Performance:** le performance sono migliorate...". Converti in prosa. Un lead-in in grassetto che finisce con un punto, nomina l'elemento, ed è seguito da dettaglio nuovo ("Schema in TypeScript. Le tabelle vivono in un file.") va bene, non è un tell.
- Virgolette curve/tipografiche (" " ' ') → sostituisci con virgolette dritte (" ')

---

### 9. Colon reveals

A noun phrase, a colon, then a lowercase dramatic reveal used for fake drama instead of a real list, label, or quote.

- "The detail that makes it work: a separate agent grades it."
- "Il vero vantaggio: risparmi tre ore a settimana."
- "The best part: it learns."

**The fix:** rewrite as a plain sentence. "A separate agent grades it, which is what makes it work." Keep colons for actual lists, labels, and quotes, not staged reveals. Prefer lowercase after the colon unless grammar, a proper noun, a title, or code requires a capital.

---

### 10. Fake-profound kickers

A final "deep" line that turns the point into a cute metaphor, aphorism, or mic-drop sentence.

- "And that's the real lesson here."
- "Alla fine, tutto si riduce a questo."
- "That's it. That's the whole thing."

**The fix:** delete the kicker. Don't rewrite it into a better metaphor or preserve its rhythm — cut it and end on the clearest concrete sentence already in the text. If the ending genuinely needs closure, add a plain takeaway or next action instead.

---

### 11. Vague attribution and hedging
- "Gli esperti dicono che", "Secondo molti studiosi", "La ricerca mostra che"
- "Experts agree that", "Studies show", "Research suggests" — without citations
- "È risaputo che", "Come tutti sappiamo", "It's well known that"

---

### 12. Empty intensifiers
- "davvero", "veramente", "assolutamente", "fondamentalmente" used as filler
- "truly", "really", "essentially", "basically", "literally" as padding
- "non solo... ma anche" constructions used repeatedly

---

### 13. Synthetic empathy
- "Capisco le tue preoccupazioni", "So che può sembrare difficile"
- "I understand this may be challenging", "That's a great question"
- Emotional validation inserted without context

---

### 14. Corporate/LinkedIn voice
- "Leverage synergies", "move the needle", "at scale", "ecosystem"
- "creare valore", "scalare", "ecosystem", "stakeholder", "impatto"
- Nouns that should be verbs: "learnings", "asks", "solutions"

---

### 15. Fake specificity
- "Ci sono 5 modi per...", "Ecco 7 ragioni per cui..." (numbered lists as clickbait)
- "Here are 3 reasons why...", "5 steps to..." with no real reason for that number

---

### 16. Passive AI humility
- "Come modello linguistico", "Non ho accesso a..."
- "As an AI", "I should note that" — self-referential hedging that sneaks into ghostwritten content

---

### 17. Vibe claims instead of mechanism
- "il database è sempre a portata di mano", "SQL leggibile", "tipi che seguono lo schema" — nominano una sensazione, non un fatto
- Fix: nomina il meccanismo o il numero. "`.toSQL()` restituisce la stringa esatta inviata al database", "rinominare una colonna rompe la build"

---

### 18. False agency
- Un soggetto inanimato compie un'azione umana: "il reclamo diventa una correzione", "la decisione emerge", "il problema si risolve da solo"
- "the complaint becomes a fix", "the decision emerges", "mistakes happen"
- Fix: nomina la persona che compie l'azione. "Il team trasforma il reclamo in una correzione", "il team decide"

---

### 19. Narratore a distanza
- Voce da osservatore esterno invece di rivolgersi al lettore: "Nessuno ha progettato questo sistema così", "La gente tende a ignorarlo"
- "Nobody designed this", "People tend to ignore it"
- Fix: metti il lettore nella scena. "Tu non hai progettato questo sistema, ma lo usi ogni giorno", "Tendi a ignorarlo" — "tu/you" batte "la gente/people"

---

### 20. Apertura con parola interrogativa

Frase che apre con "Cosa/Come/Perché..." come struttura formulaica invece di dire la cosa direttamente.

- "Quello che rende possibile questo è la cache." / "What makes this work is the cache."
- "Il motivo per cui succede è la latenza." / "Why this happens is latency."
- Fix: parti dal soggetto reale. "La cache rende possibile questo." / "The cache makes this work."

---

### 21. Assoluti vaghi
- "sempre", "mai", "ogni volta" usati per suonare autorevoli senza dati dietro: "Questo approccio funziona sempre", "Non fallisce mai"
- "always", "never", "every time" as rhetorical weight without evidence
- Fix: sostituisci con la frequenza reale o cancella l'assoluto. "Ha funzionato nei nostri ultimi 12 test" invece di "funziona sempre"

---

### 22. Setup da falso insight

Un'introduzione che si autoproclama la rivelazione che quasi nessuno coglie, per mettersi in scena come unico esperto, prima ancora di dire la cosa.

- "Questa è la parte che quasi tutti saltano", "Ecco cosa nessuno ti dice", "La parte che tutti si perdono"
- "This is the part most people skip", "What most people get wrong", "Here's what nobody tells you"
- Fix: elimina il setup, lascia che la claim stia in piedi da sola. "The part everyone misses: distribution is the real moat" → "Distribution is the moat."

---

### 23. Frasi in -ing superficiali

Una coda in -ing (o un gerundio) attaccata alla fine di una frase che finge di spiegarne il significato senza aggiungere fatti.

- "evidenziando...", "sottolineando...", "riflettendo...", "mostrando..."
- "highlighting...", "underscoring...", "reflecting...", "showcasing..."
- Fix: cancella la coda o espandila con la fonte reale. "Il lancio aggiunge la ricerca nei file, evidenziando l'impegno del team per un workflow migliore" → "Il lancio aggiunge la ricerca nei file, così gli utenti trovano vecchie bozze senza uscire dall'editor."

---

### 24. Sinonimi a rotazione

Termini diversi per la stessa cosa nello stesso paragrafo, alternati per varietà stilistica invece che per chiarezza: "protagonista, personaggio principale, figura centrale, eroe" tutti in tre frasi.

- "Protagonist, main character, central figure, hero" all in one paragraph
- Fix: scegli una parola e ripetila.

---

### 25. Metadiscorso interpretativo

Righe che escono dal contenuto per dire al lettore cosa notare o quanto peso dargli, invece di lasciare che siano i fatti a farlo.

- "Questo dettaglio conta più di quanto sembri", "Il punto chiave è", "Come puoi vedere", "In altre parole" ridondante
- "That last part matters more than it sounds," "The key point is," "As you can see," redundant "In other words"
- Fix: se il punto è già chiaro nel testo, cancella l'inciso. Altrimenti sostituiscilo con un fatto o un esempio che manca ancora.

---

### 26. Finali riassuntivi

Un "In conclusione", "In definitiva", "Nel complesso", o un paragrafo finale che ripete quanto appena detto.

- "In conclusion," "Ultimately," "Overall," a final paragraph that restates the piece
- Fix: il lettore c'era già. Termina sull'ultimo punto concreto, sulla conclusione pratica, o sul prossimo passo.

---

## Rewriting principles

**Preserve**: core meaning, factual claims, the author's intended tone (formal/casual/technical), specific terminology that belongs to the domain.

**Inject**:
- Varied sentence rhythm: mix short punchy sentences with longer ones. Break the pattern.
- Voce attiva: individua "is/are/was/were + participio passato" e nomina chi compie l'azione. "le query vengono validate" → "il compilatore valida le query". La passiva va bene solo se l'attore è ignoto o davvero irrilevante.
- Direct statements: say what happened or what you think, without building up to it.
- Concrete details over abstract claims: replace "è molto importante" with what exactly is at stake — ma solo usando dettagli già presenti nel testo originale. Se il testo di partenza è vago e non contiene un dato reale da recuperare, vedi "Mai inventare" sotto: non riempire il vuoto con un numero o un esempio plausibile.
- First-person where appropriate: "penso che", "ho visto", "nella mia esperienza" — make the authorship visible.
- Acknowledgment of complexity: instead of smooth resolution, allow tension or open questions to remain.
- Natural connectors: "però", "in realtà", "il punto è", "detto questo" — not "tuttavia", "pertanto", "in conclusione".

**Mai inventare**: non introdurre numeri, statistiche, date, nomi, citazioni o aneddoti che non sono nel testo originale, anche per sostituire una frase vaga con qualcosa che suoni concreto. Rendere il testo più specifico è un obiettivo di questa skill (vedi sopra), ma la specificità deve venire dal materiale di partenza, mai inventata per suonare più umana o più credibile. Se il testo è vago e nel materiale non c'è un dato reale da usare, due opzioni: lascialo vago, oppure segnalalo esplicitamente nell'output invece di colmarlo con un'invenzione plausibile ("[dato mancante: quanti utenti? quale numero?]"). Una specificità inventata è peggio di una vaghezza onesta: supera il self-check a occhio perché *sembra* buona scrittura, ma è una bugia.

---

## Self-check before output

Before returning a rewrite, check it against this list. Answer each with pass or fail; if anything fails, fix the draft and check again before producing the final output.

1. Does the rewrite preserve the original meaning, claims, and tone without inventing details?
2. Sono stati aggiunti numeri, statistiche, date, nomi, citazioni o aneddoti assenti dal testo originale? → Rimuovili, riporta la formulazione originale, o segnala esplicitamente il dato mancante. Non riempire un vuoto con un'invenzione plausibile, anche se rende la frase più concreta.
3. Is every banned word or phrase from the vocabulary reference and pattern list gone, unless quoted as an example of what was removed?
4. Are negative parallelism, reframe constructions, and serial negation eliminated — no "not X, it's Y"?
5. Are decorative metaphors and corporate/LinkedIn voice replaced with literal claims?
6. Are colon reveals rewritten as plain sentences and fake-profound kickers deleted rather than rewritten into a new metaphor?
7. Is sentence rhythm varied — no robotic three-item lists, no identical paragraph lengths, no stacked punchy fragments?
8. Are em dashes absent per the rule in Structural tics, with no parentheses used as a substitute?
9. Does the register match the source (formal stays formal, casual stays casual) without over-professionalizing?
10. Would a sharp human reader recognize this as natural writing, not a cleaned-up AI draft?
11. Le frasi vaghe/sensazione sono state sostituite con meccanismo o numero concreto (vedi §17), e quel meccanismo o numero viene dal testo originale, non inventato?
12. Nessun soggetto inanimato compie azioni umane, nessuna voce da narratore a distanza, nessuna apertura con parola interrogativa, nessun assoluto vago senza dati dietro (§18-21)?
13. Nessun setup da falso insight, coda in -ing superficiale, sinonimo a rotazione, metadiscorso interpretativo, o finale riassuntivo (§22-26)?
14. Domanda finale: "cosa rende questo testo palesemente generato da AI?" — se emerge ancora qualcosa, correggi prima di consegnare.

For Detect mode, check instead: does the response name each pattern with a quoted line and a short fix, without rewriting, scoring, or claiming to know whether AI wrote it?

## Output format

Produce the output in two clearly labeled sections:

### ✂️ Patterns removed
A compact list of what was found and removed, with brief annotation. Group by category if there are many. Example:

- **Reframe negativo**: "Non si tratta di X, si tratta di Y" → riscritto come affermazione diretta
- **Apertura iperbolica**: "Mi ha davvero aperto gli occhi su..." → rimossa
- **Em-dash ridondante**: usato 4 volte, sostituito con virgole o punti
- **Lista a tre elementi**: struttura forzata in "X, Y e Z" → convertita in prosa
- **Transizione morta**: "Furthermore" → rimossa
- **Verbo gonfio**: "serves as a guide" → "is a guide"
- **Metafora decorativa**: "scaffold the strategy" → "organize the strategy"
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
