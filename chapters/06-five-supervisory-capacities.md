# Chapter 5 — The Five Supervisory Capacities

> These are the five things you do that Codex cannot. Name them. Exercise them explicitly. Never delegate them.

---

## Learning outcomes

1. **(Remember)** Name and define the five supervisory capacities.
2. **(Apply)** Label the supervisory capacity required at each step of a provided grading tool build sequence.
3. **(Analyze)** Diagnose a build that went wrong by identifying which supervisory capacity was absent.

---

## Opening

This is Seth talking.

I was mid-build on a grading tool. The thing was nearly done. Codex had generated a feedback function that took a student submission, ran it against the rubric criteria I had specified, and produced a paragraph of first-draft feedback. The function compiled. The tests I had written passed. The example outputs I checked by hand looked plausible.

I almost shipped it.

Then something stopped me. Not a test failure. Not a lint error. Not anything I could point to. The output read like the kind of thing I would say if I had never met the student. The cadence was right. The criteria were right. The feedback was *technically accurate*. But it was not feedback I would actually give.

I sat there for a while trying to articulate the wrongness. Eventually I had it: the feedback assumed a generic struggling student. My actual students that week were not the generic struggling student. Two of them were exhausted from sports; one was working through grief; one had been growing all semester and needed scaffolded encouragement, not a deficit list. The feedback function did not know any of this. It could not know any of this. The output passed every condition I had thought to write — and was still wrong in the way that mattered.

What stopped me from shipping was not a test. It was **plausibility auditing**. The wrong note. The feeling of mismatch between fluent output and what I knew to be true about the situation.

This chapter is about plausibility auditing and the four other things you do that Codex cannot. Together they are the supervisory work that the conducting discipline keeps yours.

![Five supervisory capacities as a five-column layout](images/06-five-supervisory-capacities-fig-01.png)
*Figure 6.1 — Five supervisory capacities as a five-column layout*

---

## The five capacities

The capacities have abbreviations because you will refer to them in build logs. Two letters each.

### [PA] Plausibility Auditing

**The capacity to hear the wrong note before verification catches it.**

PA is what stopped Seth from shipping. The output is fluent. The tests pass. Something still does not match what you know about the domain. PA names this gap as a recognizable cognitive operation, not a vague feeling.

The mechanism: Codex generates output calibrated for *accuracy against the patterns it learned*. The accuracy is real but partial. The domain knowledge that determines whether the output is *appropriate for this specific situation* is yours. PA fires when fluent output mismatches the domain context you have but did not put in the prompt.

In grading: *"This feedback is technically accurate. But would I say this to this student? Does it match the rubric in the way the rubric intends?"* You catch it when you hear the wrong note. The catch requires that you have domain knowledge — which means PA is *cumulative*: the more you have actually graded student work, the more reliable your PA becomes.

### [PF] Problem Formulation

**The capacity to decide what the build IS before Codex sees it.**

Codex optimizes within the frame you give it. If the frame is wrong, the output is wrong, elegantly. PF is the work of getting the frame right *before* the first prompt.

In grading: "Am I building a tool that *generates individual student feedback*, or a tool that *flags patterns across submissions so I can write the feedback myself*?" These are different builds with different outputs and different failure modes. The decision between them is PF. Once you have decided, Codex helps you execute. If you have not decided, Codex will produce an answer to whichever frame your prompt accidentally implied — and the dangerous middle (Chapter 8) gets closer.

Ask Mode is your tool for PF. Use Codex in Ask Mode to interrogate the problem space — *"What questions would a teacher need to answer before designing a grading workflow?"* — and let the interrogation surface frames you hadn't considered. The deciding is still yours; the interrogation is help.

### [TO] Tool Orchestration

**The capacity to choose which Codex mode, which task, in what order, with what trust level.**

TO is the scheduling work. Which step gets Ask Mode? Which gets Code Mode? Which uses the multi-response generate-evaluate-select technique (Chapter 6)? Which uses the task queue (Chapter 9)? Which should not use Codex at all, because the cost of getting it wrong is higher than the cost of writing it by hand?

In grading: "Do I give Codex the whole rubric or just the criteria for this assignment? Do I run the feedback generation through generate-evaluate-select to compare framings? Do I fire off a pattern-analysis task while I focus on a different step?" These are sequencing decisions; they affect the build's quality at least as much as any individual prompt does. TO is the conducting metaphor's most literal expression — you are scheduling instruments.

### [IJ] Interpretive Judgment

**The capacity to supply meaning Codex's output cannot supply.**

Output can be correct and meaningless in your context. IJ is the work of supplying the meaning.

In grading: "This feedback is technically correct, but this student has been struggling all semester. The feedback needs a different tone." The correctness and the meaning are different things; IJ is the bridge.

IJ overlaps with PA but is not identical. PA catches the wrong note; IJ supplies the right note. PA fires defensively (something is off); IJ fires constructively (here is what would actually serve). In practice, the two often run together: PA notices the mismatch, IJ produces the revision.

### [EI] Executive Integration

**The capacity to hold the whole build toward a single goal across many prompts.**

