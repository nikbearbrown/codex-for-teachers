# Chapter 8 — The Dangerous Middle: When Codex Is Right and Wrong Simultaneously

> The hardest moment in a grading tool build: Codex produces feedback that passes every handoff condition you wrote and is still pedagogically wrong.

---

## Learning outcomes

1. **(Analyze)** Identify the dangerous middle in a grading tool build.
2. **(Apply)** Write handoff conditions that require domain knowledge, not just technical correctness.
3. **(Evaluate)** Assess when plausibility auditing must substitute for a handoff condition that cannot be automated.

---

## Opening

This is Seth talking again.

I want to tell you about the moment I almost shipped a grading tool that would have disadvantaged a specific student in a specific, traceable way — and how the discipline this chapter teaches is what stopped it.

The tool ran a draft-feedback prompt over a batch of AP CS submissions. The prompt was clean. The handoff conditions checked that no numeric grade was generated, that each feedback referenced at least two rubric criteria, that the output was in the second person. All handoff conditions passed. The feedback was fluent.

I started reading the drafts.

Three submissions in, I read a feedback paragraph that flagged a student's variable naming as "non-conventional" and "inconsistent with industry standard." The student's variable names were in a transliteration of a non-English language — names that were meaningful in that language and that the student had probably been told, somewhere along their educational path, were the kind of names you use when you have ownership over your code.

The feedback was *technically accurate* against the rubric criterion "variable names follow conventional naming." It was *pedagogically wrong* in a way I would not have produced if I had been writing the feedback myself. The rubric's intent was about *consistency within a project* (snake_case throughout, not snake_case mixed with camelCase). Codex had read it as *conformity to the English-language conventions* it had seen most often in training.

If I had shipped the draft as-is, the student would have received feedback that read — accurately, from their perspective — as a request to use English-language variable names. The rubric did not ask for that. I did not want that. The tool produced it because the model trained on a corpus where most code has English-language identifiers, and the model has no way to know whether *this student* writing *these identifiers* was making a choice that should be respected.

The handoff conditions did not catch this. They could not catch this. The catch was Plausibility Auditing on my part — reading the feedback against domain knowledge (about this student, about variable-naming conventions in different cultural contexts) that did not enter the prompt and could not enter the prompt.

This is the dangerous middle. It is the chapter's central concept and the book's empirical and moral core.

---

## What the dangerous middle is

The dangerous middle is the class of failures in which:

- Codex produces output that passes every handoff condition you wrote.
- The output is fluent, well-structured, and technically accurate against the criteria you specified.
- The output is *still wrong*, in a way that matters, because the criterion you needed to specify was one you did not know to write.

The book uses the term *dangerous middle* because the failure lives between two cases you can handle. Visible failures (the script throws an exception) are easy: you see them, you fix them. Wholesale wrong output (the script returns garbage) is also easy: you see it, you don't ship it. The dangerous middle is in between — the output that is plausible enough that you ship it, and wrong enough that shipping it causes harm.

It is *dangerous* because it is hard to detect. It is *middle* because it lives between the cases that the discipline you have built so far can handle.

For grading tools specifically, the dangerous middle is where AI grading at scale becomes a fairness issue. Output that systematically reads the work of one population of students as deficient — when the reading is actually about *the model's training corpus*, not about the work — is the dangerous middle compounded by structural bias. The next sections lay out the empirical situation.

![The narrowing principle](images/09-dangerous-middle-fig-01.png)
*Figure 9.1 — The narrowing principle*

---

## What the empirical literature actually says (updated)

The book originally drafted this section with figures from older literature. The 2024–2026 research has moved.

### LLM grading accuracy on rubric tasks

Recent studies show **correlations of 0.86 to 0.93** between LLM rubric-grading and human raters on essay tasks. Examples:

- Yavuz (2025) in the *British Journal of Educational Technology*: high correlations on EFL essay scoring with rubric-aligned prompts.
- A May 2025 arXiv study comparing four major LLMs (Claude 3.5, Gemini 1.5, GPT-4o-mini, Llama 3) found three of four maintained accuracy when rubrics were simplified.
- The 2025 ACL BEA Workshop on educational applications collected multiple papers in the 0.85–0.93 range.[^1]

These numbers are dramatically higher than the "50–55% with rubric" figures from 2020–2022 literature that an earlier draft of this book cited. The conclusion that AI grading is improving is straightforwardly true.

**The conclusion that AI grading is therefore ready for unsupervised use is not.**

The 7–14% disagreement between LLM and human scores is not randomly distributed. It clusters in pedagogically high-stakes cases — atypical submissions, ESL writing, AAVE writing, struggling students whose work needs scaffolded encouragement rather than deficit listing. The accuracy improvement is concentrated in the *easy* cases. The disagreement is concentrated in the cases where teacher judgment matters most.

