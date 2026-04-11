The shape of this wiki is based on [[llm-wiki]].
# Intelligence Wiki — Schema

This wiki explores **how the brain learns** — the biological mechanisms of intelligence, learning, and memory. It is maintained by an LLM following the conventions below. The human curates sources, directs analysis, and asks questions. The LLM does all writing, cross-referencing, and maintenance.

## Scope

**In scope**: Biological learning mechanisms, synaptic plasticity, memory systems, neural circuits, brain development, cognitive processes (attention, metacognition, transfer), computational neuroscience, experimental methods in neuroscience.

**Out of scope**: Pure AI/ML (reference only as analogy to biological systems), clinical neurology/psychiatry, philosophy of mind (unless directly relevant to a biological mechanism).

### Organizing principle

The wiki is organized around a specific thesis: **the most biologically grounded route to understanding intelligence begins with closed-loop sensorimotor control.** Memory, learning, and cognition are understood as extensions that improve control over longer timescales, more latent variables, and more counterfactual worlds — not as separate faculties bolted on top.

When ingesting sources or synthesizing across pages, ask: *what does this tell us about control, and how does it extend the reach of that control?* Sources that speak to sensorimotor loops, feedback control, or the progression from immediate reactive control to longer-horizon planning and abstraction are central. Sources about plasticity, memory, or representation should be connected back to how they serve the organism's ability to act effectively.

A related working hypothesis motivates the evolutionary dimension: genes encode behavior not by specifying circuits directly, but by modifying neurons' nonlinear feedback control algorithms, producing conserved macroscopic dynamical structures (e.g., limit cycle attractors for locomotion) with high probability despite unique microscopic configurations. This is the control-theoretic reading of [[Degeneracy]].

---

## Directory Layout

```
raw/                    # Layer 1: Immutable source documents — NEVER modify these
  papers/               # Academic papers (PDF or markdown)
  articles/             # Web articles, blog posts
  books/                # Book chapters, excerpts
  assets/               # Images, figures, diagrams
wiki/                   # Layer 2: LLM-generated wiki pages
  sources/              # One summary page per ingested source
  topics/               # Concepts, mechanisms, theories, methods
  brain-regions/        # Anatomical / structural pages
  people/               # Researchers, labs, institutions
  analyses/             # Comparisons, explorations, filed query responses
index.md                # Content catalog — read this first when answering queries
log.md                  # Append-only chronological activity log
overview.md             # Evolving high-level synthesis of everything in the wiki
open-questions.md       # Tracked unknowns and research gaps
```

---

## Page Types & Frontmatter

Every wiki page has YAML frontmatter. The `type` field determines the page category.

### Source (`wiki/sources/`)

Filename: `{first-author}-{year}-{short-descriptor}.md` (e.g., `kandel-2001-molecular-memory.md`)

```yaml
---
title: "Paper Title"
type: source
source_type: paper        # paper | article | book | lecture
authors:
  - "First Author"
  - "Second Author"
year: 2024
doi: "10.1234/example"
tags: [synaptic-plasticity, hippocampus]
date_ingested: 2026-04-10
key_finding: "One-line summary of the main finding"
---
```

**Required sections**: Overview, Key Findings, Methods, Implications, Connections to Existing Knowledge, Open Questions Raised.

Link back to the raw file: `[PDF](../../raw/papers/filename.pdf)` or `[Source](../../raw/articles/filename.md)`.

### Concept (`wiki/topics/`)

```yaml
---
title: "Synaptic Plasticity"
type: concept
aliases: ["synaptic modification"]
tags: [plasticity, learning]
source_count: 0
last_updated: 2026-04-10
confidence: established    # established | emerging | contested
---
```

### Mechanism (`wiki/topics/`)

```yaml
---
title: "Long-Term Potentiation"
type: mechanism
aliases: ["LTP"]
tags: [plasticity, synapse, glutamate]
source_count: 0
last_updated: 2026-04-10
level: cellular            # molecular | cellular | circuit | systems
---
```

### Theory (`wiki/topics/`)

```yaml
---
title: "Hebbian Learning"
type: theory
aliases: ["Hebb's rule", "fire together wire together"]
tags: [learning-rule, plasticity]
source_count: 0
last_updated: 2026-04-10
status: established        # established | emerging | contested | historical
---
```

### Method (`wiki/topics/`)

