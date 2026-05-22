# Research: Chapter 8 — The Dangerous Middle: When Codex Is Right and Wrong Simultaneously
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** The hardest moment in a grading tool build: Codex produces feedback that passes every handoff condition you wrote and is still pedagogically wrong.

**Research date:** 2026-05-21

**⚠️ CRITICAL EMPIRICAL UPDATE NEEDED:** TIKTOC quotes "AI grading accuracy ~50-55% with rubric, ~33% without" and "ESL and AAVE bias: documented 15-20% score discrepancies." Current literature shows higher correlations (0.86–0.93) and *worse* bias data (10.3% ESL gap at identical quality; up to 25% AAVE underperformance). Pedagogical conclusion (teacher-in-the-loop) is STRENGTHENED by current data. See Section 8.

---

## 1. Primary Sources

### Foundational papers and texts

- **Binet, Alfred. *Les idées modernes sur les enfants*. Flammarion, 1909.** "Scale is a rough guide for identifying children who need help, not a label for fixed intelligence." Intellectual core.
- **Hattie, John and Helen Timperley. "The Power of Feedback." *Review of Educational Research* 77, no. 1 (2007): 81–112.** Feedback must specify next steps. Canonical.
- **Hattie, John. *Visible Learning*. Routledge, 2008.** d = 0.73 for feedback when it specifies direction.
- **Anthropic. "How AI assistance impacts the formation of coding skills." 2026 (arXiv:2601.20245).** Three low-scoring patterns. Debugging gap.
- **Anthropic. "Anthropic Education Report" (2025).** **48.9% automation-heavy grading despite faculty rating it least effective.**
- **2024–2025 LLM grading-accuracy literature.** LLM rubric correlations 0.86–0.93:
  - Yavuz (2025), *British Journal of Educational Technology*, Wiley.
  - arXiv:2505.01035 (May 2025) — four major LLMs, rubric simplification study.
  - ACL BEA Workshop 2025 — multiple papers on LLM auto-grading.
- **2024–2026 ESL/AAVE bias literature.** The chapter's distinctive empirical contribution:
  - Stanford 2024: GPTZero false positive rates **2–4× higher** for ESL writing.
  - AI Ethics Institute 2024 (10,000+ assignments): NLP-based grading underperformed by **up to 25% on AAVE work**.
  - High-proficiency ESL essays: **10.3% lower scores** for identical human-rated quality (DeBERTa-v3).
  - Stanford analysis: error rates >30% for non-native texts.
  - arXiv:2601.16724 (Jan 2026): contrastive learning mitigation **reduces ESL disparity by 39.9%** (10.3% → 6.2%) — partial fix.

### Key empirical cases

- **Seth's "right and wrong" moment (TIKTOC opening).** Author + Seth + K-12 contributor produce.
- **The ESL student case.** Concrete: AI feedback downgrades high-proficiency ESL student because of L2 surface markers.
- **The AAVE student case.** AI flags AAVE features as errors. Documented broadly.
- **The "feedback that's accurate but generic" pattern.** Descriptive-vs-directive distinction (Hattie & Timperley 2007).

---

## 2. The Core Concept — State of the Field

### What is settled

- **LLM grading correlations are high on rubric tasks** (0.86–0.93). **TIKTOC's 50-55% is outdated.**
- **Higher correlations don't mean ready.** 7–14% disagreement concentrated in pedagogically high-stakes cases.
- **ESL/AAVE bias is measurable and significant.** 10.3% scoring gap at identical quality; up to 25% AAVE underperformance; 2–4× false-positive rates for AI-detection.
- **Effective feedback specifies next steps.** Hattie & Timperley 2007.
- **AI-generated feedback tends descriptive, not directive.** Multiple 2024–2025 studies.
- **Anthropic 48.9% finding.** Knowledge-behavior gap.

### What is disputed

- **Whether LLM grading should ever be "final word."** Book: teacher-in-the-loop because disagreement clusters in high-stakes cases.
- **Whether mitigation closes the bias gap.** Partially (39.9% reduction for ESL; not eliminated).
- **Whether "first draft, never final word" is sufficient.** Only if enforced — hooks (in Claude Code teachers book Ch 7) make enforceable; Codex equivalent is task queue + PreToolUse hook in Codex 2026.
- **Whether the narrowing principle is right scope.** TIKTOC: yes. Book defensible.

### What has changed recently (last 5 years)

- LLM grading accuracy moved from ~0.55 (2020–2022) to 0.86–0.93 (2024–2025). Pedagogical risk didn't decrease proportionally.
- ESL/AAVE bias now extensively documented.
- Mitigation approaches emerging (contrastive learning); partial fix.
- Anthropic 2025 Education Report's 48.9% finding is new and central.

---

## 3. Application Domain Examples

(Domain coverage map: Ch 8 sits in grading tool dangerous middle.)

- **High-proficiency ESL student.** Well-argued essay, non-standard preposition use. AI flags "grammar errors." Score technically correct on rubric; pedagogically wrong (10.3% gap per DeBERTa-v3).
- **AAVE student.** Clear argument with AAVE features (habitual "be," copula deletion). AI flags as errors. Score and feedback technically correct against SAE rubric; pedagogically wrong (AAVE is complete grammatical system; up to 25% underperformance).
- **Struggling student needing encouragement.** Technically weak submission representing growth. AI feedback technically accurate; teacher knows student needs scaffolded encouragement, not deficit list (Hattie & Timperley: next steps).

