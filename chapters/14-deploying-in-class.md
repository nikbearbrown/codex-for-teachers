# Chapter 12 — Deploying in Class: From Build to Lesson

> The simulation works in Code Mode. Now it has to work with 30 students who have never seen it.

---

## Learning outcomes

1. **(Apply)** Deploy a classroom simulation as a shareable artifact that students can access without setup.
2. **(Analyze)** Identify the gap between "works in Code Mode" and "works in classroom" and conduct a revision build.
3. **(Apply)** Design a classroom activity using the simulation as a learning tool, not a demonstration.

---

## Opening

You project the simulation on the classroom screen.

The screen at the front of your classroom is a 1280×720 projector running Windows 7. You have not tested the simulation on a Windows machine. You have not tested it at this resolution. You have not tested it on the projector at all.

A student in the front row opens the simulation on their school-issued Chromebook. Touch only. No keyboard arrows. They tap the forward button. The bar chart moves. They tap the back button. The bar chart moves backward. They smile.

A student in the third row opens it on a personal phone. The mobile layout (Chapter 11 Phase 5) is visible. They start stepping through. They reach the end. They tap the reset button. The reset works.

A student in the back row opens it. The page is blank. They reload. Still blank.

You walk over. The student is on a school-issued laptop running an older Chromium. The console shows a JavaScript error: a `?.` optional-chaining operator in your code that the older browser does not support. The simulation works for 29 of 30 students. It is broken for one.

This chapter is about the gap between *works in your terminal* and *works in your classroom*, and the discipline that closes it.

<!-- → [DIAGRAM: Student-facing verification pass — three checks. Check 1: does a student who knows nothing about the code know what to do in 30 seconds? Check 2: are failure states informative? Check 3: does the simulation progress from easy to hard? Binary results. Revision build path if any check fails. Editorial style.] -->

---

## The three-check verification

Before you bring the simulation into class, run three checks. Each takes a few minutes. Together they catch the most common deployment failures.

### Check 1: First-30-seconds test

Hand the simulation to one person who knows nothing about the topic and nothing about the simulation. (A colleague who teaches a different subject works perfectly. A family member also works.) Watch them for thirty seconds without saying anything.

Did they know what to do?

The first thirty seconds is the moment that determines whether the simulation is a learning tool or a frustration. A student who does not know what to do in thirty seconds will check out, ask their neighbor, or close the tab. The remaining instructional value is reduced regardless of how good the simulation is once they start using it.

What they do reveals the gap. Did they see the forward button? Did they understand what the array was for? Did they wait for an explanation that wasn't coming?

If they did not start within thirty seconds, the simulation has an *affordance* problem. The fix is not in the simulation logic; it is in the visible cues. A "Click here to start" label. A pulsing animation on the first control. An on-screen prompt for the first action. Whatever it takes to make the *next action* obvious.

The simulation in Chapter 11 had this problem the first time it was tested. The fix was a single line of HTML — a centered prompt that said *"Press → or tap the forward button to begin"* — that disappeared after the first interaction. Trivial code change. Decisive UX change.

### Check 2: Are failure states informative?

The simulation will fail in your classroom. Some student's browser will not support a feature; some student will click something in an order you didn't anticipate; some student will lose network access for a moment and not realize.

What does the simulation do when it fails?

The right answer is **graceful failure with a clear next step**. The wrong answers are: silent break (the screen freezes; the student is confused); cryptic error (a JavaScript stack trace; the student is confused and also alarmed); or no acknowledgment that anything has gone wrong (the student keeps interacting; nothing happens; the student gives up).

For the simulation in Chapter 11, the failure modes worth handling: (a) JavaScript errors in older browsers — display a fallback message ("This simulation needs a modern browser. Try Chrome or Firefox."), (b) tap-too-fast errors where the user reaches the end and keeps tapping — display a "Sort complete; press reset to restart" message rather than letting the controls do nothing, (c) load failures — display an offline message rather than a blank page.

The graceful-failure work is the kind of work the conducting discipline tends to underweight. The build is focused on the working case; the failure cases are added later, if at all. The classroom-deployment chapter is where you build the discipline of *adding the failure cases before the simulation reaches students*.

### Check 3: Progression from easy to hard

A simulation that has no progression is a demonstration. A simulation that has progression is a learning tool.

For the sorting-algorithm simulation, the progression is built into the input choice. A nearly-sorted small array (3 elements, one out of order) is easy — the student sees one swap and the algorithm finishes. A reverse-sorted medium array (8 elements, all out of order) is hard — the student sees many swaps and watches the count grow. A pseudo-random large array (16 elements) is harder — the student begins to feel the O(n²) growth in their own attention.

