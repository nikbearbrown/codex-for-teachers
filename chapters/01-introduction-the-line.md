# Chapter 0 — Introduction: The Line


## TL;DR

- By the end of this chapter, you will be able to:.
- The chapter moves through Learning outcomes, Opening, What you will build, The two tracks, and related ideas.
- Read it for the main argument, the vocabulary it introduces, and the practical judgment it asks you to develop.

> There is a line between what Codex executes and what only you can do. This book teaches you to draw it — by building real things, then teaching students to draw it themselves.

---

## Learning outcomes

By the end of this chapter, you will be able to:

1. **(Understand)** Explain the difference between prompting Codex and conducting a build with Codex.
2. **(Understand)** Describe what the interleaved structure means for how to read this book.
3. **(Remember)** Identify the three builds that form the book's arc.

---

## Opening

Eighteen months ago, Seth was the one being managed.

He was a high school senior watching his classmates ace AP CS homework with AI and freeze on the unassisted quiz two weeks later. He noticed the pattern before he had vocabulary for it. He wrote the student book in this series — *Codex for Students* — to give other technically fluent students the operational discipline he had to build on his own.

He thought he understood the discipline. He had named it, framed it, taught it.

Then, eighteen months later, he tried to build something real with Codex. Not a homework assignment. Not a worked example. An actual classroom tool that another human being would use — a teacher he respected, a teacher who was already overwhelmed, a teacher who needed the thing to *work*.

The first build broke. Not in the obvious ways. The code ran. The tests passed. The output looked correct. Three days later, the teacher pointed out that the tool was processing student submissions from the *previous* semester too — silently, alongside the current ones. Codex had done exactly what Seth had specified. The specification was wrong, and Seth had not been there to catch it because he had not been *conducting* the build. He had been approving it.

That was the moment Seth understood the discipline from the inside.

This book is what he learned. The teacher who builds with Codex and the teacher who teaches students to build with Codex are the same person, practicing the same discipline. You cannot teach the line until you have drawn it yourself.

> *"Teachers are now building tools with Codex they always wanted but could never afford."* — OpenAI engineers, December 2025

You are about to become one of those teachers.

