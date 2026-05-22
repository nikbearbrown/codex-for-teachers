# Chapter 6 — Generate, Evaluate, Select: The Verification Technique

> When uncertain which Codex output is correct, generate multiple responses and evaluate all of them. The selection judgment is irreducibly human.

---

> **A note on the chapter's name.** This chapter was originally drafted as *Best-of-N: The Verification Layer.* Best-of-N is the term used in ML literature for sampling multiple responses and choosing among them, and OpenAI engineers occasionally use it in retrospectives. **It is not a named user-facing feature in Codex as of mid-2026.** The technique is real and worth practicing; the feature, by that name, does not exist as a button you press. The chapter therefore teaches the *technique* — generate, evaluate, select — under a name that describes what you actually do. If the term Best-of-N becomes a named Codex affordance in a later version, this chapter still works; you will just have a button instead of a manual procedure.

---

## Learning outcomes

1. **(Understand)** Explain what generate-evaluate-select is and why the selection judgment cannot be delegated to Codex.
2. **(Apply)** Use the technique on a grading-tool task where two reasonable approaches exist.
3. **(Analyze)** Distinguish tasks where the technique adds value from tasks where a single well-specified prompt is sufficient.

---

## Opening

You are mid-build on the grading tool. You have reached the step where Codex generates the first-draft feedback paragraph. You have a clean specification. You run it.

Codex returns a response. The feedback is competent. It addresses the rubric criteria. It is in the second person. It does not generate a grade. It passes every handoff condition you wrote.

You read it carefully and you cannot decide whether it is *right*.

The wrongness, if it is wrong, is in the *framing*. The response is structured as a deficit list — three things the student did not do. You could also imagine a version structured as a strengths-and-next-steps list — two things working well, two things to improve next. Both would be pedagogically defensible. The choice between them depends on what you believe about this student population, this assignment, this point in the semester.

You cannot decide because you do not have enough material to compare. One output is not a choice; it is a default.

So you generate two more. Same prompt; same Codex; three separate responses. Now you can compare.

The deficit-list version is the one Codex returned first. The second is a more conversational strengths-and-next-steps. The third is a hybrid — it names one strength up front, then walks through the rubric. You read all three. You select the third. You note in your build log *why* you selected it: because your students this year are in the second half of a difficult semester and the strength-first opening will reduce defensiveness without losing the rubric coverage. You write the selection reasoning down because, when you teach this discipline in Chapter 13, the reasoning is the lesson.

The technique that just happened — generate multiple, evaluate, select — is the chapter.

<!-- → [DIAGRAM: Generate-Evaluate-Select pattern. Specification → [N parallel Codex responses, however generated]. Human evaluates all N. Selects one (optionally combines parts). The selection is the supervisory judgment. Editorial style.] -->

---

## What the technique is

You write a specification. You run it. You get one response.

Then you run the same specification *again*, in a fresh session — `/clear` first, or open a new Codex tab. You get a second response. You run it a third time. You get a third.

You read all three. You compare them. You select one. You note why.

That is it.

The technique works because of a property of language models: they are *stochastic*. Two runs of the same prompt produce two different responses, sampling from the model's space of plausible outputs. For specifications where the right answer is genuinely determined (e.g., "compute the factorial of N"), the responses will be near-identical and the comparison adds nothing. For specifications where multiple reasonable answers exist (e.g., "draft a paragraph of feedback for a student missing three rubric criteria"), the responses *will* differ — sometimes subtly, sometimes substantially — and the comparison gives you material to exercise interpretive judgment.

The selection step is where the supervisory work happens. You are comparing the responses against domain knowledge that did not enter any of the prompts — what you know about your students, your rubric, your pedagogical goals for this unit. The model has no way to do this comparison; it produced the candidates by sampling. You are the only one in the loop who can read them as candidates for *this* situation.

---

## When to use it (and when not)

The technique is valuable when the right answer requires judgment that you cannot fully specify upfront. It is overhead when the right answer is determined by the specification.

**Use generate-evaluate-select for:**

- *Pedagogical framing decisions* in grading-tool output: deficit vs. strengths-based vs. hybrid feedback structures.
- *Architectural choices* in your build where two reasonable approaches exist: per-criterion processing vs. holistic processing of student submissions.
- *Visual/aesthetic decisions* in your Act Three simulation (Chapter 10–11): which color combination, which interaction model, which animation style.
- *Tone and voice* in any teacher-facing or student-facing text Codex generates.
- *Scaffolding level* in feedback or instructional output: how much hint to give for this concept and this student population.

**Skip generate-evaluate-select for:**

- Mechanical tasks fully determined by the specification.
- Routine completion within an established pattern.
- Bug fixes with a single right answer.
- Tasks where the specification is so tight that all three responses would be near-identical.