If your simulation has the same difficulty for every interaction, there is nothing for students who are ready for more to do. They will be done in two minutes. They will check their phones.

If your simulation has a progression — even a simple one — students at different levels of comfort can engage at different levels. The first-time student plays the small easy case. The second-time student tries the reverse-sorted case. The student who is ready for the abstract claim about complexity classes runs the large random case and counts.

The Chapter 11 simulation built in a hard-coded array size of 8. The size-selector that Codex offered to add (and that you deferred to a future phase) is exactly the affordance that creates progression. **For classroom deployment, the size selector is no longer a "future phase." It is a check-3 prerequisite.**

You return to the build. You implement the size selector — small (3 elements), medium (8 elements), large (16 elements). You verify. You re-deploy.

---

## Deployment options

For a teacher who is not a developer, three deployment paths.

**ChatGPT Artifacts.** If you built the simulation through the Codex app, you can usually deploy it as a Codex/ChatGPT Artifact — a shareable URL that anyone can open in a browser, no install. Fastest path. Best for first deployments. Works on student devices that allow URL access. Stable for moderate-traffic classroom use; less guaranteed for high-traffic or long-term hosting.

**GitHub Pages.** If you have a GitHub account, GitHub Pages will host static HTML/CSS/JS at a public URL for free. Slightly more setup than Artifacts; more durable for the long term. Good for simulations you expect to use across multiple terms.

**Class website integration.** If you built a class website in Act One, the simulation can be embedded as a page on the class site. Most durable. Requires the simulation to be packaged for inclusion in the site's deployment pipeline.

For first deployments, Artifacts is the friction-minimum path. For simulations you will use repeatedly, the class-website integration is the long-term home.

---

## Conducting a revision build

The simulation will fail in class. Not catastrophically; in small ways that reveal what your pre-deployment testing missed. The discipline is *watching*, *noting*, and *conducting a revision build* with the same gate/specification/handoff discipline you used the first time.

The revision build is shorter than the original. The Ask Mode interrogation is more focused — you know what failed, you know what needs to change. The specification is tighter. The handoff conditions are about the specific failure, not the whole simulation.

The revision build for the back-row student's older-Chromium issue from the chapter opening:

> **Operation:** Add browser-compatibility fallbacks for older Chromium versions in `simulation.js`.
>
> **Invariants:** No change to the simulation's behavior on modern browsers. No change to the DESIGN.md visual vocabulary.
>
> **Context:** AGENTS.md sections on stack and verification. The failing browser is Chromium 86 on a school-issued laptop.
>
> **Output format:** A working simulation on the older Chromium, verified by opening on the specific laptop.
>
> **Negative constraint:** No new dependencies. No transpilation step. Hand-write the fallback code (the optional-chaining usage is in three places; replacing with explicit null checks is a 10-line change).

Codex executes. You test on the back-row student's laptop the next morning before class. It works. The simulation is now 30-of-30.

The revision is part of the build, not separate from it. The post-build document (Chapter 14) records the revision as a continuation of the original build.

---

## The classroom activity design

The simulation is not a demonstration. It is the *starting point* for an activity that does the pedagogical work.

For the sorting-algorithm simulation, a possible activity:

- **5 minutes:** students step through the small-array case individually. They count the comparisons. They write the count.
- **5 minutes:** students step through the medium-array case. They count again. They predict whether the large-array count will be larger or smaller than (medium count × 2).
- **5 minutes:** they run the large case and check their prediction. Most predicted too small. The chapter on bubble sort's complexity now lands operationally — *not from the formula, from the count they made themselves*.
- **5 minutes:** discussion. The teacher asks: *"For a 32-element array, how many comparisons would you predict?"* The students extrapolate. The teacher writes the formula on the board.

The simulation is the substrate. The activity is the lesson. The two together teach what neither would alone.

Notice what the activity is doing: it has students *produce* a count (germane cognitive load, the kind that constitutes learning), then *predict* (engaging the model the count built), then *extrapolate* (using the model to reason about a case they did not measure). This is the **Frictional** principle from the back-matter themes appendix applied to simulation-based learning. The simulation removed the *extraneous* load (no longer having to hand-draw the array transitions on the board); the activity adds back the *germane* load (the cognitive work that is the learning).

---

## Common misconceptions

**"If it works on my machine, it'll work in class."** No. Browser variance, network variance, touch vs. mouse variance, projector resolution variance — each one is a deployment failure waiting. The three-check verification catches the most common cases.

**"Pre-deployment testing is overkill."** Three checks. Fifteen minutes total. Saves a failed class period, which is worth dramatically more than fifteen minutes.