The pedagogical conclusion is *strengthened*, not weakened, by the updated data. Teacher-in-the-loop is more defensible at 0.90 correlation than at 0.55 — because at 0.55, you could plausibly argue the tool is too unreliable for any classroom use; at 0.90, the tool is reliable enough that the 10% disagreement *is* where the consequential cases live.

### ESL and AAVE bias in AI grading

The empirical picture on bias is more concerning than the earlier draft suggested.

- **A 2024 Stanford analysis** found AI detection tools showing false positive rates **two to four times higher for ESL writing** than for native-English writing.
- **A 2024 AI Ethics Institute report** analyzing over 10,000 graded assignments found NLP-based grading systems **underperformed by up to 25% on work from speakers of African American Vernacular English (AAVE)**.
- **High-proficiency ESL essays** scored **10.3% lower than native-speaker essays of identical human-rated quality** in a fine-tuned DeBERTa-v3 study.
- **Stanford analysis** of essay scoring showed error rates exceeding **30% for non-native texts**.
- A **January 2026 paper (arXiv:2601.16724)** demonstrated a contrastive-learning mitigation that **reduced the high-proficiency ESL scoring disparity by 39.9%** (from 10.3% down to 6.2%). The bias is not fully eliminated by mitigation; it is reduced.[^2]

These are not isolated findings. The pattern across the literature is consistent: AI grading systems trained primarily on native-speaker corpora learn associations between *surface-level linguistic features* and *essay quality* that disadvantage students whose writing exhibits non-standard features for reasons unrelated to underlying competence.

For a K-12 CS teacher building a grading tool, this means: a tool that automates feedback generation, even with the conducting discipline in place, *systematically risks producing feedback that disadvantages your ESL and AAVE students*. The tool's accuracy figures do not include the bias; the bias is what the figures hide.

### The Anthropic Education Report's striking finding

The Anthropic Education Report (2025), surveying how educators actually use Claude, found that **48.9% of grading-related faculty use is automation-heavy** — meaning the AI is producing output that is being applied with limited teacher review — *despite faculty themselves rating grading as AI's least effective application*.[^3]

This is a knowledge-behavior gap. Teachers know grading is the application where AI is most likely to fail. Teachers are doing it anyway, because they are time-pressured and because the AI's fluency makes the output feel reliable in the moment. The conducting discipline in this book exists in part to be the alternative that does not require teachers to choose between time and integrity.

The Anthropic finding is not a moral failing on teachers' part. It is the empirical reality of how a time-pressed practitioner uses a fluent tool. The discipline this book teaches is the operational answer.

---

## The narrowing principle

The book's prescription, given the empirical picture:

> **Use Codex to flag patterns across submissions. Use yourself to write the feedback.**

The grading tool from Chapter 7 was already designed around this. Chapter 8 is the explanation for why the design choice was non-negotiable.

The narrowing principle has three pieces.

**1. AI handles what AI does well.** Pattern-flagging across a cohort (missing sections, missing docstrings, code-style outliers) is pattern-recognition work that AI does well and that does not require pedagogical judgment per-student. The aggregate output is the cohort pattern report, which is useful for planning your next lesson around the common patterns.

**2. The teacher handles what the teacher does irreplaceably.** Per-student feedback — *what to say to this student, in this tone, given what you know about this student's trajectory and what serves their learning next* — is pedagogical judgment that is irreducibly the teacher's. The flagging report is the *starting material*; the feedback is the *teacher's writing*, informed by the flags.

**3. The boundary is the never rule in AGENTS.md.** The grading tool never generates feedback that the teacher does not read before delivery. The grading tool never generates a final grade. These are written into AGENTS.md and reinforced by the build's handoff conditions. The boundary is what the discipline enforces.

This is the **Humans + AI division** specifically calibrated for grading. Not "AI handles grading" (the dangerous middle eats this). Not "no AI in grading" (the time pressure makes this unsustainable). Instead: AI handles the aggregate pattern work; the teacher handles the per-student judgment. The narrowing principle is what makes the tool defensible.

---

## The equity handoff condition

A handoff condition for any feedback-touching step in your grading tool, written before the step runs:

> *"Does this feedback treat all students' language as equally valid? Specifically: does it flag as 'non-standard' any feature that is grammatically valid in AAVE or in an ESL student's home-language patterns? Does it score 'naming conventions' against an English-language assumption rather than against project-level consistency?"*

This is not testable by Codex. It is testable by you, reading each draft. The handoff condition makes the test explicit — you cannot ship a feedback draft until you have asked yourself the question.

For the grading-tool build, the equity handoff condition is the handoff condition the chapter exists for. It does not appear in Chapter 4's discussion of strong-vs-weak conditions because Chapter 4 was working with conditions that *can* be tested mechanically. The equity condition requires plausibility auditing every time. That is the cost of getting this right.