The rule of thumb: if you can imagine writing a single handoff condition that the right answer must meet and the wrong answer fails, you do not need this technique. The handoff condition does the work. If you find yourself struggling to write the handoff condition — because the criterion is "what would work pedagogically for this student population," which is hard to formalize — then generate-evaluate-select is the discipline for that step.

---

## How to do it, mechanically

Three operational paths.

**Path 1: Manual, separate sessions.** The accessible-to-any-teacher version. Run the same specification in three separate Codex sessions (use `/clear` between runs in the CLI, or open new tabs in the app). Compare the three outputs in a side-by-side. Select. This is slow but works on any plan.

**Path 2: Via the API `n` parameter.** If you have Codex API access, the `n` parameter on chat completions requests N parallel responses to the same prompt. Faster; requires API setup. Most K-12 teachers will not have this configured; the manual path is the realistic option.

**Path 3: Codex app multi-agent UI** (with caveats). The 2026 Codex app's parallel-task UI is built around *agent teams* — different specialized agents on different tasks. This is different from generate-evaluate-select, which wants multiple responses to the *same* task. The app's UI can be used for the technique by running the same prompt through multiple agents, but this is not what the UI is optimized for. As of mid-2026, manual session-switching remains the cleanest implementation for individual teachers.

The discipline does not depend on the path. The discipline is: generate at least three responses; evaluate them against pedagogical (not technical) criteria; select; record the selection reasoning.

---

## Worked example: the feedback-framing decision

The grading tool's first-draft feedback step, run with the technique.

**Specification** (abbreviated):

> Operation: Generate a first-draft feedback paragraph (second person, ~80 words) for the attached student submission. Invariants: No numeric grade. References at least two specific rubric criteria. Output format: plain markdown. Negative constraint: Do not address the student by name; do not assume prior knowledge of the rubric.

**Response 1** (deficit list):

> *"Your submission did not include the required `Methodology` section. The `Results` section is present but does not address the criterion of statistical significance. The `Discussion` section relies on assertions rather than evidence from the data. Revisit each of these areas using the rubric handout for guidance."*

**Response 2** (strengths-and-next-steps):

> *"Your `Introduction` is well-framed and sets up the question clearly. The data collection in `Methods` shows careful work. Two next steps: add a `Discussion` section that grounds your conclusions in your own data, and check whether your `Results` section addresses the rubric's statistical-significance criterion."*

**Response 3** (hybrid):

> *"Your introduction frames the question well and the methods section shows you took the data collection seriously. Working through the rest: the `Results` section needs the statistical-significance treatment described in the rubric, and the `Discussion` section is doing more asserting than evidencing — go back to your data and let it drive what you claim. The structure is there; the analytical depth is what to add next."*

You read all three. You note:

- Response 1: covers the rubric thoroughly; the deficit framing will likely produce defensiveness in a struggling student at this point in the semester.
- Response 2: starts strong; the strengths read slightly thin (the introduction was actually a baseline expectation, not a particular strength).
- Response 3: hybrid; the analytical-depth phrase at the end gives the student a concrete next move; the framing acknowledges work without overpraising.