```yaml
---
title: "Patch Clamp Recording"
type: method
aliases: ["patch clamp", "whole-cell recording"]
tags: [electrophysiology, recording]
source_count: 0
last_updated: 2026-04-10
technique_type: recording  # recording | imaging | manipulation | computational
---
```

### Brain Region (`wiki/brain-regions/`)

```yaml
---
title: "Hippocampus"
type: brain-region
aliases: ["hippocampal formation"]
tags: [limbic-system, memory, spatial-navigation]
source_count: 0
last_updated: 2026-04-10
---
```

### Person (`wiki/people/`)

```yaml
---
title: "Eric Kandel"
type: person
tags: [memory, aplysia, molecular-biology]
affiliation: "Columbia University"
source_count: 0
last_updated: 2026-04-10
---
```

### Comparison (`wiki/analyses/`)

```yaml
---
title: "LTP vs LTD"
type: comparison
tags: [plasticity, synaptic]
source_count: 0
last_updated: 2026-04-10
---
```

### Exploration (`wiki/analyses/`)

```yaml
---
title: "How does sleep affect memory consolidation?"
type: exploration
tags: [sleep, memory, consolidation]
date_created: 2026-04-10
prompted_by: "user query"
---
```

---

## Naming Conventions

- **Filenames**: kebab-case (`long-term-potentiation.md`)
- **Titles** (in frontmatter): Title Case (`Long-Term Potentiation`)
- **Source pages**: `{first-author}-{year}-{short-descriptor}.md`
- **Tags**: kebab-case, prefer broad over narrow

---

## Linking Conventions

- Use Obsidian `[[wikilinks]]` for all cross-references
- Link on first mention in each section, not every mention
- Link generously — over-linking is better than under-linking
- Use `[[Page Name|display text]]` when the page name doesn't read naturally in prose

---

## Evidence & Citation Standards

- Every factual claim should be traceable to a source page
- Source pages cite the original document (DOI, URL, or raw file link)
- When sources conflict, note both positions and flag the contradiction explicitly
- Use hedging language proportional to evidence strength:
  - Strong: "X is well-established", "strongly supported by [[source]]"
  - Moderate: "X is suggested by [[source]]", "evidence indicates"
  - Weak: "preliminary evidence from [[source]] suggests", "one study found"
  - Conflicting: "[[source-a]] found X, but [[source-b]] reports Y"
- Every wiki page has a **Sources** section at the bottom listing which source pages informed it

---

## Workflows

### Ingest

Triggered when the user adds a source to `raw/` and asks to process it.

1. **Read** the source document fully
2. **Discuss** key findings and takeaways with the user — what's interesting, what's surprising, how it connects to existing knowledge
3. **Create source summary** in `wiki/sources/` with all required sections
4. **Update or create wiki pages** for each major concept, mechanism, theory, brain region, method, or person mentioned:
   - If page exists → integrate new information, add source to Sources section, increment `source_count`, update `last_updated`
   - If page doesn't exist → create it with initial content from this source
5. **Update `index.md`** — add entries for any new pages
6. **Append to `log.md`** — one entry with date, action type, and description
7. **Update `overview.md`** if the source materially changes the overall synthesis
8. **Update `open-questions.md`** if the source raises new questions or resolves existing ones

### Query

When the user asks a question about the wiki's domain.

1. Read `index.md` to identify relevant pages
2. Read those pages, follow links as needed for deeper context
3. Synthesize an answer with `[[wikilinks]]` to relevant pages
4. If the answer is substantial and worth preserving → offer to file it as an exploration page in `wiki/analyses/`

### Lint

Periodic health check — run when the user asks or after significant ingests.

1. Orphan pages — wiki pages with no inbound links
2. Red links — `[[wikilinks]]` that point to pages that don't exist yet
3. Stale pages — low `source_count` or old `last_updated`
4. Contradictions — claims on one page that conflict with another
5. Missing cross-references — pages that should link to each other but don't
6. Gaps — important concepts mentioned in passing but lacking their own page
7. Report findings, suggest fixes, and suggest new sources to seek out

---

## Page Content Guidelines

- Write in clear, precise prose — academic but accessible
- Lead each page with a 1-2 sentence definition or summary
- Use `## Heading` hierarchy consistently: H2 for major sections, H3 for subsections
- Keep pages focused — if a section grows large, consider splitting it into its own page
- When a topic has both biological and AI/ML parallels, note the analogy briefly but keep focus on the biological side
