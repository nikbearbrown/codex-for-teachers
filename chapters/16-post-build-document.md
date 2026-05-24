# Chapter 14 — Your Terminal Deliverable: The Post-Build Document

> The simulation is deployed. The build is done. This chapter is the record of what you built, what you learned, and what you would do differently.

---

## Learning outcomes

1. **(Create)** Produce a post-build document for the interactive simulation using the five-section template.
2. **(Evaluate)** Assess your own build against the five supervisory capacities.
3. **(Create)** Design a second build based on what the first one taught you.

---

## Opening

Not Seth's build. Yours.

The simulation is running in your classroom. Students are using it. The grading tool is processing the first batch of submissions from this week's assignment, and you are reading the first-draft feedback as you write this chapter's draft. The class website is up to date. The AGENTS.md you started in Chapter 2 has thirty-one lessons-learned entries; you can read it as a record of the semester.

This chapter asks one thing: account for every decision.

Not in defense. Not in performance. In the honest mode that the conducting discipline has prepared you for over twelve chapters. You built three tools. Some of them are better than you imagined. Some are worse. You delegated some work to Codex; you kept some work for yourself; the choices were yours and you can explain them.

The artifact that records this is the **post-build document**. Five sections. One file per build. Honest.

![The post-build document as the arc's terminal artifact](images/16-post-build-document-fig-01.png)
*Figure 16.1 — The post-build document as the arc's terminal artifact*

---

## The five sections

The template is the same for every build. By section:

### 1. What I built

One paragraph. Plain language. Not technical. The kind of description you would give a colleague who teaches a different subject and asks what your project does.

For the sorting-algorithm simulation: *"An interactive bubble-sort visualization that my AP CS students step through one comparison at a time, watching the bars compare, swap or not, and slowly accumulate into a sorted region. The simulation has three input sizes — small, medium, large — so students who finish the easy case can try the harder ones. It's deployed via ChatGPT Artifacts and linked from the class website."*

The point of this section is to remind you what you actually built. Six months from now you will not remember the build's details; this paragraph will.

### 2. What I delegated to Codex and why

This is the section where you make the labor split explicit. For each major category of work in the build: did Codex do this, or did you?

For the simulation:

> *"I delegated to Codex: the HTML scaffold, the CSS generation from the DESIGN.md variables, the bubble-sort algorithm in pure JavaScript, the step-controller logic that translates user input into algorithm advances, the array-state-to-DOM translation, the mobile-responsive CSS, and most of the browser-compatibility fallback work in the revision build. These are pattern-completion tasks: the patterns are well-established, Codex generates them faster than I could type, and the verification is straightforward (does it work, does it match the spec).*

> *"For the bubble-sort logic specifically, I also delegated the test-input generation — Codex produced three test inputs (small-sorted, medium-mixed, large-random) that I used to verify the algorithm's correctness. That saved me about twenty minutes."*

The why for each is the same: pattern-completion work that benefits from speed and where verification is cheap.

### 3. What I kept for myself and why

The mirror section. This is where the irreducibly human work is named.

> *"I kept the Intent Layer of PROJECT.md — what the simulation is for, what the student should understand, what questions it refuses to answer, the tone. This is the part that makes the simulation mine; Codex would have produced a generic version.*

> *"I kept the DESIGN.md decisions — the six colors, the four allowed interactions, the explicit list of what the system never does. These are constraints, not preferences, and they protected the build from improvisation drift.*

> *"I kept the pedagogical scope decision: bubble sort specifically, as a counterexample to efficiency, not as a sort to memorize. This is the framing that makes the simulation teach what I want it to teach. Codex would have produced a generic sorting visualization; the framing is what makes it specifically useful for my class.*

> *"I kept the revision-build decision: when the back-row student's browser failed, the revision was a deliberate build session with its own specification and handoff condition. The decision to do the revision deliberately rather than patching reactively was mine."*

The why for the kept work is harder to articulate than the why for the delegated work. The kept work is the work where my judgment was irreplaceable: judgment about my students, my classroom, my pedagogical goals, my voice. Articulating this section is *itself* the supervisory work the book has been teaching.

### 4. What I learned that I didn't know before the build

This section is the consolidation. What changed in your head between starting the build and finishing it?

> *"I learned that Codex iterates on visual output if I give it a screenshot to compare against — the screenshot-iterate pattern was the most useful technique for the mobile-responsive work. I had not realized the model could engage with visual targets this way; I assumed I would describe the layout in words.*

> *"I learned that the DESIGN.md six-color constraint was the most useful thing I did. Forcing myself to decide on six and only six colors made me decide what each color was *for* — and that decision is what makes the simulation visually coherent. Without the constraint, the build would have drifted to a more decorative version that taught less.*

> *"I learned that the scope-creep moments are real and frequent. Codex suggested three 'while I'm here' improvements during the build. Two were good; logging them in PROJECT.md let me come back to them. One was off-spec; declining it kept the build focused. I had practiced this in Acts One and Two, but the simulation build is where it landed as a *habit* rather than a *rule*.*

> *"I learned that the first 30 seconds of classroom use teaches you more about your build than three hours of pre-deployment testing. The student who could not open the simulation on the older Chromium was the test case I could not have constructed on my own machine."*

The pattern: name what changed. Be specific. The reader of this section (which is mostly future-you) needs the specifics to recognize the lesson later.

### 5. What I would do differently

The hardest section to write honestly. The temptation is performative humility (*"I would do more research before starting"* — vague, unfalsifiable, useless to future-you) or performative bravado (*"I would do nothing differently; the build is exactly what I wanted"* — almost certainly false; also useless).

The honest mode is specific: name a real decision you would reverse and explain why.

> *"I would write the Intent Layer of PROJECT.md before AGENTS.md and DESIGN.md, not after. I drafted them in the order they appear in the three-file system chapter (Chapter 10), which is AGENTS → DESIGN → PROJECT. Writing PROJECT first would have changed what I put in the other two — the technical decisions and the visual vocabulary would have been calibrated to the Intent. As it was, I had to revise AGENTS.md once and DESIGN.md twice as the Intent Layer revealed what mattered. Next time, Intent first.*

> *"I would specify Step 4 (step controls + keyboard handling) before Step 3 (the bubble-sort algorithm itself). The algorithm's interface — what tuple shape it returns — depends on what the step controller needs. I built the algorithm first, then built the controller, then had to revise the algorithm's return shape to match what the controller wanted. The dependency runs the other direction.*

> *"I would add the size-selector affordance in the original specification, not as a Phase 5 deployment requirement. The size selector is what makes the simulation work for students at different levels of readiness; building it in last meant deployment testing surfaced its absence as a problem. Building it in first would have integrated cleanly.*

> *"I would have spent more time on PROJECT.md's *What questions it refuses to answer* section. My initial answers were two bullet points; the deployment surfaced a third question students kept asking ('what about quicksort?'). Adding it to the refuse-list early would have saved a class-period digression."*

Four specific decisions. Each is reversible (not "I'd be smarter"; specific moves I would make differently). Each is something future-me can apply on the next build.

The post-build document is most valuable when this section is honest. The temptation to perform here is real. The discipline is to resist.

---

## The AGENTS.md as the second deliverable

The post-build document is the chapter's terminal deliverable. The AGENTS.md — the three-tier file you have maintained from Chapter 2 through Chapter 11 — is the *second* deliverable.

Both travel with you. The post-build document records what you learned from this specific build. The AGENTS.md records what your project knows about itself. Together they are the artifacts that make the next build faster, the next teaching moment sharper, the next student conversation more grounded.

When you start your next build, you do not start from scratch. You start with the AGENTS.md from this build (forked, refined for the new project) and with the lessons from the post-build document (the *what I would do differently* section especially). The second simulation will be smaller, faster, and better-scoped because the first one taught you what to scope.

---

## What comes next

You are at the end of the book. Three concrete next moves:

**The second simulation.** Smaller. Better Intent Layer from the start. Built in less time. The pattern this book has taught is iterative — each build improves the discipline, and each improvement compresses the time-to-shippable on the next build. By the third simulation, the conducting discipline is internalized; the explicit framework becomes implicit practice.

**The CSTA community.** The CS Teachers Association has active discussions on AI in K-12 CS classrooms. Other teachers are practicing variants of what you have practiced. Sharing your AGENTS.md, your build logs, your post-build documents — with appropriate redaction — is how the practice matures across the field.

**The students book, again.** Now that you have built three tools, return to *Codex for Students*. The chapters that read as framework when you started will read as *recognized practice* now. You will see what the students will see in a way the first read did not allow. This re-reading is where you find the specific moments in the students book that map to specific moments in your build experience — which is what makes the cross-book chapter map in the previous chapter operational.

---

## Common misconceptions

**"Post-build is bureaucratic."** Five sections. Under thirty minutes. Most teachers report it is the most useful thing they wrote in the build.

**"I'll write it when I have time."** No. Write it now. The lessons are freshest now. They will not stay fresh.

**"My document should be modest."** Performative humility is the failure mode of this section. Be specific about decisions you would reverse. The honesty is the value.

**"The document is just for me."** Mostly yes. Some of it (the *what I learned* section especially) can be shared with students as teaching material. Most of it lives in your build folder for future-you.

**"I'm not done with the build, so I can't write the document yet."** The build is done when the simulation is in classroom use and you have conducted one revision based on student feedback. The polishing afterward is ongoing; the post-build document is for the build as it stood at the moment of meaningful deployment.

---

## Exercises

1. **(Create)** Write your post-build document for the simulation. Five sections. Honest. The *what I would do differently* section is the test: if it contains nothing specific, write it again.

2. **(Evaluate)** Which supervisory capacity was hardest to exercise consistently across the simulation build? Design a practice exercise that targets that capacity specifically — for you, in your next build, and for your students in the classroom activities of Chapter 13.

3. **(Create)** Design the second simulation. What you would build with what the first one taught you. Start with the three files. The 45-minute scope test still applies. By the time you finish drafting the three files, you should be able to predict what the build will be hard at.

---

## Terminal deliverable

The teacher's post-build document for the interactive simulation. One document. Five sections. Honest about what worked and what didn't.

Plus the AGENTS.md that spans three build tiers — the artifact you carry forward to the next build.

Plus the simulation itself, deployed and in use.

Three deliverables. The post-build document is what makes the rest of them teach you something.

---

## Closing

You built it. Your students learned from it. You know what every decision cost you and what it gave you. You can sit next to a student in mid-build and say exactly where the line is, because you have drawn it yourself, on three increasingly hard builds.

That is what conducting looks like when it is complete.

The next build starts here.

---

## Classroom activity

Have students write a post-build document for *their* most recent build — the one from Chapter 14 of the students book, if they have been working through it, or the most recent build they completed in your class. Five sections. Honest. Peer review on whether the *what I would do differently* section names something specific.

This is the activity that closes the discipline for them as well as for you.

---

## Links

- *Codex for Students*: the companion book; the next read.
- CSTA: [csteachers.org](https://csteachers.org)
- The author's other books in this series: [nikbearbrown.com](https://nikbearbrown.com)

---

## What would change my mind

The chapter's strong claim is that **the post-build document is the artifact that converts the experience of building into the capacity to teach building** — that without the document, the build's lessons remain implicit and the teaching of the discipline is harder than it has to be.

If a controlled comparison — teachers who wrote post-build documents vs. teachers who did not — found no difference in next-build quality, no difference in their students' build-log quality, and no difference in their classroom-activity design quality, the post-build document becomes a personal-reflection tool rather than a teaching-discipline tool. The chapter would still recommend it; the framing would shift.

I expect the difference to be real because the post-build document forces *consolidation* — the same neurobiological mechanism that makes student struggle produce learning. Articulating what you would do differently is itself the cognitive work that makes the lesson durable.

---

## Still puzzling

- **The right cadence for post-build documents.** One per build? One per phase? One per major revision? Practitioners disagree. The book recommends one per build for the first few builds and lets the practice mature from there.

- **Whether to share post-build documents with other teachers.** The case for sharing: the practice matures faster across the field. The case against: post-build documents contain candid self-assessment that is easier to write when only the writer will read. Probably both modes exist — a candid version for you, a revised version for the CSTA community.

- **The second-build acceleration claim.** The book argues that the second simulation is smaller, faster, and better-scoped than the first. Whether this acceleration is reliably observed across teachers — and how many builds it takes for the framework to become implicit — is empirically untested.

---

## AI Wayback Machine

🕰️ **bell hooks** (1952–2021) — scholar, educator, and cultural critic whose *Teaching to Transgress: Education as the Practice of Freedom* (1994) argued that the teacher who has lived the practice is the teacher whose authority is rooted in something real. hooks called this *engaged pedagogy* — teaching that requires the teacher to be present, to be honest about what they do and do not know, to learn alongside students as a co-practitioner rather than perform the role of expert.[^1] The post-build document is engaged pedagogy applied to teacher-as-builder. The teacher who has built three tools, named where each one was hard, articulated what they would do differently, and shared the honest record with their students is teaching from a different ground than the teacher who is presenting a finished best-practices framework. hooks argued that this difference is felt by students even when it is not named. *(The TIKTOC originally specified Donald Schön — reflection-on-action — as the Wayback figure here. Schön is also at Chapter 7. The pantry research recommended bell hooks for this chapter to avoid the over-use and to strengthen the diversity of the book's Wayback figures. The substantive fit is excellent: hooks's "teacher as co-practitioner" is exactly the stance the post-build document operationalizes.)*

---

## The book ends.

You are now the practitioner. The next build is yours.

---

[^1]: hooks, b. *Teaching to Transgress: Education as the Practice of Freedom*. Routledge, 1994.

## Prompts

Use these prompts with Claude to generate interactive D3 v7 versions of the
figures in this chapter. Each produces a standalone HTML file you can open
in a browser and modify freely.

**Prerequisites:** Load `brutalist/CLAUDE.md` and `brutalist/DESIGN.md` into
your Claude project context before using these prompts. They define the stack,
naming conventions, color system, and typography the figures use.

---

### Figure 16.1 — The post-build document as the arc's terminal artifact

Create a standalone D3 v7 HTML file for Figure The post-build document as the arc's terminal artifact. Use the CDN https://cdnjs.cloudflare.com/ajax/libs/d3/7.9.0/d3.min.js, inline CSS, ResizeObserver redraw, SVG role="img", aria-labelledby, title, and desc. Build the figure from this structural brief: The post-build document as the arc's terminal artifact. A simple timeline from Chapter 0 (the teacher opens the terminal) to Chapter 14 (the teacher accounts for every decision). Five milestones labeled: first session / first page / grading tool / simulation deployed / post-build document. Editorial style.. Use the described data shape and labels; when exact values are not supplied, use plausible illustrative values that preserve the relationships in the brief. Use a zero baseline for bars or areas, direct labels where possible, and annotations named in the brief. Use only DESIGN.md color variables and the required serif/mono font split.

> Reference implementation: `d3/16-post-build-document-fig-01.html`