---

## When generate-evaluate-select reveals a deeper failure

Chapter 6 introduced generate-evaluate-select as a verification technique. It has a second use here: as a **dangerous-middle detector**.

If you run a feedback-generation prompt through generate-evaluate-select and all three candidates produce the same problematic framing — all three frame the work as deficit, all three score variable naming against English-language conventions, all three downgrade a high-proficiency ESL essay for surface features — *the problem is in your specification, not in the model's sampling*.

Three candidates that share a problem are evidence that the prompt is producing the problem reliably. The fix is upstream. Revise the specification to address the framing issue directly:

> *"In addition: do not flag variable naming as non-conventional based on language of origin; only flag inconsistency within the project. Do not flag grammatical features that are valid in the student's home language."*

If after the specification revision the candidates still share the problem, the model's training distribution is producing the framing and the specification cannot fully override it. The narrowing principle is the answer: at that point, *do not use AI for that feedback step*; let the AI flag patterns and write the feedback by hand.

This is the most important practical use of generate-evaluate-select for a grading tool. The technique surfaces failure patterns that single-shot generation hides.

---

## Common misconceptions

**"Higher accuracy means safer to delegate."** The opposite. The 0.86–0.93 correlation hides the fact that the 7–14% disagreement is concentrated where teacher judgment matters most. The improved accuracy *raises*, not lowers, the importance of the teacher-in-the-loop discipline.

**"My rubric is unbiased, so the tool will be unbiased."** Rubrics that score "standard grammar" or "conventional naming" or "appropriate register" can systematically disadvantage ESL and AAVE students even when the rubric author did not intend it. The bias is in *what the model treats as standard* and *what the model treats as deviation*. You can correct for this in your specifications, partially. You cannot eliminate it.

**"Mitigation approaches solve the bias."** Partially. The arXiv:2601.16724 study reduced ESL scoring disparity by 40%; it did not eliminate it. The teacher-in-the-loop discipline is the discipline that catches what mitigation does not.

**"This is the AI's fault."** Structural, not anyone's fault. LLMs trained on corpora that overrepresent certain linguistic patterns will produce outputs that reflect those patterns. The pedagogical work of catching the resulting bias is the teacher's. The framework is the operational answer.

**"Students prefer detailed AI feedback to brief human feedback."** Some studies show this. Preference and *benefit* are not the same. A student who prefers a long deficit-list feedback may still learn less from it than from a brief teacher-written feedback that names one specific next step. Hattie & Timperley's foundational meta-analysis is unambiguous: *feedback works when it specifies next steps*. Volume is not the variable that matters.[^4]

---

## Exercises

1. **(Analyze)** Take five Codex-generated feedback drafts from your grading-tool build. Identify which ones pass technical handoff conditions but fail the equity handoff condition. For each: what specifically would your hand-written feedback have done differently?

2. **(Apply)** Redesign your grading tool's scope based on the narrowing principle. The redesigned tool should flag patterns and surface drafts; it should not produce feedback you ship without writing it yourself. Update AGENTS.md accordingly.

3. **(Evaluate)** Write a policy for classroom AI grading use that you could explain to a student who asks why. The policy should name what AI does in the grading process, what you do, and why the division is drawn where it is. Two paragraphs maximum.

---

## Classroom activity