![The book's arc as three build tiers on](images/01-introduction-the-line-fig-01.png)
*Figure 1.1 — The book's arc as three build tiers on*

---

## What you will build

This book is structured around three builds. Each one is deployable in your actual classroom. Each one introduces the conducting concepts you will need for the next.

**Act One: a class website.** Low stakes. One page at a time. The website is the vehicle for learning the most important rule in the book — that nothing goes from Ask Mode to Code Mode without a reviewed plan — and for writing your first AGENTS.md, the file Codex reads at the start of every session.

**Act Two: a grading tool.** Higher stakes. The grading tool is where the conducting discipline starts to matter — where you experience what the rest of the book calls *the dangerous middle*: the moment when Codex produces output that passes every handoff condition you wrote and is still pedagogically wrong. You will rebuild the tool with narrower scope, add the verification techniques that catch the cases automation misses, and learn the supervisory work that the model structurally cannot do.

**Act Three: an interactive classroom simulation.** The build your students will use directly. The simulation is governed by three files — AGENTS.md (what Codex never improvises), DESIGN.md (every aesthetic decision specified or escalated), PROJECT.md (the intent layer that is yours, always). You will deploy it in front of thirty students. You will watch it break in ways your terminal could not have predicted. You will conduct a revision build based on what you observed. You will write a post-build document.

By Chapter 14 you will have shipped three classroom tools and designed fourteen classroom activities. You will have an AGENTS.md that spans three build tiers and reads as a record of how the discipline accumulates. You will be able to sit next to a student in mid-build and say exactly where the line is — because you have drawn it yourself, three times, on three increasingly hard builds.

---

## The two tracks

Every chapter in this book runs two tracks simultaneously.

The first track is **your build**. You read a chapter on handoff conditions and immediately apply it to the page you are adding to the class website. You read a chapter on AGENTS.md and immediately write one for your grading tool. The discipline does not land as theory; it lands as a thing you did this afternoon.

The second track is **your classroom**. The same chapter that taught you handoff conditions includes a classroom activity that teaches your students the same concept — usually starting from your build as the example. The students book in this series teaches the conducting discipline directly to students. This book teaches you the same discipline *and* gives you the classroom activity design that makes the students book teachable.

The two tracks are not parallel. They are interleaved. The teacher who reads a chapter and immediately applies it in both directions never has to translate the concept later. You finish every chapter already knowing how to teach it, because you just did both.

This is the structural commitment that makes the book work. It is also the reason the book is shorter than it would be otherwise. Every chapter does two jobs at once.

---

## How to use the students book alongside this one

Your students may have the companion volume — *Codex for Students*. Maybe you assigned it. Maybe a particular student found it on their own. Either way, the two books are designed to be used together.

The mapping is explicit. Chapter 13 of this book is a chapter-by-chapter map between what students are learning and what you now know how to teach. Until then, you can read the books in parallel without confusion: where the students book introduces a concept (the five supervisory capacities, AGENTS.md, the dangerous middle), this book gives you the *build experience* that lets you teach that concept from the inside.

If you have not read the students book, do not stop to read it now. Come back to it after Act Two. By then you will have built enough with Codex to recognize what Seth is describing.

---

## A practical note for teachers with thirty minutes on Monday night

The CSTA 2025 CS Teacher Landscape Report names what you already know: 74% of CS teachers have ten or more years of classroom experience; only 26% have ten or more years of CS teaching specifically; 96% participated in professional development in the past year; almost half did fewer than eleven hours of PD across the year. You are an experienced educator, early in your CS journey, doing the most you can in the time you have.[^1]

Two practical accommodations:

**Dictation.** On macOS, System Settings → Accessibility → Dictation (the double-tap-Shift-to-speak option is the fastest). On Windows, Win+H opens dictation in any text field. Speaking your specification prompts is materially faster than typing them and gives you a different relationship to the work — you describe what you want out loud and Codex begins. For a teacher with thirty minutes on Monday night, this is not a productivity hack; it is what makes the book tractable.

**Plan availability.** Codex is included with most ChatGPT plans as of 2026 — Free (rate-limited), Go, Plus, Pro, Business, Enterprise, Edu. Most of what this book teaches works on Plus ($20/month). Pro ($100/month) gives you significantly higher rate limits, which matters for Act Three's simulation build. School-issued ChatGPT Edu access works equivalently. If your district restricts AI tools and you cannot install Codex, see the deployment notes in the back matter — most of the conducting discipline transfers to any agentic coding tool.[^2]

---

## What this book is not

A few clarifications.

**This is not an AI ethics curriculum.** The book treats your students as builders to equip, not as plagiarism risks to manage. It treats you as a practitioner to support, not as a gatekeeper to install. Generic responsible-use frameworks are not in scope. If you need them, the *AI for Teachers* companion exists for that purpose.

**This is not a developer course.** The Vanderbilt and Coursera Codex courses are excellent if you want to delegate like a tech lead. This book teaches you to conduct like a composer — to specify what you want, review what Codex proposes, evaluate what it produces, and supply the judgment the model cannot. You do not need to be a developer to do this. You need to be willing to write specifications and evaluate output.

**This is not a content-generation guide.** The "ChatGPT for teachers" genre teaches you to use AI as a faster lesson-plan generator. This book teaches you something different: how to *build classroom tools* with Codex and how to *teach the discipline* of doing so. The lesson plan is downstream of the discipline. The discipline is the book.

What this book *is* is the practitioner handbook for the K-12 CS teacher who is both builder and instructor — who wants to make real classroom tools with Codex and wants their students to learn the same discipline the right way.

---

## What you will keep when you are done

When you reach Chapter 14, you will have produced two deliverables that travel with you.

The first is the **three classroom tools** themselves: a working class website, a grading tool calibrated to your subject, an interactive simulation deployed in front of your students. These are the obvious outputs.

The second deliverable is the one that matters more in the long run. It is **the AGENTS.md file that you carry from build to build**, plus a **post-build document** — a five-section honest record of what you built, what you delegated, what you kept, what you learned, what you would do differently. The AGENTS.md will become the most useful teaching artifact you have. You will show it to students. You will use it to start your next build faster. The post-build document is the thing that converts the experience of building into the capacity to teach building.

By Chapter 14 you will have the tools. You will also have the record of how you built them. Both deliverables are yours.

---

## Common misconceptions

This book lives downstream of four misconceptions worth naming now.

**"Codex is a better ChatGPT."** No. ChatGPT is a chat interface. Codex is an agentic system that plans multi-step tasks, executes shell commands, reads and writes files, and iterates autonomously. The autonomy is the feature *and* the reason you need a different discipline before you start. A chat conversation does not act on your filesystem; Codex does. Chapter 1 is the first session, where this distinction lands.

**"I need to be a developer to use Codex."** No. The teacher-as-builder pattern requires *specification writing* and *verification* — not deep coding ability. If you can describe a classroom tool clearly enough that a competent intern could build it, you can conduct Codex. If you can evaluate whether the output matches your description, you can verify. Most of the cognitive work of this book is pedagogical work in a new register, not coding work.

**"AI for teachers means faster lesson plans."** That is one use, and it is not what this book teaches. Lesson plans are content generation. Classroom *tools* — websites, grading aids, simulations — are builds. This book is about builds.

**"My students know more about AI than I do, so I cannot teach this."** Partially true; not relevant. Your students may know more about Codex's UI than you do. They almost certainly do not know what *the conducting discipline costs when it is skipped*. The teacher who has built three real tools with Codex knows something the technically fluent student does not: how silent failures feel from the inside, what the cost of forward correction is, what plausibility auditing actually catches. That is what you have to teach. By Chapter 14 you will have lived it three times.

---

## Exercises

1. **(Remember)** Name the three builds in this book's arc and the conducting concept each one introduces. (Look back at "What you will build" if needed.)

2. **(Understand)** What is the difference between a teacher who uses Codex to generate lesson plans and a teacher who conducts Codex through a classroom build? Write one paragraph.

3. **(Understand)** Read Chapter 0 of the students book (*Codex for Students*) if you have it. Name one concept Seth learns there that you will eventually teach using your own build experience. If you do not have the students book, name one moment in your own teaching where you watched a student "use AI" in a way that made you uneasy. You will return to this moment in Chapter 13.

---

## What would change my mind

The book stakes one strong empirical claim and one strong operational claim. Both could be wrong.

The empirical claim: that AI-assisted learning *without* a conducting discipline produces a measurable gap between practice performance and unassisted performance — a homework/quiz gap that the Bastani RCT measured at 17 percentage points on the unassisted exam.[^3] If a sufficiently large follow-up RCT, conducted with a contemporary frontier model and a more representative student population, fails to replicate this gap — or shows that the gap closes within six months of unassisted practice — the empirical foundation of the book softens. The operational discipline still helps; the urgency drops.

The operational claim: that the teacher who builds *and then teaches* learns more than the teacher who only teaches. If a controlled study of K-12 CS teacher PD compared teachers who used this book (build + teach) to teachers who used a teaching-only version (no builds) and found no meaningful difference in classroom outcomes — student conducting fluency, student supervisory-capacity demonstration in build logs — the interleaved structure becomes optional rather than load-bearing. The book would still work; it would no longer require the second track.

Either finding would require revising this chapter.

---

## Still puzzling

A few questions this book opens but does not close:

- **How much of the discipline transfers between agentic tools?** The framework is written for Codex. The conducting discipline applies — by argument, not by measurement — to Claude Code, Gemini, and successor systems. The student book in the Claude Code series exists precisely because the *operational* discipline differs in detail even when the framework holds. Whether teachers who learn the discipline in Codex transfer it cleanly to other tools is open.

- **Does the homework/quiz gap appear in non-CS subjects with the same magnitude?** Bastani measured math; Kosmyna measured essay writing; the Anthropic 2026 RCT measured Python developers learning a new library. The gap appears in every domain measured so far. Whether it appears in, for example, AP Chemistry lab work or AP Literature analysis at the same scale is open.

- **What is the right age for the conducting discipline?** This book assumes K-12 CS teachers and high-school students. The same framework may or may not work for middle school. The empirical foundation in younger learners has not been tested.

These questions are the live edge of the field. The book does not pretend otherwise.

---

##  AI Wayback Machine
 **John Dewey** (1859–1952) — philosopher of education whose argument that *the teacher learns by teaching* underlies the interleaved structure of this book. Dewey's concept of "reflective practice" holds that making a discipline explicit for students deepens the teacher's own understanding of it — that the act of teaching is itself a form of inquiry. In *Experience and Education* (1938) he wrote that the educator's task is to organize "experiences that arouse a genuine desire for further knowledge."[^4] Every chapter of this book is built on Dewey's claim: your build is the experience; teaching that experience to your students is what consolidates what you learned in building it.

---

## Bridge

The reader knows the arc. Chapter 1 puts them in their first Codex session — where the difference between agentic Codex and chat-style ChatGPT becomes visible from the inside, and the first rule of the book lands: nothing goes from Ask Mode to Code Mode without a reviewed plan.

---

[^1]: Computer Science Teachers Association, *The 2025 CS Teacher Landscape Report* (csteachers.org, fall 2024 survey). Full interactive data at landscape.csteachers.org.
[^2]: OpenAI, Codex pricing (developers.openai.com/codex/pricing). [verify — confirm Free/Go/Plus/Pro/Business/Enterprise/Edu plan list and Codex availability at press.]
[^3]: Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakcı, Ö., Mariman, R. "Generative AI without guardrails can harm learning: Evidence from high school mathematics." *PNAS* 122 (2025). The 17-percentage-point gap is the GPT Base arm vs. control on the unassisted exam.
[^4]: Dewey, J. *Experience and Education*. Macmillan, 1938. The Kappa Delta Pi reprint (1998) is the standard recent edition.