---

## 4. The Book's Thesis Connection

Ch 8 is empirical and moral core. Stakes highest. AI grading at scale, applied uncritically, systematically disadvantages ESL/AAVE/struggling students.

Contribution:
1. **Names the pedagogical dangerous middle.**
2. **Updates empirical foundation.** Discipline matters more, not less.
3. **Operationalizes narrowing principle.**
4. **Equity handoff condition.** "Does this feedback treat all students' language as equally valid?"

Student-supplied capacity: pedagogical and equity judgment. Cannot transfer.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: Alfred Binet (1857–1911).** Cross-series consistent with gh-copilot teacher Ch 6 and Claude Code teacher Ch 8.

Candidates:
- **Alfred Binet** (1857–1911, France). Named. French; non-USA.
- **Asa G. Hilliard III** (1933–2007, USA, educational psychologist). Cultural bias in standardized testing, especially AAVE. **Substantively more direct fit** for this chapter's AAVE content. Black scholar — strongest diversity addition.
- **Hortense Powdermaker** (1900–1970, USA, anthropologist). Embedded observation. Woman, American.

Recommendation: **consider Hilliard.** Substantive fit for AAVE bias is more direct than Binet's general warning. Cross-series consistent with Claude Code teacher book Ch 8 recommendation.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Act One + Ch 5 (capacities) + Ch 6 (Best-of-N technique) + Ch 7 (grading tool built).

### Common misconceptions to disarm
- **"Higher accuracy means safer delegation."** Opposite: disagreement clusters where judgment matters most.
- **"My rubric is unbiased."** Rubrics scoring "standard grammar" can disadvantage ESL/AAVE.
- **"Mitigation solves bias."** Partially.
- **"This is the AI's fault."** Structural; pedagogical work is teacher's.
- **"Students prefer detailed AI feedback."** Preference ≠ benefit.

### Effective instructional sequences
- **Lead with specific case.** Seth + ESL/AAVE worked examples.
- **Updated empirical anchor sidebar.** 0.86–0.93 correlation; 10.3% ESL gap; up to 25% AAVE; 48.9% automation-heavy.
- **Narrowing principle.**
- **Equity handoff condition** as apply-level exercise.

### Known failure modes
- **Anti-AI grading.** Book is pro-discipline.
- **Over-claiming bias.** Specific findings; don't generalize.
- **Sympathy theater.** Anthropic 48.9% is acknowledgment, not absolution.
- **Stale accuracy data.** TIKTOC's 50-55% is outdated. Update or lose credibility.

### What separates understanding from memorization
A reader who *understands* Ch 8 has rebuilt grading tool with narrowing principle, added enforcement (PreToolUse hook or task-queue gate), and written equity handoff condition naming ESL/AAVE risks. A reader who memorized Ch 8 recites "first draft only" without restructuring.

---

## 7. Representation and Display Research

TIKTOC specifies one figure:

- **`<!-- → [DIAGRAM: The narrowing principle.] -->`** Worked content:
  - Two paths.
  - Before: Codex generates individual student feedback (dangerous — ESL/AAVE bias, generic, accuracy-without-pedagogy).
  - After: Codex flags patterns → teacher writes individual feedback.
  - Editorial style.

Optional: **Updated grading-accuracy + bias sidebar.** Three numbers: 0.86–0.93 correlation; 10.3% ESL gap; up to 25% AAVE.

---

## 8. Open Questions and Research Gaps

- **THE LIVE ISSUE: Update TIKTOC Contested Claims table.** "50-55% with rubric" → "0.86–0.93 correlation; 7–14% disagreement clusters in pedagogically high-stakes cases."
- **THE LIVE ISSUE: Update ESL/AAVE bias data.** "15-20%" → specific 2024–2026 findings (10.3% ESL gap at identical quality; up to 25% AAVE; 2–4× false-positive rates).
- **K-12 contributor (Hard-Chapter requirement).** TIKTOC names. Author identifies.
- **The "students preferring AI feedback" tension.** Author decides framing.
- **Mitigation approaches.** Brief sidebar on contrastive learning (arXiv:2601.16724) without overstating.
- **Hilliard swap.** Strongest single diversity addition.
- **Codex equivalent of CLAUDE.md Hooks.** Codex doesn't have hooks the same way; the enforcement layer is task-queue gating + AGENTS.md negative constraints + manual review.

---

## 9. Sourcing Notes

- **Binet 1909** — Flammarion.
- **Hattie 2008 / Hattie & Timperley 2007** — Routledge / *Review of Educational Research*.
- **Anthropic RCT 2026** — anthropic.com/research/AI-assistance-coding-skills.
- **Anthropic Education Report 2025** — anthropic.com.
- **Yavuz 2025** — Wiley *BJET*.
- **arXiv:2505.01035** — open access.
- **ACL BEA 2025** — aclanthology.org/2025.bea-1.35.pdf.
- **arXiv:2601.16724** — open access; critical for this chapter.
- **Hilliard sources** if swapping: *Testing African American Students* (1991); *SBA: The Reawakening of the African Mind* (1997).
