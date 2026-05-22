# Research: Chapter 6 — Best-of-N: The Verification Layer
## Codex for Teachers: A Practitioner's Guide

**Chapter one-line:** When uncertain which Codex output is correct, generate multiple responses and evaluate all of them. The selection judgment is irreducibly human.

**Research date:** 2026-05-21

**⚠️ CRITICAL FRAMING NOTE:** Best-of-N is **NOT a named user-facing UI feature** in Codex as of May 2026. The Codex app's parallel-task UI handles *multi-agent execution* (different agents on different tasks), not Best-of-N (multiple responses to the same task). The API exposes `n` parameter for parallel completions. **The chapter currently reads as if Best-of-N is a button. It isn't.** Recommendation in Section 8.

---

## 1. Primary Sources

### Foundational papers and texts

- **OpenAI. Codex documentation (developers.openai.com/codex).** Confirms parallel-task UI for multi-agent execution; does not document a user-facing "Best-of-N" mode. The OpenAI engineer-voice posts mention "review several iterations and combine parts of different responses" without naming this as "Best-of-N."
- **Simon, Herbert A. *Models of Bounded Rationality*, Volume 3. MIT Press, 1997.** Satisficing — decision-maker who searches for good-enough solution under cognitive constraints. The technique of generate-evaluate-select is satisficing made explicit.
- **Klein, Gary. *Sources of Power*. MIT Press, 1998.** Recognition-primed decision; comparing multiple candidates is RPD with explicit options.
- **Anthropic. Research papers on multi-sample evaluation and best-of-n sampling for language models (multiple, 2023–2026).** The *technique* is documented in ML literature even when not exposed as a UI feature.

### Key empirical cases

- **The teacher's "two pedagogical approaches" moment (TIKTOC opening).** Teacher has two approaches to grading-tool feedback and isn't sure which is pedagogically better. Generates both and evaluates. The pattern is the chapter.
- **The "structured vs. narrative feedback" comparison.** Concrete grading-tool example — two response styles, teacher picks based on pedagogical judgment.
- **The "I asked Codex twice in separate sessions and got two different answers" workaround.** Pre-feature manual implementation of the technique. Many teachers do this informally.

---

## 2. The Core Concept — State of the Field

### What is settled

- **Multi-sample evaluation produces better outcomes than single-sample for ambiguous tasks.** Established in ML literature.
- **The selection judgment cannot be delegated to the model.** Structural property — model has no basis to prefer one of its own outputs over another beyond likelihood.
- **The Codex app supports multi-agent parallel execution.** Confirmed for 2026.

### What is disputed

- **Whether "Best-of-N" exists as a user-facing Codex feature.** TIKTOC asserts yes; current OpenAI docs and 2026 product reporting do not confirm a named Best-of-N mode in the Codex UI. The technique is real; the *named feature* may not be. **OQ-6 is the live question.**
- **Whether the technique adds value for K-12 teacher use.** TIKTOC argues yes for judgment-intensive steps; the book's position is defensible.

### What has changed recently (last 5 years)

- The Codex app introduced parallel task execution in 2025–2026. This is closer to *agent teams* than to Best-of-N — different specialized agents on different tasks, not multiple responses to the same task.
- API `n` parameter for parallel completions has existed since early Codex; usage is developer-facing, not teacher-facing.

---

## 3. Application Domain Examples

(Domain coverage map: Ch 6 sits in grading tool.)

The chapter's worked examples must use the *technique* (generate-evaluate-select), described in a way that works regardless of whether a named feature exists:

- **Manual Best-of-N via separate sessions.** Teacher opens two Codex sessions, runs same specification, compares outputs. Operationally identical to Best-of-N at small N. Accessible to any teacher with Codex access.
- **Best-of-N via API `n` parameter** (for teachers comfortable with API access). Run a single API call requesting N completions. Compare. Select.
- **Best-of-N via the Codex app's parallel-agent UI** (if/when this becomes the analog). The chapter should describe the *workflow* rather than relying on a specific UI affordance.

For grading tool decisions where Best-of-N adds value:
- Which feedback framing serves this student population (structured vs. narrative)?
- Which architectural approach handles the rubric better (per-criterion vs. holistic)?
- Which scaffolding level matches this assignment (more or less hint)?

