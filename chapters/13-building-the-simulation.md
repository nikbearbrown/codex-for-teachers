# Chapter 11 — Building the Simulation: Conducting at Full Complexity

> The three files are in place, the plan is approved. The build begins. Every step has a specification, a handoff condition, and a labeled supervisory capacity.

---

## Learning outcomes

1. **(Apply)** Execute a simulation build sequence in Code Mode, completing Codex tasks and human tasks in dependency order.
2. **(Apply)** Apply each supervisory capacity at the steps requiring it, labeled explicitly.
3. **(Analyze)** Identify when the simulation build is going off-script and stop before the three-file system is violated.

---

## Opening

The three files exist. You have AGENTS.md, DESIGN.md, and PROJECT.md, all populated, all checked into git. The Ask Mode plan for Phase 1 of the simulation build sits in front of you. You have reviewed it. You have corrected one assumption (Codex wanted to use SVG for the bar chart; you decided to use HTML divs with CSS heights — simpler to debug, easier to inspect in devtools). You have approved.

You switch to Code Mode.

This chapter is what happens next.

<!-- → [DIAGRAM: The simulation build loop. Three files populated → Ask Mode plan → review and approve → Code Mode specification → execute → handoff condition check → pass/revert. Subagent or task-queue branch off the main loop. Supervisory capacity label at each human step. Editorial style.] -->

---

## Phase 1 — Scaffold and styling

The first build step is the scaffold: the HTML structure, the CSS variables from DESIGN.md, the empty containers that the simulation logic will populate.

**Specification (excerpt):**

> Operation: Create `index.html`, `simulation.css`, and an empty `simulation.js`. Invariants: per DESIGN.md and AGENTS.md. Output format: HTML scaffold with the array container, the control buttons (per DESIGN.md interaction vocabulary), the labels. CSS uses only the six variables from DESIGN.md. Negative constraint: no JavaScript logic yet; no animations; no test data injected.

Codex executes. Three files appear. You open `index.html` in Chromium.

**Handoff condition:** The page renders. The structure matches the spec (array container, four allowed controls, labels). The CSS uses only the six DESIGN.md variables (you check by searching `simulation.css` for any color value not in the variable list). The mobile breakpoint renders correctly. No JavaScript errors in the console (there is no JS yet, so any errors would indicate a misconfigured script tag).

All pass. Commit.

**Capacities exercised:** TO (choosing scaffold-first), PA (verifying the rendered scaffold against DESIGN.md), IJ (deciding whether the bar-chart container is the right shape — the spec said "container," you have to interpret what that means visually).

---

## Phase 2 — Bubble-sort algorithm in JS

The simulation logic. Pure JavaScript, no DOM manipulation yet.

**Specification:**

> Operation: Implement bubble sort in `simulation.js` as a pure function that takes an array and returns the sequence of (compared-indices, swapped-or-not, array-state-after) tuples. Invariants: no DOM access; no side effects; deterministic. Output format: `bubbleSortSteps(arr) → Array<{ compared: [i, j], swapped: boolean, arrayAfter: Array<number> }>`. Negative constraint: do not implement any other sort; do not optimize the implementation beyond what's needed for visualization (early termination is fine; sentinel optimizations are not).

Codex executes. The function appears. You write a quick test in the browser console:

```js
bubbleSortSteps([3, 1, 4, 1, 5, 9, 2, 6])
```

You inspect the return value. The first three tuples should compare indices [0,1], [1,2], [2,3] in the first pass. The first one swaps (3 > 1). The output matches.

**Handoff condition:** The function returns the right shape (array of step objects). The step count for the test input matches hand-traced count. Already-sorted input produces (n-1) comparisons and 0 swaps. Reverse-sorted input produces (n²-n)/2 comparisons and (n²-n)/2 swaps. The function has no side effects (calling it twice on the same input produces identical output).

The first three pass. The fourth — *no side effects* — fails. Codex's implementation mutated the input array in place rather than copying. You can see the issue in the diff: the bubble-sort function uses the input array directly, and after the function runs, the original array is sorted.