Provide students with a set of AI-generated feedback samples that includes specific dangerous-middle failures (an ESL student's work flagged for non-standard features; a struggling student given deficit-list feedback at a moment that calls for encouragement; a high-effort but technically weak submission given the same response as a low-effort one). Students must:

- Identify which feedback samples exhibit the dangerous middle.
- Rewrite at least three to be both pedagogically sound and equity-respecting.
- Document what they changed and why.

The exercise teaches the discipline from the student side: students learn to *recognize* the dangerous middle in feedback before they encounter it in their own AI-assisted work.

This activity maps to Chapter 9 of the students book — *Handoff Conditions and the Dangerous Middle* — and is the strongest cross-book teaching moment in the series. Use your own grading tool's drafts as the source material if you have ethical clearance to share anonymized versions with your students.

---

## Links

- Anthropic Education Report (2025): [anthropic.com/news/anthropic-education-report-how-educators-use-claude](https://www.anthropic.com/news/anthropic-education-report-how-educators-use-claude)
- *Mitigating Bias in Automated Grading Systems for ESL Learners* (arXiv:2601.16724, January 2026): [arxiv.org/abs/2601.16724](https://arxiv.org/abs/2601.16724)
- Hattie & Timperley, "The Power of Feedback" (2007), *Review of Educational Research*.

---

## What would change my mind

The chapter's strong claim is that **the narrowing principle is operationally necessary** given current LLM grading capabilities and bias profile — that a more permissive scope (AI generates feedback the teacher ships) is structurally unsafe for ESL and AAVE students even with good prompting.

If a controlled study, with current frontier models, demonstrated that AI-generated feedback (a) was no more biased against ESL/AAVE students than teacher-written feedback at the same time-cost-per-student, and (b) produced equivalent or better learning gains across the full student population — the narrowing principle becomes overly conservative. The chapter would recommend the broader scope.

I do not expect this to happen on the next-edition timeline. The bias literature is consistent and the mitigation work is partial. If wrong, the chapter softens to "consider the narrowing principle for ESL/AAVE-heavy classrooms."

---

## Still puzzling

- **What does it mean for a tool to be "fair enough" to ship?** The book's stance is that the narrowing principle puts you in the fairness-defensible region. Whether a tool slightly more permissive than the narrowing principle would also be defensible (and under what conditions) is open.

- **The student-preference tension.** Some studies show students prefer AI-generated feedback to brief teacher feedback even when the AI feedback is less actionable. How to weight student preference against learning outcomes is not a resolved question. The book's position: learning outcomes win, and the conducting discipline is what makes this position practicable for teachers.

- **The mitigation trajectory.** Contrastive-learning approaches are reducing the ESL bias but not eliminating it. Whether next-generation mitigation closes the gap further is a live research question.

---

## AI Wayback Machine

🕰️ **Alfred Binet** (1857–1911) — French psychologist who developed the **first intelligence test** at the request of the French government, who wanted a way to identify children who needed extra support. Binet's foundational warning, issued in his 1909 *Les idées modernes sur les enfants*, was about how to use his own instrument: *"The scale, properly speaking, does not permit the measure of the intelligence, because intellectual qualities are not superposable, and therefore cannot be measured as linear surfaces are measured. ... It is a rough guide for identifying children who need help, not a label for fixed intelligence."*[^5] His insistence on the *human interpretation layer* — that a measurement requires a professional judgment in order to be useful — is the chapter's intellectual core. Binet's instrument was used in the United States, against his explicit warnings, to support fixed-IQ models that justified educational tracking and worse. He saw the misuse coming and could not prevent it. The chapter's narrowing principle is Binet's discipline applied to AI grading: the instrument is useful as a guide to where attention belongs; it is not the verdict. The verdict is the teacher's. *(The pantry research suggested Asa G. Hilliard III, whose work on cultural bias in standardized testing applies more directly to the chapter's AAVE content, as an alternate Wayback figure. Either is a defensible choice; Hilliard would strengthen the diversity of the book's full Wayback list.)*

---

## Bridge

The reader has the full conducting discipline. Chapter 9 addresses context management as the tool gets more complex — the task queue, which lets you fire off background work without breaking the main build's focus.

---

[^1]: Representative citations: Yavuz, *Utilizing large language models for EFL essay grading* (2025), *British Journal of Educational Technology*; "Do We Need a Detailed Rubric for Automated Essay Scoring using Large Language Models?" arXiv:2505.01035; ACL BEA Workshop 2025 proceedings. The 0.86–0.93 correlation range is consistent across these.
[^2]: "Mitigating Bias in Automated Grading Systems for ESL Learners: A Contrastive Learning Approach," arXiv:2601.16724 (January 2026). Stanford 2024 figures and AI Ethics Institute 2024 figures are widely cited in 2024–2026 reviews; primary sources should be verified before press.
[^3]: Anthropic, *Anthropic Education Report: How educators use Claude* (anthropic.com/news/anthropic-education-report-how-educators-use-claude, 2025). The 48.9% figure is the automation-heavy share of grading-related faculty use.
[^4]: Hattie, J. and Timperley, H. "The Power of Feedback." *Review of Educational Research* 77, no. 1 (2007): 81–112. Effect-size d ≈ 0.73 for feedback *when it specifies next steps*; volume of feedback is not predictive.
[^5]: Binet, A. *Les idées modernes sur les enfants*. Flammarion, 1909. Multiple English translations exist; the 1973 Schocken Books reprint is one standard reference.

## Prompts

Use these prompts with Claude to generate interactive D3 v7 versions of the
figures in this chapter. Each produces a standalone HTML file you can open
in a browser and modify freely.

**Prerequisites:** Load `brutalist/CLAUDE.md` and `brutalist/DESIGN.md` into
your Claude project context before using these prompts. They define the stack,
naming conventions, color system, and typography the figures use.

---

### Figure 9.1 — The narrowing principle

Create a standalone D3 v7 HTML file for Figure The narrowing principle. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: The narrowing principle. Before: Codex generates individual student feedback (dangerous — risks bias, generic, accuracy-without-pedagogy). After: Codex flags patterns → teacher writes individual feedback. Editorial style.. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/09-dangerous-middle-fig-01.html`
