# Research: Chapter 4 — Handoff Conditions: The Gate Between Steps
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** Not "looks good." A specific, testable condition that must be true before the next step begins. This is what separates conducting from approving.

**Research date:** 2026-05-21

---

## 1. Primary Sources

### Foundational papers and texts

- **Deming, W. Edwards. *Out of the Crisis*. MIT Press, 1986.** PDCA. "A bad system will beat a good person every time."
- **Hoare, C.A.R. "An Axiomatic Basis for Computer Programming." *CACM* 12 (1969): 576–580.** Pre/postconditions.
- **Meyer, Bertrand. "Applying 'Design by Contract.'" *IEEE Computer* 25 (1992): 40–51.** Contracts.
- **Hopper, Grace. "The Education of a Computer." *ACM Symposium*, 1952.** Done must be defined before verified.
- **Spear & Bowen. "Decoding the DNA of the Toyota Production System." *HBR*, Sep 1999.** Andon-cord.
- **OpenAI. "How OpenAI Engineers use Codex" (Dec 2025).** TIKTOC quotes: "If you've corrected Codex more than twice on the same issue, the context is cluttered. Start fresh with a more specific prompt."

### Key empirical cases

- **Teacher's "broken link three days later" (TIKTOC opening).** Codex output looked correct; approved; later finding. Real, recoverable, teaches.
- **The /clear-after-two-failed-corrections rule.** OpenAI's own prescription; the book's revert-and-respecify discipline.
- **Pixar Toy Story 2 near-deletion (1998); GitLab 2017 database deletion.** Strongest precedents for "exit 0 / completion ≠ correctness."

---

## 2. The Core Concept — State of the Field

### What is settled

- **Process completion is not correctness.** Uncontroversial.
- **Postconditions are not implied by syntactic success.** Established in formal methods.
- **Layered verification reduces error rates.** Safety-critical systems literature.

### What is disputed

- **All-build-steps-need-handoff vs. proportional.** In proportion to consequence.
- **Forward correction vs. revert.** Book: revert. Contrarian relative to incremental fixes; defensible because forward correction pollutes context.
- **Visual handoff conditions.** Some require human review; chapter must distinguish.

### What has changed recently (last 5 years)

- The 2026 Codex app's parallel-task UI changes how handoff conditions interact with multiple agents.
- "Approval-required" patterns for destructive ops standard in enterprise 2024–2026.

---

## 3. Application Domain Examples

(Domain coverage map: Ch 4 sits in class website.)

For the website, three handoff conditions:

1. **After adding a page.** Weak: "looks good." Strong: "renders on mobile (Chrome devtools iPhone preset); all links resolve; no CSS from prior pages changed (`npm run lint-html`, exit 0); new page linked from nav."
2. **After CSS change.** Weak: "no errors." Strong: "every previously-rendered page renders identically (visual diff on three pages); change appears only where intended."
3. **After deploy step.** Weak: "rsync exits 0." Strong: "server's index.html mtime within 1 minute of local; HEAD to class URL returns 200."

---

## 4. The Book's Thesis Connection

Ch 4 closes Act One. Teacher has built one deployable page with AGENTS.md, Ask/Code gate, specifications, handoff conditions. Gate 1 met.

Contribution:
1. **Operationalizes verify.**
2. **Binary acceptance threshold.**
3. **Closes Act One framework.**

Student-supplied capacity: only the teacher knows what "done" means for *their* page on *their* server.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: W. Edwards Deming (1900–1993).** Cross-series consistent.

Candidates:
- **Deming** — named. Diversity: white male American.
- **Taiichi Ohno** (1912–1990, Japan). Andon-cord. **Strongest diverse alternate.** Cross-series consistent.
- **Walter Shewhart** — PDCA originator; more academic.

Recommendation: **consider Ohno swap.** Series-wide consistency.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Ch 1–3 fully assimilated.

### Common misconceptions to disarm
- **"Looks good is a condition."** No.
- **"Forward correction works."** OpenAI itself recommends fresh start after two failed corrections.
- **"Handoff conditions are for big builds."** Proportional to consequence.

### Effective instructional sequences
- **Strong vs. weak side by side.**
- **Apply-level: teacher writes conditions for website.**
- **Revert-and-respecify drill.**

### Known failure modes
- **Test-writing advocacy.** Intent verification, not unit tests.
- **Over-formalization.**

### What separates understanding from memorization
A reader who *understands* Ch 4 has written handoff conditions for three website steps and reverted at least once. A reader who memorized Ch 4 recites "specific, testable, binary" without applying.

---

## 7. Representation and Display Research

TIKTOC specifies two figures:

- **`<!-- → [DIAGRAM: Handoff condition gate.] -->`** Step N → [handoff check] → Pass → Step N+1. Fail: revert + respecify. Editorial style.
- **`<!-- → [TABLE: Strong vs. weak handoff conditions.] -->`** Five examples for website context.

---

## 8. Open Questions and Research Gaps

- **Gate 1 acceptance criteria.** Concrete checklist at end of chapter.
- **STOP block specifics.** Foreshadow for grading tool (Ch 7) and simulation (Ch 11).
- **Visual handoff conditions.** Some require human review; distinguish.

---

## 9. Sourcing Notes

- **Deming 1986** — MIT Press; 2018 reprint.
- **Hoare 1969** — open access *CACM*.
- **Meyer 1992** — IEEE.
- **Pixar/GitLab cases** — primary sources.
- **OpenAI engineer-voice** — forum.openai.com.