This is a revert moment. You go back to the specification. The invariant *"no side effects"* was in there, but the negative constraint did not name "do not mutate input" explicitly. You revise:

> Negative constraint (revised): do not implement any other sort; do not mutate the input array (make a copy if needed); do not optimize beyond what's needed for visualization.

You `/clear` to start fresh (the previous attempt's context is now noise). You re-specify with the tightened constraint. Codex re-implements. The function now uses `const sorted = [...arr]` and operates on the copy. All handoff conditions pass.

**Capacities exercised:** PA (catching the side-effect failure in the test), IJ (deciding that the side-effect issue was a specification gap rather than a Codex error), TO (the `/clear` and respecify decision).

---

## Phase 3 — Connecting the logic to the DOM

Now the simulation has to *do* something on the page. The user clicks the forward button; the simulation advances one step; the array container reflects the new state.

**Specification:**

> Operation: In `simulation.js`, implement the step controller that responds to user input (the four controls from DESIGN.md), advances or rewinds the simulation state, and updates the DOM. Invariants: per DESIGN.md interaction vocabulary; no hover-only states; no auto-advance. Output format: every click on a control updates the array container to reflect the current step's state, with the compared elements highlighted in `--accent`, the target in `--target`, the sorted region in `--highlight`. Negative constraint: no drag-and-drop; no animations beyond a single CSS transition on the highlight color change.

Codex executes. The page now responds. You step through a sort.

You watch.

The interaction is *almost* right. Forward stepping works. Backward stepping works. Reset works. Keyboard arrows work. But there is a subtle issue: when you reach the end of the sort, the simulation does not visually indicate "we are done." The last sorted-region update fades; the controls remain active; the user has no signal that they have completed a full sort.

**Handoff condition:** The four DESIGN.md controls work. Stepping advances/rewinds correctly through the full sort sequence. The visual highlights match the step state.

The handoff conditions pass. The thing you noticed — the missing "done" signal — is not a handoff-condition failure. It is *plausibility audit*: the simulation works, but it does not *teach* without a clear end-state signal. The student would reach the end and be uncertain whether they had finished or whether the simulation had broken.

This is exactly the case where the handoff condition does not catch the issue. You catch it by reading the experience against pedagogical knowledge. The fix is in the spec: add a step-end visual ("Sort complete" label) and a state where the array is shown fully sorted with all elements in the `--highlight` color.

You revise the specification, re-run, verify.

**Capacities exercised:** PA (the missing-end-signal catch — the wrong note), IJ (deciding what the right end-signal should look like, in this DESIGN.md vocabulary), EI (this is the second pedagogical refinement of the build; making sure the simulation as a whole still serves the Intent Layer).

---

## Phase 4 — The scope-creep moment

You are mid-Phase-3-revision. Codex finishes the sort-complete signal. Then, unprompted, Codex notes: *"While I'm in this file, I noticed the array size is hard-coded to 8. Would you like me to add a size selector?"*

This is the scope-creep moment.

The size selector is a real feature you want. It is in PROJECT.md Layer 2 as a "What is pending" item. It is *not* in the current build step. If you accept, you break the focus of the current step. If you refuse, you might forget the suggestion.

The right move: **log it in PROJECT.md Layer 2, decline now.**

You update PROJECT.md:

```markdown
## Layer 2: Technical State (Codex Layer)
...
What is pending:
- [...]
- Array-size selector. (Codex offered to add during Phase 3; deferred to a
  separate phase. Specify before implementing.)
...
```

You respond to Codex: *"Logged for a separate phase. Continue with the current step's verification."*

This is exactly the discipline Chapter 4 named — and the task-queue alternative from Chapter 9 — applied during a single build session. The scope-creep moment is one of the three pivotal moments every simulation build will produce. You handled it. Continue.

**Capacities exercised:** EI (the scope-creep would have drifted Phase 3 off-spec; you held the goal), TO (deferring vs. integrating).

---

## Phase 5 — Mobile responsiveness

DESIGN.md's accessibility rules include "works at 200% browser zoom" and "minimum 44px tap target on touch." The simulation needs to be verified on the mobile breakpoint.

**Specification:**

> Operation: Verify and adjust the CSS in `simulation.css` so the simulation renders correctly at the mobile breakpoint (Chrome devtools, iPhone preset). Invariants: per DESIGN.md. Output format: working mobile layout; controls are at least 44px tap targets; text is at least 16px. Negative constraint: no media-query branches that change the simulation's *behavior* (only its layout).

Codex executes. You verify in Chrome devtools.

The desktop layout is unchanged (good — the negative constraint held). The mobile layout: controls are 48px (above the 44px minimum). Text is 16px on the labels. But — and this is a screenshot-iterate moment — the bar chart's vertical proportions are off; the chart is too short on portrait mobile, and the visual relationships between bars (which is the *point* of the simulation) are visually compressed.

This is where the screenshot-and-iterate pattern earns its place. From the OpenAI engineering retrospective: *"Give it a mock and you say, build this web UI, it will get it pretty good. But if you iterate two or three times, often it gets it almost perfect."*[^1]

You take a screenshot of the current mobile rendering. You paste it into the chat. You describe what is wrong: *"The bar chart is too short on mobile portrait. The relative heights of bars are visually compressed; the simulation's value (comparing magnitudes) is lost. Increase the chart's vertical space at the mobile breakpoint; the controls can move below the chart on mobile to free up vertical space."*

Codex revises the CSS. You re-screenshot. The chart is now taller; the controls are stacked below; the relationships between bars are visible.

You iterate one more time on a minor spacing issue. By the third screenshot the mobile layout is right.

**Capacities exercised:** PA (catching the compressed-bars failure visually — not a handoff-condition failure), IJ (deciding the right fix was to restructure the layout, not just tweak heights), TO (the screenshot-iterate technique).

---

## Closing Phase 1 of the build

You have a working simulation at the end of these five phases. Bubble sort. Step controls. Mobile-responsive. Visually faithful to DESIGN.md. Pedagogically scoped per PROJECT.md's Intent Layer.

Two things remain: the size selector (logged for next phase) and the array-input customization (deferred to v2). You update PROJECT.md Layer 2 with what was built and what is pending. You commit. You write a brief build-log entry naming the supervisory capacities you used at each pivotal moment.

The simulation works in your terminal. Chapter 12 is what happens when you try to deploy it in your classroom.

---

## Common misconceptions

**"With three files, the build runs itself."** No. The three files protect against the *improvisation drift* failure mode. They do not eliminate the per-step gate or the per-output handoff conditions. The build is the same conducting discipline as Acts One and Two; the three files keep it on the rails.

**"Skip explain on familiar commands."** No — same as Chapter 1. The simulation build has more moving parts than the website. Familiar-looking commands hide more in Code Mode than they did in the simpler builds.

**"Scope creep is fine; the suggestions are good."** The suggestions are often good. They still break the current phase's focus. Log; defer; do.

**"Screenshot-iterate is a hack."** It is a documented practice. OpenAI engineers use it. It is the most efficient way to converge on a visual target when the target is not fully verbalizable.

**"The build is done when the handoff conditions pass."** The build is done when the handoff conditions pass *and* you have plausibility-audited the result against the Intent Layer. The end-signal-missing failure in Phase 3 is the example. Handoff conditions catch what you knew to specify; PA catches what you didn't.

---

## Exercises

1. **(Apply)** Execute Phase 1 of your own simulation build. Document every specification, every handoff condition evaluation, and every supervisory capacity label.

2. **(Analyze)** Identify the moment in your build where Codex's output passed handoff conditions but plausibility auditing caught something. Describe what PA caught and what you did about it.

3. **(Evaluate)** At the end of Phase 1: what would you change in your three files? Make the change. Run the next phase with the revised files.

---

## Classroom activity

Have students run Phase 1 of their own simulation build using their three files. Required: a build log documenting each specification, handoff condition, and supervisory capacity label. Peer review of build logs, not code — peers evaluate whether the log is honest, whether the labels are right, whether the plausibility-audit catches were named clearly.

This activity maps to Chapter 11 of the students book — *Building the Simulation: Conducting at Full Complexity.*

---

## Links

- OpenAI Codex documentation: [developers.openai.com/codex](https://developers.openai.com/codex)
- Codex screenshot-iterate pattern: [openai.com/index/harness-engineering](https://openai.com/index/harness-engineering/) [verify — confirm specific page on screenshot iteration]

---

## What would change my mind

The chapter's strong claim is that **the conducting discipline scales to full simulation complexity** — that AGENTS.md, the gate, specifications, handoff conditions, the five capacities, generate-evaluate-select, the task queue, and the three-file system together produce simulations that are pedagogically sound and visually faithful. If a controlled comparison — same simulation brief, with and without the full discipline — produced equivalent pedagogical outcomes and equivalent classroom usability, the discipline becomes a workflow preference rather than a load-bearing practice. I do not expect this; the dangerous middle and the scope-creep moment are real and the discipline catches them.

---

## Still puzzling

- **The right level of CSS specificity at the mobile breakpoint.** The chapter's worked example used three iterations. Some teachers will need more; some will need fewer. The right number is not specifiable in advance.

- **When to use the task queue vs. handle inline.** The scope-creep moment in this chapter was handled inline (log to PROJECT.md, decline now). It could have been handled by firing a task-queue item to investigate the size-selector idea in parallel. Both are defensible. The book's preference is to handle inline when the deferral can be expressed in one sentence in PROJECT.md; fire the task queue when the deferred work is itself non-trivial.

- **Schön over-use.** The TIKTOC originally named Schön here. The pantry research recommended swapping to Wanda Orlikowski (technology-in-practice) for both diversity and substantive fit. The chapter uses Orlikowski; if you prefer Schön, the substantive fit is also strong, and the TIKTOC would no longer match the book's Ch 7 figure. *(See the Wayback Machine entry below.)*

---

## AI Wayback Machine

🕰️ **Wanda Orlikowski** (born 1953) — MIT Sloan professor of information technologies whose work on **technology-in-practice** argues that tools are *shaped by the work they support* — that the meaningful unit of analysis is not the tool itself but the recurrent practices through which the tool gets used.[^2] In *Using Technology and Constituting Structures* (Organization Science, 2000) and in subsequent work, Orlikowski showed that two organizations adopting the same technology can produce strikingly different patterns of use, and that the difference is in the *practices* the technology gets enacted through. The three-file system + the conducting discipline is what makes Codex's *practice* — in your classroom, on your build — *yours*. The same Codex, used by a teacher with a generic prompt and no three-file system, produces the generic simulation that opened Chapter 10. Used with the discipline, it produces a simulation that fits your students. Orlikowski's framework is the argument for why the discipline matters: the tool is constituted by the practice. The book is a practice. *(The TIKTOC originally specified Donald Schön here; the chapter has used Orlikowski to avoid over-using Schön across the book. Schön remains the figure at Chapter 7 where reflection-in-action lands most precisely.)*

---

## Bridge

The simulation works in your terminal. Chapter 12 deploys it in your classroom. Thirty students. Three different laptop configurations. A projector that nobody has tested with. The gap between *works in Code Mode* and *works in class* is the chapter's subject.

---

[^1]: OpenAI engineers, "How OpenAI Engineers use Codex to Tackle Big Projects with Rigor" (forum.openai.com, December 4, 2025).
[^2]: Orlikowski, W. J. "Using Technology and Constituting Structures: A Practice Lens for Studying Technology in Organizations." *Organization Science* 11, no. 4 (2000): 404–428. See also Orlikowski's *Sociomateriality: Challenging the Separation of Technology, Work and Organization* (2008) for the elaboration.