For tasks where it adds overhead (don't use):
- Mechanical, well-specified tasks where specification fully determines output.
- Routine code completion within an established pattern.

---

## 4. The Book's Thesis Connection

Ch 6 makes plausibility auditing scalable. PA at three candidates is more reliable than PA on one. The technique is the operational form.

Contribution:
1. **Multi-sample evaluation as verification layer.**
2. **Selection as irreducibly human work.**
3. **Best-of-N as dangerous-middle detector** (foreshadowed Ch 8): when three candidates all produce the same pedagogically problematic framing, the problem is the specification, not the response.

Student-supplied capacity: the selection. Only the teacher can judge which output serves the classroom.

---

## 5. The AI Wayback Machine — Candidate Figures

**TIKTOC names: Herbert Simon (1916–2001).** Strong fit. **BUT Herbert Simon is also TIKTOC's Ch 9 Wayback figure (decomposition for task queue).** Same-figure double-booking should be resolved.

Candidates:
- **Herbert Simon** (1916–2001, USA, polymath). Named. Satisficing. Substantive fit excellent. Diversity: white male American.
- **Gary Klein** (born 1944, USA, cognitive scientist). RPD model — comparing multiple candidates. Direct fit; pre-2000 work published. Same diversity profile.
- **Donald Schön** (1930–1997, USA, philosopher/planner). Already TIKTOC's Ch 7, 11, 14 figure. **AVOID** — already over-booked.

Recommendation: **swap Ch 6 to Gary Klein (RPD), keep Simon at Ch 9 (decomposition for task queue).** Klein's RPD is a closer substantive fit for Best-of-N than Simon's satisficing, and frees Simon for Ch 9 where decomposition is the precise frame.

---

## 6. Pedagogical Delivery Research

### Prior knowledge required
Ch 5 (capacities). Teacher building grading tool and confronting judgment-intensive steps.

### Common misconceptions to disarm
- **"Best-of-N is a button."** As of May 2026, not in Codex UI. Technique, not feature.
- **"More candidates = better."** Diminishing returns; three is usually sufficient for student-scale work.
- **"Best-of-N for everything."** No. Adds value for judgment-intensive steps; overhead for mechanical.
- **"The AI can pick the best."** No. Selection is the supervisory work.

### Effective instructional sequences
- **Frame as technique, not feature.** Works regardless of UI affordance.
- **Worked example: two pedagogical approaches.** Concrete grading-tool case.
- **The "Best-of-N as dangerous-middle detector" insight.** When all candidates share the problem, the spec is wrong.

### Known failure modes
- **The chapter as feature tutorial.** If a named feature doesn't exist, the chapter becomes hollow. Reframe as technique.
- **Over-claiming Best-of-N benefit.** Mechanical tasks: skip. Judgment tasks: yes.
- **Codex-specific overhead.** Without a UI feature, the technique requires manual session-switching or API access — overhead the chapter must acknowledge.

### What separates understanding from memorization
A reader who *understands* Ch 6 has used the generate-evaluate-select technique on a grading-tool decision and can articulate why the selection couldn't be delegated. A reader who memorized Ch 6 recites "Best-of-N" without applying.

---

## 7. Representation and Display Research

TIKTOC specifies one figure:

- **`<!-- → [DIAGRAM: Best-of-N pattern.] -->`** Worked content:
  - Specification → [N parallel Codex responses, however generated].
  - Human evaluates all N.
  - Selects one (optionally combines parts).
  - The selection is the supervisory judgment.
  - Editorial style.

The diagram should NOT show a Codex UI button. Show the *pattern*, not the *interface*.

---

## 8. Open Questions and Research Gaps

- **THE LIVE QUESTION (TIKTOC OQ-6): Best-of-N availability.** As of May 2026: not a named user-facing feature in Codex. Three options:
  1. **Reframe Ch 6 as "Generate-Evaluate-Select: The Verification Technique."** Drop "Best-of-N" as a named feature; teach the pattern using manual session-switching or API. Most defensible.
  2. **Keep "Best-of-N" terminology but be explicit about implementation.** Teach via API `n` parameter or manual sessions. Acknowledge no UI button.
  3. **Wait for a named Codex feature.** Defer Ch 6 to second edition. Loses a chapter in v1.
  Recommendation: **option 1.** The technique is the content; the name is overhead at student/teacher scale.
- **Multi-agent Codex app parallel execution.** Different concept (different agents on different tasks). Worth a sidebar distinction so readers don't confuse the two.
- **API access for teachers.** Most K-12 teachers won't have API access. The chapter should emphasize the manual session-switching workflow as the accessible path.

---

## 9. Sourcing Notes

- **OpenAI Codex docs** — developers.openai.com/codex. Verify "Best-of-N" status at press; current as of May 2026: not a named UI feature.
- **Simon 1997** *Models of Bounded Rationality* — MIT Press; satisficing.
- **Klein 1998** — trade book; academic papers (1989, 1993) for depth.
- **Anthropic research papers on best-of-n sampling** — multiple; cite a representative one.