You select Response 3. You revise it slightly (the *"working through the rest"* phrasing is yours, not Codex's, and you would not have written it). You note in your build log: *"Selected Response 3 for the hybrid framing. The strengths-first opening reduces defensiveness; the closing phrase ('the structure is there; the analytical depth is what to add next') gives the student a concrete improvement target. This was the supervisory call; would not have made the selection without the comparison."*

That is the discipline.

**The lesson:** when the right answer requires interpretive judgment, generate-evaluate-select forces you to *exercise* the judgment rather than default to whichever response Codex happened to return first.

**The limit:** the technique does not catch the case where *all three responses share the same pedagogically wrong framing*. If every candidate is deficit-structured and the right answer requires a fundamentally different approach the model is not sampling, the comparison just confirms a shared wrong frame. This is **Best-of-N as dangerous-middle detector** (Chapter 8): when all candidates exhibit the same problem, the spec is wrong, not the response.

---

## Common misconceptions

**"Best-of-N is a button in Codex."** As of mid-2026, no. The technique is real; the named feature isn't. Manual session-switching is the realistic implementation for K-12 teachers.

**"More candidates = better selection."** Diminishing returns past three. Three candidates is enough to see variation. Five gives slightly more variation; the marginal value of the fourth and fifth candidate is usually less than the additional cost of reading them.

**"Generate-evaluate-select for everything."** No. Mechanical tasks waste the overhead. Use it for judgment-intensive steps where the right answer depends on something not in the specification.

**"The AI can pick the best response."** Asking Codex to pick the best of its own three candidates produces a fourth response, not a selection — and the fourth response will often be a synthesis that smooths out exactly the trade-off you needed to see. The selection has to be yours.

**"My evaluations are subjective; they don't add value."** Your evaluations encode domain knowledge the model does not have. That is not subjectivity; it is exactly the supervisory work the conducting framework is built around. Your selection on the grading-tool feedback is informed by knowing your students, your rubric, your pedagogical goals. Codex does not know any of this.

---

## Exercises

1. **(Apply)** Use generate-evaluate-select on one step of your grading-tool build where you have been undecided about the right approach. Generate three responses. Document which you chose and why. The reasoning is the exercise.

2. **(Analyze)** Review three Codex responses (provided, or from your own session) to the same grading task. Which would you select for your classroom? What specific supervisory capacity (Chapter 5) did you exercise to decide?

3. **(Evaluate)** Name two tasks in your current build where the technique adds value. Name two where it would be overhead. Explain the difference.

---

## Classroom activity

Have students use the technique on a build task where two reasonable approaches exist (designing an API for a small tool, choosing a data structure for a simulation, framing the user-facing copy for an app). They generate three responses. They evaluate. They select. They document *why* — and that documentation is what is peer-reviewed, not the code.

This activity maps to Chapter 6 (*Best-of-N* in Codex student book Ch 9 work) or its functional equivalent in the students book — the discipline of evaluating multiple candidates rather than accepting the first one. Cross-reference your build experience this chapter when you teach it.

---

## Links

- OpenAI Codex documentation: [developers.openai.com/codex](https://developers.openai.com/codex)
- Anthropic research on sampling and selection in language models (general background): [anthropic.com/research](https://www.anthropic.com/research) [verify — confirm specific paper citation at press]

---

## What would change my mind

The chapter stakes a structural claim: that **the selection judgment in generate-evaluate-select cannot reliably be performed by the model itself**. If a model release demonstrated reliable cross-candidate evaluation — meaning, given three of its own outputs, the model could consistently identify the one that best matched a pedagogical criterion it had not been trained on — the technique would become partially automatable. The human selection would remain valuable for cases where the criterion is genuinely domain-specific; routine framing decisions could be delegated.

I do not expect this on the 2027–2028 timeline. If wrong, the chapter's prescription becomes "use the technique on the genuinely domain-specific cases; let the model handle routine framing."

---

## Still puzzling

- **The exact threshold for "judgment-intensive."** The chapter draws the line between mechanical and judgment-intensive tasks, but the line is fuzzy. Practitioners disagree. A future edition may revise the heuristic.

- **Stylistic biases across candidates.** If Codex is systematically biased toward certain framings (e.g., consistently producing deficit-list feedback as the first response), the three candidates may share the bias even when the model is technically sampling. Generate-evaluate-select detects bias only if at least one candidate breaks it. Whether to add an explicit "now generate a candidate that takes the opposite framing" prompt is an open practitioner question.

- **How this transfers to non-text outputs.** The chapter's worked example is text generation. The same technique applies to code, visual designs, simulations — but the evaluation criteria differ across modalities. The book applies the technique to visual states in Chapter 11 (simulation build). Whether the same discipline generalizes cleanly is partially open.

---

## AI Wayback Machine

🕰️ **Gary Klein** (born 1944) — cognitive scientist whose work on **recognition-primed decision-making (RPD)** transformed how we understand expert decision-making in time-pressured domains. Klein studied firefighters, nurses, military commanders — experts who *recognize patterns* and rapidly simulate outcomes to make decisions, often without articulable reasoning. His *Sources of Power* (1998) is the canonical reference.[^1] The generate-evaluate-select technique is RPD with the *candidates externalized*. You generate three responses so that you have three pattern-recognized candidates in front of you at once, then your expert pattern-recognition fires to select. Klein's argument is that expert recognition is fast, partly tacit, and reliable when the expert has domain experience. Generate-evaluate-select gives your domain experience something to bite on. (The TIKTOC originally specified Herbert Simon's satisficing as the Wayback figure here — also a strong fit. The pantry research recommended Klein because his framework is closer to what the human actually does in the selection moment. The chapter uses Klein; you can substitute Simon if your reading prefers him.)

---

## Bridge

You have a verification technique that scales plausibility auditing. Chapter 7 puts everything together — AGENTS.md, Ask Mode → Code Mode, specifications, handoff conditions, the five capacities, generate-evaluate-select — on the build that matters most: the grading tool.

---

[^1]: Klein, G. *Sources of Power: How People Make Decisions*. MIT Press, 1998. Klein's RPD model is also documented in his academic papers (e.g., Klein, 1989, in *Decision Making in Action*).