**"Failures in class are embarrassing."** Failures in class are *teaching moments* — for you and for your students. The student who watched you debug the back-row laptop is also a student who learned that real-world software has failure modes and that the fix is a deliberate process. Chapter 14 is the post-build document; the failure-in-class is exactly the kind of thing the document records, honestly.

**"I'll fix it during class if something breaks."** No. Fix it in advance. The thing you cannot fix in advance — the unanticipated student interaction, the device you didn't have access to — you fix in the revision build that night. Real-time debugging in front of 30 students burns your attention and theirs.

**"The simulation is the lesson."** No. The simulation is the *substrate*. The activity is the lesson. A great simulation with no activity is a demonstration. The pedagogical value comes from what the students *do with* the simulation, not from the simulation alone.

---

## Exercises

1. **(Apply)** Deploy your simulation (Artifacts, Pages, or class-website integration). Give it to one person who knows nothing about the topic. Watch them for thirty seconds without speaking. Document what they did that you didn't expect.

2. **(Analyze)** Run the three-check verification on your deployed simulation. Document the result of each check. For any check that failed, plan a revision build with a specific specification.

3. **(Apply)** Design a classroom activity for your simulation that puts students in the *producing* role, not the *observing* role. The activity should generate a measurable output (a count, a prediction, a comparison) that students can compare to each other's.

---

## Classroom activity

Have students deploy their own simulations and run a cross-class usability test. A student from another group tries each simulation without explanation. The builder observes. The builder documents:

- What did the tester not understand in the first 30 seconds?
- What failure state did the tester encounter? Was it informative or confusing?
- Did the tester reach a "now what?" moment with no path forward?

The builder then conducts a revision build based on observations. The revision is documented; the post-revision retest is documented.

This is the chapter's discipline applied to student work. The student practitioner now experiences what you experience: the gap between "works in my terminal" and "works for someone else."

This activity maps to Chapter 12 of the students book — *Deploying in Class: From Build to Lesson.*

---

## Links

- ChatGPT Artifacts documentation: [help.openai.com](https://help.openai.com) [verify — confirm Artifacts deployment guidance at press]
- GitHub Pages: [pages.github.com](https://pages.github.com)

---

## What would change my mind

The chapter's claim is that **the three-check verification meaningfully reduces classroom-deployment failures** for simulations built by teachers without developer training. If a controlled study compared teachers who ran the three-check verification to teachers who deployed without it — and found equivalent classroom outcomes (student engagement, time-to-first-interaction, failed-deployment recovery time) — the verification becomes optional rather than load-bearing. The chapter would still recommend the three checks (defense in depth); the urgency would drop.

---

## Still puzzling

- **Chromebook variance.** A K-12 classroom may have a wide range of Chromebook generations. The book's recommendation is to test on the oldest device in your room. Whether more sophisticated cross-browser testing is worth the time for teacher builds is open.

- **Touch vs. mouse vs. trackpad interaction modes.** The DESIGN.md (Chapter 10) forbids hover-only states and drag-and-drop precisely because of touch. Whether other interaction modes (stylus, voice, accessibility devices) deserve the same protection in DESIGN.md from the start is a live practitioner question.

- **The "show students the fix" lesson.** This chapter argues that showing students how the simulation was revised from their feedback is itself a lesson in conducting. Whether this meta-lesson lands at K-12 scale, and at what age, is open. Anecdotally, high-school AP CS students engage with it; whether middle-school students do is untested.

---

## AI Wayback Machine

🕰️ **Maria Montessori** (1870–1952) — Italian physician and educator whose *Montessori Method* (1912) argued that educational materials must be **self-correcting**: the student who uses the material discovers their own errors without needing teacher intervention.[^1] Montessori called this *the control of error*. Her insight was that materials with built-in feedback loops free the teacher's attention for the cases the material cannot handle, and free the student to learn at the pace their work produces. The first-30-seconds test in this chapter is *control of error* applied to digital classroom tools: the simulation that requires teacher explanation to begin is not yet a Montessori-grade learning material; the simulation that the student can open and start using without intervention is. Montessori's argument was made for physical materials (the pink tower, the cylinder blocks, the sandpaper letters). The principle scales to interactive simulations exactly: the value of the material is in *what the student can do with it independently*, not in what the teacher demonstrates from the front of the room.

---

## Bridge

The simulation is deployed. Students are using it. Chapter 13 maps what your students are learning to what you now know how to teach — and how the artifacts you have produced this whole book (AGENTS.md, the grading tool, the simulation, the build logs) become the teaching material for the discipline itself.

---

[^1]: Montessori, M. *The Montessori Method*. Frederick A. Stokes, 1912. The Schocken Books reprint (1964) is the standard English edition.
