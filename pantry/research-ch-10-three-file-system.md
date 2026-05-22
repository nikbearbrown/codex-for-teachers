# Research: Chapter 10 — The Three-File System: Intent, Constitution, State
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** Before Codex enters Code Mode on the simulation, three files define everything. The Intent Layer is human, always.

**Research date:** 2026-05-21

---

## 1. Primary Sources

### Foundational papers and texts

- **Mies van der Rohe, Ludwig.** "Less is more" attributed; from lectures and writings 1920s–1960s. **Note: attribution is aphoristic; for precise citation, use MoMA *Mies van der Rohe Centennial Exhibition* catalog (1986) or specific lecture transcripts.**
- **Alexander, Christopher. *A Pattern Language*. Oxford, 1977.** Patterns as nested constraints.
- **Bear Brown, Nik. *Brutalist Design System*. brutalist.art.** Central operational reference. **Author's own work; chapter must be transparent.**
- **DESIGN.md ecosystem.** designmd.app, getdesign.md, github.com/VoltAgent/awesome-design-md. 2025–2026 broader ecosystem; Brutalist is one entrant.
- **LeWitt, Sol. "Sentences on Conceptual Art" (1969).** Author who holds intent and writes instruction is author. Foundational for Intent Layer.

### Key empirical cases

- **Teacher's "build me a sorting simulator" failure (TIKTOC opening).** One-line prompt; Codex builds something; color scheme wrong, interaction model wrong, scaffolding missing. Teacher didn't draw line.
- **Teacher's first three files.** All populated before Code Mode. Author produces real examples.
- **45-minute scope test.** TIKTOC's forcing function.

---

## 2. The Core Concept — State of the Field

### What is settled

- **AI-context files improve generated output.** 2024–2026 practitioner literature.
- **Separating intent/constitution/state reduces drift.** Software architecture + design literature.
- **Brutalist is one operational choice.** designmd.app catalogs 454 design systems.

### What is disputed

- **Three files vs. fewer or more.** Two-file teams exist; four-file (with SKILL.md) exists. Book commits to three.
- **Whether Intent Layer is off-limits to Codex.** TIKTOC: yes. Defensible.
- **200-line limit per file.** AGENTS.md-documented; DESIGN.md/PROJECT.md not formally bound. Book extends.

### What has changed recently (last 5 years)

- 2024–2026 DESIGN.md ecosystem is institutional support.
- Codex 2026 supports subdirectory AGENTS.md, which interacts with the three-file system (the simulation folder can have its own AGENTS.md).

---

## 3. Application Domain Examples

(Domain coverage map: Ch 10 sits in simulation.)

For sorting-algorithm simulation (working example pending OQ-1 resolution):

**AGENTS.md (Technical Constitution):**
- Stack: vanilla HTML/CSS/JS.
- Structure: `index.html`, `simulation.css`, `simulation.js`.
- Naming: kebab-case IDs; camelCase JS.
- Never touch without instruction: anything outside simulation directory; class website's shared CSS.
- Verification: opens in Chromium with no console errors; works on mobile breakpoint.

**DESIGN.md (Visual Constitution):**
- Color (six max): `--background: #f5f5f0` (warm white); `--ink: #1a1a1a` (near-black); `--accent: #c97a3a` (compared); `--target: #3a7ac9` (placed); `--rule: #999999` (axis); `--highlight: #f0d843` (sorted region).
- Typography: monospace for numerics; sans-serif for labels. No serif. No script.
- Interaction: single click step forward; long click step backward; arrow keys fine control. **Never:** drag-and-drop; hover-only states; hidden controls.
- Accessibility: keyboard-navigable; screen-reader labels; min 16px.

**PROJECT.md (Project State):**

Layer 1 — Intent (human, never overwritten):
- What this simulation is: interactive bubble sort visualization showing O(n²).
- What student should understand: comparison-based sorts have simplicity-efficiency tradeoff; small changes cascade.
- What questions it answers / refuses to answer.
- Tone: matter-of-fact, slightly playful; no jargon.

Layer 2 — Technical State (Codex layer):
- What is built / pending / generation log / open technical questions.

---

## 4. The Book's Thesis Connection

Ch 10 opens Act Three. Design work explicit before generation begins. Most simulation failures are intent failures.

Contribution:
1. Names the design work.
2. Three files = three concerns separated.
3. Brutalist governing principle.
4. 45-minute scope test.

Student-supplied capacity: Intent Layer is irreducibly teacher's.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: Mies van der Rohe (1886–1969).** Substantive fit moderate (aphoristic).

Candidates:
- **Mies** — named. Diversity: white male German-American.
- **Eileen Gray** (1878–1976, Ireland/France). Total design. **Strongest diverse alternate.** Woman, Irish-French.
- **Lina Bo Bardi** (1914–1992, Italy/Brazil). Functional design with social purpose. Diversity: Italian-Brazilian woman.
- **Sol LeWitt** (1928–2007, USA). Direct fit for Intent Layer concept.

Recommendation: **consider Eileen Gray.** Total-design approach maps onto three-file system more precisely than Mies's aphoristic philosophy. Strong diversity addition.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Act One + Act Two (AGENTS.md, Ask/Code, capacities, task queue).

### Common misconceptions to disarm
- **"Three files too much for small simulation."** 45-minute test forces appropriate scope.
- **"DESIGN.md is for designers."** Anyone with visual output needs design decisions.
- **"Codex can figure out Intent."** No. Irreducibly human.
- **"I'll iterate during build."** No. Write first; refine if needed. Iteration during generation is forward correction (Ch 4 warns against).

### Effective instructional sequences
- **Write three files live.**
- **45-minute test as forcing function.**
- **All three files for worked example.** Sorting simulation.
- **brutalist.art transparency.** Be honest.

### Known failure modes
- **Brutalist evangelism.** Teach principles; let readers adopt.
- **brutalist.art as authority.** Author should be honest.
- **DESIGN.md fetishism.** Six colors is a constraint, not a religion.

### What separates understanding from memorization
A reader who *understands* Ch 10 has written three files in under 45 minutes, identifies which file each decision belongs to, recognizes Intent Layer is theirs. A reader who memorized Ch 10 recites three-file structure without producing usable files.

---

## 7. Representation and Display Research

TIKTOC specifies two figures:

- **`<!-- → [DIAGRAM: Three-file system as concentric / nested.] -->`** Outer: AGENTS.md. Middle: DESIGN.md. Inner: PROJECT.md (Intent Layer human, always). Editorial style.
- **`<!-- → [TABLE: Three-file system.] -->`** File / contents / who writes / when it changes.

---

## 8. Open Questions and Research Gaps

- **brutalist.art transparency.** Be honest about authorship.
- **Eileen Gray vs. Mies swap.** Author's call.
- **Simulation domain (OQ-1).** Most acute here.
- **Three-file vs. four-file.** Book commits to three.

---

## 9. Sourcing Notes

- **Mies attribution** — careful; MoMA centennial (1986) or specific lectures.
- **Alexander 1977** — Oxford.
- **brutalist.art** — author's own.
- **DESIGN.md ecosystem** — designmd.app, getdesign.md.
- **LeWitt 1969** — open access via 0–9 archives.
- **Eileen Gray** if swapping: Adam, *Eileen Gray* (1987); Pompidou catalog (2013).
