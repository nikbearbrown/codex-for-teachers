# Research: Chapter 3 — From Prompts to Specifications: Ask Mode, Code Mode, and the First Build
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** Ask Mode is for planning. Code Mode is for executing. Nothing goes to Code Mode without a reviewed plan. The class website is the first build.

**Research date:** 2026-05-21

---

## 1. Primary Sources

### Foundational papers and texts

- **Pólya, George. *How to Solve It*. Princeton University Press, 1945.** Understand → plan → execute → look back. The Ask Mode / Code Mode gate is Pólya at scale.
- **Brooks, Frederick P. "No Silver Bullet." *IEEE Computer* 20, no. 4 (1987): 10–19.** Essential difficulty: specification.
- **Lovelace, Ada. *Notes on the Analytical Engine* (1843), Note G.** First program; precise specification.
- **Liskov, Barbara H. and Jeannette M. Wing. "A Behavioral Notion of Subtyping." *ACM TOPLAS* 16 (1994): 1811–1841.** Contract specification.
- **Wirth, Niklaus. "Program Development by Stepwise Refinement." *CACM* 14 (1971): 221–227.** Specification as refinement.
- **OpenAI. "Codex Prompting Guide" (developers.openai.com/cookbook/examples/gpt-5/codex_prompting_guide).** Vendor authority for specification structure.
- **OpenAI. "How OpenAI Engineers use Codex" (forum.openai.com, Dec 2025).** TIKTOC quotes the Ask-then-Code prescription explicitly.

### Key empirical cases

- **Teacher's first page (TIKTOC pebble).** Course home page with syllabus. One Ask Mode plan, one specification, review, Code Mode, verify.
- **Same task, two prompts.** TIKTOC's pattern: weak prompt vs. five-element specification.
- **The Ask Mode revision moment.** Teacher corrects one assumption in Codex's plan before approving. Concrete example.

---

## 2. The Core Concept — State of the Field

### What is settled

- **Specification clarity correlates with output quality.** Broad consensus.
- **Ask Mode / Code Mode separation is current Codex UX.** Verified May 2026.
- **Negative constraints matter.** "Do not touch X" is not implied.
- **Feedback-mechanism prompts produce better results.** OpenAI's own guidance.

### What is disputed

- **Formality level.** Structured XML vs. natural-language. Book recommends simple five-element; defensible.
- **Plan-mode-by-default vs. per-task.** TIKTOC implies for non-trivial.
- **Examples in prompts.** Useful for complex; overhead for routine.

### What has changed recently (last 5 years)

- 2025–2026 Codex handles structured prompts more reliably than 2023.
- Ask Mode formalization (2024+) institutionalized what experienced engineers were doing manually.

---

## 3. Application Domain Examples

(Domain coverage map: Ch 3 sits in class website.)

For the website's first page, the five elements:
1. **Operation:** Create new file `src/syllabus.html`.
2. **Invariants:** No existing files modified; existing CSS unchanged; same head/nav template as `src/index.html`.
3. **Context:** AGENTS.md sections — stack (vanilla HTML/CSS), code style (semantic HTML5), verification (npm run lint-html).
4. **Output format:** Complete `src/syllabus.html` rendering syllabus structure. Linked from index.html nav.
5. **Negative constraint:** No JavaScript. No new dependencies. No CSS changes.

Same task as one-line prompt produces generic; specification produces project-fit.

---

## 4. The Book's Thesis Connection

Ch 3 is first deployable artifact. Teacher has AGENTS.md (Ch 2); now writes specifications inside the Ask/Code gate.

Contribution:
1. **Specification bridges intent and code.**
2. **Five elements operationalize supervisory work** (foreshadowed; full Ch 5).
3. **First page works.** Deployable by end of Ch 3.

Student-supplied capacity: every element is information Codex lacks.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: George Pólya (1887–1985).** Cross-series consistent.

Candidates:
- **Pólya** — named. Hungarian-American; adds non-USA. Substantive fit excellent.
- **Lovelace** (cross-series Ch 8 candidate).
- **Hopper** (cross-series Ch 9 candidate).

Recommendation: keep Pólya.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Ch 1 (gate) + Ch 2 (AGENTS.md).

### Common misconceptions to disarm
- **"Specifications for big builds."** Any operation that fails silently.
- **"More words = better."** Precision per element.
- **"I'll edit the generated code."** Sometimes; not in dangerous middle.

### Effective instructional sequences
- **Build first page live.**
- **Show Ask Mode revision moment.**
- **Before/after pairs.**

### Known failure modes
- **Specification as boilerplate.**
- **Over-specification of trivial commands.**

### What separates understanding from memorization
A reader who *understands* Ch 3 has built first page using five-element specification through Ask Mode review. A reader who memorized Ch 3 recites elements without producing tailored spec.

---

## 7. Representation and Display Research

TIKTOC specifies two figures:

- **`<!-- → [DIAGRAM: Ask Mode / Code Mode sequence.] -->`** Ask Mode: interrogate → plan → review → approve. Gate. Code Mode: specification → execute → verify. Editorial style.
- **`<!-- → [TABLE: Prompt vs. specification.] -->`** Five-row format for website task.

---

## 8. Open Questions and Research Gaps

- **Dry-run alternatives for static-site builds.** Verification protocol when no `--dry-run`.
- **Ask Mode UX evolution.** Verify terminology at press.

---

## 9. Sourcing Notes

- **Pólya 1945** — Princeton.
- **Brooks 1987** — IEEE.
- **Lovelace 1843** — scholarly editions.
- **OpenAI prompting guide + engineer-voice posts** — current URLs at press.