A long build session has dozens of prompts. Each one is locally reasonable. Without EI, you finish a build that has drifted — every individual step looked fine, but the cumulative result violates a constraint you set three hours ago.

In grading: "Three prompts ago we agreed the tool would never generate a final grade. This output is generating grades. Stop." EI is the capacity that catches drift. It requires that you remember what was agreed, that you notice when the current output violates it, and that you intervene before the drift compounds.

EI also exercises across *sessions*: the constraint you set in last week's session, recorded in AGENTS.md, is something Codex will respect if it can see it. EI is partly about remembering, partly about ensuring the things you have agreed are written down so Codex can also remember.

---

## The capacities in motion: a worked grading-tool build

A full grading-tool build sequence, with capacities labeled.

| Step | Action | Capacity exercised |
|------|--------|---------------------|
| 1 | Decide whether to build a *feedback generator* or a *pattern flagger* | **PF** |
| 2 | Open Ask Mode, ask Codex to interrogate the rubric file | **TO** + **PF** |
| 3 | Read the Ask Mode plan; correct one wrong assumption about the rubric structure | **IJ** |
| 4 | Approve plan; switch to Code Mode | **TO** |
| 5 | Codex writes the rubric-parser. Tests pass. | (no capacity needed yet) |
| 6 | Codex writes the pattern-flagger. Tests pass. Output flags look reasonable on three sample submissions. | **PA** (checking against sample) |
| 7 | Codex proposes "while I'm here, want me to also generate per-student feedback?" | **EI** (this violates the PF decision in step 1; stop) |
| 8 | Decline. Log the suggestion in PROJECT.md for later. | **TO** |
| 9 | Run pattern-flagger on full submission set. Output: 47 flags. | **PA** (do these flags match what you'd flag manually on a sample?) |
| 10 | Spot-check: take 5 submissions; flag them manually; compare. 3 of 5 match. | **PA** + **IJ** (interpret the mismatch) |
| 11 | Realize: the rubric's "code organization" criterion was interpreted by Codex as comment density, not actual function decomposition. Revise. | **PF** (revisit the frame) |

Eleven steps. Five capacities. Each capacity fires at a different moment. The discipline is naming them as they fire — because naming makes them more reliable, and labeling them in your build log lets you diagnose later what went well and what didn't.

| Item | Meaning |
| --- | --- |
| Five supervisory capacities | label, plain name, what it catches, example failure when absent. Five rows. No color. |

---

## Diagnosing a build that went wrong

The capacities are diagnostic. When a build produces a bad outcome, you can ask: *which capacity was absent?*

- **Output is fluent but wrong in a way the tests don't catch.** PA was absent or fired and was overridden.
- **The whole build solved the wrong problem.** PF was absent at step zero.
- **Wrong tool at the wrong time.** TO was absent — you were in Code Mode when you should have been in Ask Mode, or vice versa.
- **Output is technically correct but means the wrong thing in context.** IJ was absent.
- **Final result violates a constraint you set earlier.** EI was absent — the constraint was forgotten across the session.

This is the conducting framework's payoff. A build that goes wrong is not a mystery. It is one of five named failures. The post-mortem becomes structured: which capacity was absent at which step? What would the build look like if it had fired? This is how you teach the next session (or the next teacher) without repeating the failure.

---

## The Humans + AI division this represents

The five capacities are the operational form of the **Humans + AI** theme that runs through this book. They are the work that the human practitioner does in an AI-assisted build — not because the human is faster or because the human "should" do them, but because the cognitive operations they require are ones the model is structurally weak at.[^1]

The structural argument: a model that generates output cannot reliably audit its own output, because the same weights that produced the output are doing the audit. Plausibility auditing must come from outside the model. Problem formulation requires values (what matters in this context); models do not have stable values across contexts. Tool orchestration requires meta-judgment about the model itself; the model has no privileged view of its own limits. Interpretive judgment requires meaning that exists outside the data the model was trained on. Executive integration requires holding intent across time in a way the model's context window does not durably support.

These are not limitations the next model release will close. They are properties of *what models structurally are*. The conducting framework is built on this argument.

This does not mean the capacities are eternal. The book's Contested Claims table is honest: the five supervisory capacities "currently require human judgment." The "currently" is doing work. The book stakes its prescription on the current generation of agentic AI and on a near-term horizon that looks similar. If, in 2030, models develop reliable meta-cognition of their own outputs — the capacity to flag their own errors as outputs rather than as parts of their reasoning — the chapter's claim would need revising.

For now, the capacities are yours. Name them. Practice them. Never delegate them.

---

## Common misconceptions

**"I have to consciously perform all five on every prompt."** No. The capacities fire at different moments. PF dominates at the start of a build. TO fires at tool-selection decisions. PA fires when output arrives. IJ fires when you have to revise. EI fires when something drifts. Most prompts exercise one or two; some exercise none (mechanical handoffs); a few exercise all five.

**"With practice they fuse into a single capacity."** Yes — and you should let that happen. The named decomposition is for the early period when you are still learning to recognize what you are doing. Once the practice is internalized, the names recede. You will still use them in build logs (to make supervisory work *visible* in retrospect), but you will stop thinking in five distinct operations.

**"PA = paranoia."** No. PA is vigilance — the attentive reading of output against domain knowledge. Paranoia is undirected suspicion of all output. PA is directed: you suspect the output where the domain knowledge suggests it could be wrong. It saves you time; paranoia costs you time.

**"The five capacities are personality traits."** They are practices. They develop with use. The teacher who has run five build sessions has stronger PA than the teacher who has run one — not because they are wired differently but because they have practiced.

**"Models will eventually do all five themselves."** Maybe. The book's position is that, on the current trajectory, the capacities will remain irreducibly human for at least the near-term horizon for which this book is written. The "currently" qualifier in the Contested Claims table is the honest version of this.

---

## Exercises

1. **(Apply)** Take your grading-tool build plan (from your AGENTS.md and the Ask Mode interrogation from Chapter 2 or 3). Label the supervisory capacity required at each major step. Aim for one capacity per step where possible; some steps will need two.

2. **(Analyze)** Review a Codex transcript from a build you (or another teacher you know) ran in the past month. Identify one moment where a supervisory capacity should have fired and did not. Which capacity? What happened as a result?

3. **(Create)** Design a classroom activity that teaches the five supervisory capacities using a non-coding context — collaborative writing, peer-review of essays, lab notebook critiques, any domain where students are reviewing partly-generated work. The capacities should map cleanly to recognizable moments in the activity.

---

## Classroom activity

Provide students with a Codex transcript in which one supervisory capacity is systematically absent. (Example: a transcript where the student approved every output without exercising PA, ended up with a polished but wrong final result.) Students must identify which capacity was missing, trace the consequences, and propose where the intervention should have happened.

The transcript can be a real anonymized session from the teacher's own build or a synthetic one. The diagnostic exercise is the point: students recognize a failure pattern when it has a name.

This activity maps directly to Chapter 5 of the students book, which introduces the same five capacities from the student's angle. Cross-reference is explicit.

---

## Links

- Anthropic, "How AI assistance impacts the formation of coding skills" (2026): [anthropic.com/research/AI-assistance-coding-skills](https://www.anthropic.com/research/AI-assistance-coding-skills)
- *Codex for Students*, Chapter 5: introduces the same five capacities from the student practitioner angle.

---

## What would change my mind

The chapter stakes a strong structural claim: that the five capacities are *not closable* by improvements to the model. If a near-term model release demonstrated *reliable* meta-cognition of its own outputs — not just self-critique that occasionally helps, but a measurable reduction in confidently-wrong output across diverse domains — Plausibility Auditing would become partially delegable. The chapter would need revising to specify which capacities are now partially shared and which remain irreducibly human.

I do not expect this to happen on the next-edition timeline (2027–2028). I am willing to be wrong.

---

## Still puzzling

- **Are five the right number, or is the decomposition somewhat arbitrary?** The five capacities are a synthesis from Engelbart, Norman, Klein, and the Anthropic 2026 RCT's three engagement patterns. Other taxonomies use three or seven. The five is operational — it is the number that proved useful for naming what we do in build sessions. Whether it is the *correct* number is not a question with a clean answer.

- **Distinguishability.** Some readers will conflate PA and IJ. The chapter draws the line (PA = defensive, IJ = constructive), but in practice they often run together. Whether the distinction is worth preserving or whether they should merge into a single capacity is an open practitioner question.

- **Capacity fluency development.** The chapter argues that capacities strengthen with use. Anthropic measured engagement patterns at a single time point; whether sustained practice produces durable capacity improvement is not directly measured. The book's bet is that it does.

---

## AI Wayback Machine

🕰️ **Norbert Wiener** (1894–1964) — mathematician who founded **cybernetics**, the study of control and communication in animals and machines. Wiener's central insight was that systems maintain their goals through *feedback loops*: a signal that compares current state to intended state, used to correct course. *The Human Use of Human Beings* (1950, revised 1954) extended cybernetics into a question that is the question this book asks: *what does the machine do to the human who uses it?*[^2] The five supervisory capacities are Wiener's feedback loops applied to AI-assisted work. They are the mechanisms by which the human maintains the build's goal in the face of the disturbance — *productive* disturbance, but disturbance — that the agentic system introduces. Without the feedback loops, the system drifts. Wiener saw this in 1950 with mechanical systems. The chapter is his argument applied to systems that write code.

---

## Bridge

Chapter 6 introduces the verification technique that makes one specific capacity — Plausibility Auditing — more reliable at scale: generate multiple Codex responses for the judgment-intensive step, evaluate them all, select. The technique is sometimes called Best-of-N. The skill is older.

---

[^1]: This is the *Humans + AI* theme developed in the back-matter Fundamental Themes appendix. The five capacities are its operational form for Codex builds.
[^2]: Wiener, N. *The Human Use of Human Beings: Cybernetics and Society*. Houghton Mifflin, 1950; revised 1954. The 1954 edition is the standard citation.
