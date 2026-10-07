---
name: mayank-youtube-content
description: >
  Generalized YouTube educational-content production skill. Converts a folder of
  heterogeneous learning/source materials—PPTX, DOCX, PDF, TXT, MD, transcripts,
  XLSX/CSV, images, notebooks, code, and related reference files—into a coordinated
  YouTube teaching package for planning, preparing, executing, recording, and publishing
  an educational video. The workflow is source-first, evidence-grounded, and topic-aware.
  It does not force a Jupyter notebook unless the topic genuinely requires one.
  Trigger on requests such as: prepare YouTube content from training files, create a
  video plan from my course materials, make slides/script/runbook, prepare a recording
  package, convert Udemy learning material into a YouTube tutorial, or generate the
  complete YouTube content package. v5 also triggers on: make this content mine,
  change the links/branding of a course, check source rights/originality, build an
  AI-agent/RAG demo package, or finish a staged package.
---

# Mayank YouTube Content Skill — Generalized v5

## What changed in v5

- **Rights, Ownership & Originality Gate (Section 4A).** Every source is classified
  before use. Third-party material is a topic map only and is never re-skinned.
- **Demo knowledge-source and test design (Section 15A)** for AI agent / RAG / chatbot
  episodes: owned, official or synthetic sources; refusal-first testing.
- **Delegation, staging and defaults (Section 28A):** what to do when the user says
  "do it best from your knowledge", and how to stage large packages.
- **Transcript/caption error handling and a volatile-facts rule** (Section 3).
- **New QA blocks** (Rights & Originality QA, Agent / RAG Demo QA) and rules 16-22.
- Conditional outputs added: Demo Knowledge Pack and Knowledge Template.
- Fixed a stray code fence in Section 21.


## 1. Purpose

This skill converts a collection of learning materials from a course, Udemy training,
book, workshop, internal training, or research topic into a **complete YouTube production
package**.

The source folder may contain:

- PPT/PPTX
- Word/DOCX
- PDF
- TXT/MD
- transcripts
- XLS/XLSX/CSV
- images/diagrams/screenshots
- Jupyter notebooks
- Python/JavaScript/SQL/code files
- configuration files
- URLs/reference documents
- previously created notes

The objective is NOT to reproduce the source material.

The objective is to produce material that helps the instructor:

1. understand and organize the topic;
2. decide what belongs in the YouTube episode;
3. plan the teaching flow;
4. prepare slides and demonstrations;
5. execute the technical steps;
6. record the video confidently;
7. publish supporting content afterward.

### Core principle

**Source material is the evidence base. The YouTube package is a teaching adaptation.**

Never silently invent facts, statistics, examples, commands, API behavior, benchmark
results, screenshots, or execution results that are not supported by the supplied sources.

If outside research is explicitly requested, clearly distinguish:

- Source-derived information
- Verified external information
- Instructor inference/recommendation
- Items requiring validation during recording

---

# 2. Default Output Philosophy

Do NOT automatically generate a fixed number of files.

Generate the **Core Package** for every topic and add **Conditional Packages** only when
they are relevant.

## Core Package — normally required

| # | File | Format | Purpose |
|---|------|--------|---------|
| 1 | Source Analysis & Coverage | MD | What was found, where it came from, gaps, conflicts |
| 2 | YouTube Topic & Episode Plan | MD | Episode scope, objectives, audience, teaching flow |
| 3 | YouTube Notes / Learning Guide | MD | Clean instructor reference and conceptual structure |
| 4 | Slide Deck | PPTX | Presentation-ready teaching slides |
| 5 | Speaker Script | MD | What to say slide-by-slide and section-by-section |
| 6 | Recording Runbook | MD | Exact plan for recording the episode |
| 7 | Demo / Execution Runbook | MD | Step-by-step technical demo execution, if applicable |
| 8 | Improvements & Technical Guide | DOCX | Technical depth, corrections, modernization, improvements |
| 9 | YouTube Publishing Pack | MD | Title, description, chapters, tags, CTA, resources |
| 10 | LinkedIn Promotion | MD | LinkedIn post promoting the video |

## Conditional Outputs

Create these only when justified by the source material or requested workflow:

| File | When to create |
|------|----------------|
| Medium Blog | Topic has enough depth for a long-form article |
| Architecture Diagram Spec | Architecture/system-design topic |
| Mermaid Architecture | Architecture/process topic where a reusable diagram helps |
| Code Walkthrough | Substantial code/demo is present |
| Demo Data / Query Pack | Demo requires queries, prompts, test data, payloads |
| Troubleshooting Guide | Technical setup has likely failure points |
| Recording Checklist | Complex multi-platform recording |
| Thumbnail Brief | User wants thumbnail planning |
| Shorts Pack | User wants Shorts derived from the episode |
| Quiz / Q&A | Training/educational topic benefits from learner questions |
| Source-to-Slide Matrix | Large source folder or many source documents |
| Notebook | ONLY when executable notebook content is central to the episode |
| Clean Notebook | ONLY when notebook execution is part of the actual YouTube demo |
| Demo Knowledge Pack | AI agent / RAG / chatbot demos that need sample documents, agent instructions, and a test-question set |
| Knowledge Template | The demo needs real facts only the user can supply (FAQ, policies); gives a fill-in form |

The previous notebook-first behavior is removed. A notebook is now an **optional execution
artifact**, not a mandatory deliverable.

---

# 3. Source Priority and Evidence Rules

When multiple files discuss the same subject, establish a source hierarchy.

Default priority:

1. Executed code / actual outputs
2. User-provided project/code/configuration files
3. User-provided instructor transcript
4. User-provided lecture slides
5. User-provided written notes
6. User-provided reference PDFs/books
7. User-provided spreadsheets/data
8. Explicitly requested external research
9. General model knowledge

Do not use a lower-priority source to contradict a higher-priority source without
flagging the discrepancy.

## Source conflict handling

Create a table:

| Topic | Source A | Source B | Resolution | Recording Action |
|------|-----------|-----------|------------|------------------|

Possible resolutions:

- Prefer executed result
- Prefer current project code
- Preserve both as historical/current
- Mark for validation
- Ask user if the conflict materially changes the video

Never silently reconcile contradictory material.

## Transcript and caption quality

Spoken transcripts and auto-captions contain errors: acronym expansions, product
names, numbers, and half-finished sentences. Cross-check key terms against official
documentation and correct them in the on-camera wording. Example: RAG means
Retrieval-Augmented Generation, whatever the transcript says. Record corrections in the
conflict table.

## Volatile facts

Model names, licence plans, file-size limits, quotas, prices, preview features and UI
labels change often. Do not put them on slides. Mark them **validate on recording day**.

---

# 4. Step 0 — Inspect the Source Folder

Before generating content:

1. Inventory all supplied files.
2. Classify each file by type and likely purpose.
3. Extract text/content where supported.
4. Identify duplicate or near-duplicate material.
5. Identify source relationships.
6. Identify the main topic and possible episode boundaries.
7. Detect code, datasets, diagrams, transcripts, and demonstrations.
8. Record missing information.

Create a source inventory:

| File | Type | Likely Purpose | Topic | Key Content | Reliability | Used In |
|------|------|----------------|-------|-------------|-------------|---------|

Do not assume the newest-looking file is authoritative unless the evidence supports it.

---

# 4A. Step 0B — Rights, Ownership & Originality Gate

Run this straight after the inventory and before analysing content.

### 1. Look for ownership signals

Author or instructor credits, copyright or "All rights reserved" notices, course or
company branding, logos and trademarks, licence terms, and platform terms (for example a
Udemy course).

### 2. Classify every source

| Class | Meaning | Allowed use |
|-------|---------|-------------|
| Own | Created by Mayank | Adapt freely; keep his teaching flow |
| Licensed | Written permission or open licence | Adapt within the licence; attribute as required |
| Third-party | Another author's course, slides, transcripts, prompts, logos | Topic map and personal learning only |
| Unknown | No ownership signals | Treat as third-party until Mayank confirms |

### 3. Rules for Third-party and Unknown sources

- Do NOT reuse: wording or transcript phrasing, slide layouts or diagrams, prompt text,
  scenarios, practice exercises, example topics, test questions, logos, business names, or
  the lecture sequence.
- Do NOT "re-skin" the material (swap names, links or branding). It is still the same work.
- DO use general, non-proprietary knowledge: concepts, standard definitions, product facts,
  and steps that are inherent to the product.
- Build an original episode: own scenario, own demo data, own prompts, own diagrams, own
  script and structure, with every step validated in the product itself.
- Do not create a line-level Source-to-Slide matrix for these sources. Use a concept-level
  coverage map instead.
- Offer, but do not force, a one-line credit if a named course helped him learn.

### 4. When the user asks to "make it mine"

If the user asks to change links, names or branding of third-party material, say once,
briefly and without lecturing, what belongs to the author. Then offer the original-build
path and continue with it. Refuse the re-skin, not the topic.

### 5. Third-party brands in demos

Avoid real businesses, their websites or logos as demo subjects unless the topic needs
them. Prefer Mayank's own scenario or clearly synthetic data. Never imply affiliation.

### 6. Record the outcome

Add a **Rights & Originality Statement** to the Source Analysis: the classification
table, what was used, and what was deliberately not used.

---

# 5. Step 1 — Analyze the Learning Material

Extract:

- Core topic
- Candidate episode title
- Audience
- Prerequisites
- Learning objectives
- 3–7 major concepts
- Important terminology
- Analogies/examples
- Real-world use cases
- Architecture/process flows
- Code and packages
- Tools/platforms
- Commands/configuration
- Tables/data
- Statistics/facts
- Exercises/labs
- Common mistakes
- Troubleshooting information
- Source references
- Possible visual demonstrations
- Possible browser/platform switches

Also determine whether the topic should be:

- one YouTube episode;
- multiple episodes;
- a tutorial + conceptual episode;
- a short-form + long-form combination;
- or a playlist/module.

If the material is too large for one episode, recommend a series rather than compressing
everything into one video.

---

# 6. Step 2 — Define the YouTube Episode

Every episode plan should define:

### Episode identity

- Working title
- Final title candidates
- Episode number, if applicable
- Series name
- Target audience
- Difficulty
- Estimated duration
- Prerequisites

### Learning outcome

By the end of the video, the viewer should be able to:

1. ...
2. ...
3. ...

### Scope

Explicitly state:

**Included**
- ...

**Not included**
- ...

This prevents course material from overwhelming the YouTube episode.

---

# 7. Step 3 — Build the Teaching Narrative

Prefer this structure unless the topic requires another sequence:

1. Hook / Why should the viewer care?
2. What this video is and is not
3. Prerequisites / safe-use notes
4. Problem
5. Concept
6. Architecture / mental model
7. Simple analogy
8. Step-by-step implementation
9. Demo / live execution
10. Results / interpretation
11. Common mistakes
12. Practical use case
13. Key takeaways
14. Next step / CTA

Respect the instructor's original teaching flow where it is pedagogically strong
(own or licensed materials only; for third-party material follow Section 4A).

Do not mechanically reproduce a course lecture.

---

# 8. Step 4 — Safety and Responsible-Use Review

For technical topics, add a concise safety section where relevant.

Examples:

- Never expose API keys/secrets.
- Never paste credentials into public AI tools.
- Do not expose customer/private data.
- Use synthetic/demo data for recording.
- Mask account IDs and sensitive URLs.
- Review generated code before execution.
- Confirm destructive commands before running.
- Respect software/data licensing.

For AI topics, distinguish:

- model-generated content;
- retrieved evidence;
- verified facts;
- instructor interpretation.

---

# 9. Step 5 — Slide Deck Planning

Default: 8–15 slides for a focused YouTube episode.

Use more only when the topic genuinely requires it.

Suggested structure:

| Slide | Purpose |
|------|---------|
| 1 | Title / branding |
| 2 | What are we learning? |
| 3 | Problem / motivation |
| 4 | Core concept |
| 5 | Architecture / mental model |
| 6 | Analogy / simplified explanation |
| 7 | Step-by-step flow |
| 8 | Demo setup |
| 9 | Demo/result |
| 10 | Common mistakes |
| 11 | Real-world use case |
| 12 | Key takeaways |
| 13 | Next steps / CTA |

Slides must be visually useful, not transcript dumps.

## Slide rules

- 3–6 concise bullets maximum where possible.
- Prefer diagrams, flows, comparison tables, and callouts.
- Keep code on slides minimal.
- Move detailed code to the demo/runbook.
- Use consistent terminology with source material.
- Do not fabricate screenshots.
- Clearly label illustrative diagrams as illustrative.

---

# 10. PPTX Design Standard

Default palette:

```text
darkBg:   0A1628
midBg:    0D2137
teal:     00B4D8
orange:   FF6B35
green:    4CAF82
purple:   9B72CF
lightTxt: E8F4FD
subTxt:   90B8D4
cardBg:   102235
white:    FFFFFF
```

Rules:

- Do not use `#` in pptxgenjs hex values.
- Use factory functions for reusable styles/shadows.
- Use accessible contrast.
- Do not overcrowd slides.
- Architecture labels must match actual technologies used.
- Never use placeholder metrics when actual results exist.
- Render and visually inspect every slide before delivery.

---

# 11. Speaker Script

The speaker script is separate from the slides.

For every slide/section include:

```text
[SLIDE N — Title]

Purpose:
What the viewer should understand.

Opening:
...

Main explanation:
...

Example / analogy:
...

Demo transition:
...

Key emphasis:
...

Transition:
...
```

The script should sound natural when spoken.

Avoid reading slide bullets verbatim.

## Standard opening

Use when appropriate:

"Hello guys! My name is Mayank Chugh and welcome to my YouTube channel!"

Then immediately establish:

- what the viewer will learn;
- why it matters;
- what will be demonstrated;
- what prerequisites are required.

## Standard closing

Use when appropriate:

"I'm Mayank Chugh, thank you for watching! Please Like, Share, and Subscribe. Take care!"

---

# 12. Recording Runbook

This is one of the most important outputs.

It must allow the instructor to record the episode without repeatedly returning to
the source material.

Include:

## A. Pre-recording checklist

- Source files reviewed
- Slide deck ready
- Script reviewed
- Demo environment ready
- Accounts authenticated
- API keys available securely
- Secrets hidden
- Browser tabs prepared
- Screen resolution checked
- Microphone checked
- Camera checked
- Recording software checked
- Sample data prepared
- Backup plan prepared

## B. Recording sequence

For each segment:

```text
SEGMENT N
Duration:
Environment:
Slide:
Screen:
Action:
What to say:
Expected result:
If it fails:
Transition:
```

## C. Platform switch markers

Use:

```text
[SHOW SLIDE N]
[SWITCH TO BROWSER]
[SWITCH TO CONSOLE]
[SWITCH TO TERMINAL]
[SWITCH TO IDE]
[SWITCH TO NOTEBOOK]
[COME BACK TO SLIDES]
[PAUSE]
[RUN]
[WAIT]
[SHOW RESULT]
```

Only include platforms actually required by the topic.

---

# 13. Demo / Execution Runbook

Create this whenever the episode includes implementation.

For each demo:

### Prerequisites

- Software
- Versions
- Accounts
- Packages
- Environment variables
- Dataset
- Files
- Expected runtime

### Execution

For each step:

```text
STEP N — Description

Action:
Command/code/navigation:

Expected output:

What to explain:

Validation:

Common failure:

Recovery:
```

Never invent expected output.

If actual execution has not been performed, explicitly label expected output as:

**Expected / must be validated during recording.**

If executed artifacts are supplied, use their actual outputs.

---

# 14. Code and Technical Accuracy

When code is supplied:

- Preserve actual package names and imports unless recommending a documented update.
- Identify deprecated APIs.
- Identify version-sensitive behavior.
- Separate "source code" from "recommended improvement".
- Do not silently rewrite working code.
- Do not invent package versions.
- Do not invent command output.

Create a technical changes table where useful:

| Original | Current/Recommended | Why | Validation Needed |
|----------|---------------------|-----|-------------------|

---

# 15. Browser / Platform Demonstrations

Whenever recording requires a browser portal, document:

```markdown
## ⏸️ PLATFORM SWITCH — [Purpose]

[SWITCH TO BROWSER]

Open:
[URL or navigation path]

Step 1:
- ...

Step 2:
- ...

Capture/show:
- ...

Do NOT show:
- secrets
- personal information
- unrelated account details

What to say on camera:
> "..."

[COME BACK TO SLIDES]
```

Do not assume UI labels are current unless supported by supplied screenshots or verified
external research.

If UI details may have changed, label them:

**UI may differ by account/version — validate immediately before recording.**

---

# 15A. Demo Knowledge Sources and Test Design (AI agent / RAG / chatbot topics)

### Choosing knowledge sources

Priority order:

1. Content Mayank owns or controls.
2. Official public documentation (stable, factual, well structured).
3. Synthetic documents written for the demo.

Avoid volatile commercial pages (promotions, prices) and sites the user does not control.

- Verify platform constraints from official documentation before recommending a source
  (for example indexing, URL depth, authentication) and record them as
  **Verified external information**.
- Never invent URLs. If the user delegates the choice, pick a stable public URL that
  appeared in verified results or official documentation, and label it
  **validate on recording day**.

### Sample data

- Label sample documents as sample content, on camera and in the description.
- Real facts come only from what the user supplied or stated. Never invent fees, dates,
  prerequisites, policies or contact details.
- Deliberately leave some facts out so the agent can be shown refusing correctly.
- No personal data in demo documents. Hide tenant and account details.

### Instruction and setting consistency

Check that the agent instructions match its settings. If the instructions say "answer only
from my sources", open web search must be off, and the video should show that setting.

### Minimum test set

| Test | Purpose |
|------|---------|
| Answered from the document | Shows document grounding |
| Answered from the website | Shows web-source grounding |
| Not in any source | Must decline rather than invent |
| Out of scope or trick question | Shows guardrails |

- Show the source citation for each answer.
- Capture rehearsal screenshots as a fallback. Show real behaviour on camera and never
  edit answers.
- Label expected outputs: **Expected / must be validated during recording.**

---

# 16. Notes / Learning Guide

The Notes MD is the instructor's clean reference.

Recommended structure:

```markdown
# Topic
### by Mayank Chugh

## 1. Learning Objectives

## 2. Prerequisites

## 3. Core Concepts

## 4. Architecture / Mental Model

## 5. Step-by-Step Explanation

## 6. Examples and Analogies

## 7. Demo Summary

## 8. Common Mistakes

## 9. Real-World Applications

## 10. Key Takeaways

## 11. Further Learning

## Source Material
```

Do not place the full speaker script here.

---

# 17. Improvements & Technical Guide

DOCX should contain:

- Technical corrections
- Modernization opportunities
- Architecture improvements
- Code quality improvements
- Security improvements
- Performance considerations
- Production-readiness considerations
- Version/package migration notes
- Teaching improvements
- Suggested demo improvements
- Common learner misunderstandings

Do not turn this into another transcript.

Use code blocks where they materially help.

---

# 18. Publishing Pack

Generate:

### YouTube

- 3–5 title candidates
- Recommended title
- Description
- Chapter structure
- Prerequisites
- Key learning points
- Resources
- CTA
- 10–15 relevant tags
- Tags must remain within YouTube's practical character constraints when requested.

### Optional

- Thumbnail text
- Thumbnail concept
- Pinned comment
- Community post
- Shorts ideas

Do not invent URLs. Preserve supplied URLs exactly and clearly identify their purpose.

---

# 19. LinkedIn Promotion

Create a separate LinkedIn post.

Default structure:

1. Strong first-two-line hook
2. Why the topic matters
3. What the video teaches
4. Practical outcome
5. Watch/CTA
6. 3–5 hashtags

Keep the LinkedIn post native and readable.

---

# 20. Medium Blog

Create only when useful.

It should NOT be a copy of the speaker script.

Use:

- Problem
- Concept
- Architecture
- Implementation
- Lessons learned
- Common mistakes
- Practical use case
- Conclusion

If source material contains a paper/reference, cite it accurately.

---

# 21. Source-to-Output Traceability

For large or mixed-source folders, create:

```text
Source-to-Slide Matrix
```

Example:

| Source | Section | Used In | Purpose |
|--------|---------|---------|---------|
| File A | Page 12 | Slide 4 | Architecture |
| File B | Section 3 | Demo Runbook Step 5 | Implementation |
| Transcript | 18:20 | Speaker Script | Analogy |

This applies to Own and Licensed sources. For Third-party sources use a concept-level
coverage map (Section 4A).

This prevents important source material from being lost.

---

# 22. Quality Assurance

Before delivery, perform these checks.

## Content QA

- [ ] Topic is clearly defined.
- [ ] Learning objectives are measurable.
- [ ] Scope is realistic for one episode.
- [ ] No unsupported facts were invented.
- [ ] Source conflicts are documented.
- [ ] Terminology is consistent.
- [ ] Analogies are preserved where useful.
- [ ] Demo steps are executable or explicitly marked for validation.

## Technical QA

- [ ] Package/import names checked.
- [ ] Commands checked against supplied material.
- [ ] Secrets are not exposed.
- [ ] Destructive actions are clearly identified.
- [ ] Expected outputs are distinguished from actual outputs.
- [ ] Version-sensitive items are flagged.

## Recording QA

- [ ] Every slide has a purpose.
- [ ] Every demo has a transition.
- [ ] Browser/platform switches are explicit.
- [ ] Narration exists for important actions.
- [ ] Failure/recovery paths exist for important demos.
- [ ] Recording order is practical.

## Publishing QA

- [ ] Title is clear and searchable.
- [ ] Description matches actual video.
- [ ] Chapters correspond to actual sections.
- [ ] Tags are relevant.
- [ ] Links are verified/provided by the source material.
- [ ] CTA is included.

## PPTX QA

- [ ] Every slide rendered.
- [ ] No text overflow.
- [ ] No clipped diagrams.
- [ ] Fonts are readable.
- [ ] Colors have sufficient contrast.
- [ ] Speaker notes are present.
- [ ] Actual metrics are used where available.

## Rights & Originality QA

- [ ] Every source is classified Own, Licensed, Third-party or Unknown.
- [ ] No third-party wording, prompts, slides, scenarios, logos or exercises were reused.
- [ ] Scenario, demo data, prompts, diagrams and script are original.
- [ ] No real business or website is a demo subject without a reason and a disclaimer.
- [ ] A credit line was offered where a named course inspired the topic.

## Agent / RAG Demo QA

- [ ] Knowledge sources are owned, official or synthetic, and constraints were verified.
- [ ] Sample data is labelled and no facts were invented.
- [ ] Agent instructions match the enabled settings.
- [ ] Tests cover grounded, unknown and out-of-scope questions.
- [ ] Rehearsal screenshots exist and citations are shown.
- [ ] Model names and UI labels are flagged for validation.

---

# 23. Conditional Notebook Policy

A Jupyter notebook is NOT a default output.

Create a notebook only if at least one is true:

1. The YouTube episode teaches notebook-based execution.
2. The source material contains important executable notebook content.
3. The user explicitly asks for a notebook.
4. The notebook itself is the primary demonstration artifact.

If created, produce:

- `Topic_WithTranscript.ipynb` only when narration synchronization is needed.
- `Topic_Clean.ipynb` when a clean viewer-facing notebook is useful.

Do not create notebook gold blocks merely because the source folder contains a notebook.

---

# 24. Optional Architecture / Diagram Outputs

For architecture-heavy topics, generate:

```text
[Topic]_Architecture_Mermaid.md
```

Include:

- Mermaid diagrams
- ASCII fallback
- Diagram explanation
- Slide mapping
- Recording narration

Do not rely on Mermaid alone for the PPTX.

---

# 25. Optional Q&A / Learner Support

For educational topics, generate:

```text
[Topic]_Interview_and_QA.md
```

Include:

- Beginner questions
- Intermediate questions
- Advanced questions
- "Why?" questions
- Troubleshooting questions
- Interview-style questions
- Answers grounded in the supplied material

Do not invent claims unsupported by the source.

---

# 26. Recommended File Naming

Use a topic slug.

Core:

```text
[Topic]_Source_Analysis.md
[Topic]_YouTube_Episode_Plan.md
[Topic]_Notes.md
[Topic]_YouTube_Lecture.pptx
[Topic]_Speaker_Script.md
[Topic]_Recording_Runbook.md
[Topic]_Demo_Runbook.md
[Topic]_Improvements.docx
[Topic]_YouTube_Publishing_Pack.md
[Topic]_LinkedIn_Post.md
```

Conditional:

```text
[Topic]_Medium_Blog.md
[Topic]_Architecture_Mermaid.md
[Topic]_Interview_and_QA.md
[Topic]_Troubleshooting.md
[Topic]_Shorts_Pack.md
[Topic]_WithTranscript.ipynb
[Topic]_Clean.ipynb
[Topic]_Demo_Knowledge_Pack.md
[Topic]_Knowledge_Template.md
```

---

# 27. Branding Constants

Default YouTube introduction:

"Hello guys! My name is Mayank Chugh and welcome to my YouTube channel!"

Default outro:

"I'm Mayank Chugh, thank you for watching! Please Like, Share, and Subscribe. Take care!"

Default byline:

"by Mayank Chugh"

Default technical branding when appropriate:

"AI Engineer • Azure • GenAI • RAG"

Known profile links may be included only when they are supplied/approved for the
specific publishing package. Do not invent or alter URLs.

---

# 28. Final Delivery Rule

The final package should be presented in this order:

1. Source Analysis
2. Episode Plan
3. Notes
4. PPTX
5. Speaker Script
6. Recording Runbook
7. Demo Runbook
8. Improvements DOCX
9. YouTube Publishing Pack
10. LinkedIn Post
11. Conditional files

The user should be able to answer:

> "What do I teach?"
> "What do I show?"
> "What do I say?"
> "What do I execute?"
> "What do I do if the demo fails?"
> "What files support the recording?"
> "What do I publish afterward?"

without reopening the original course material during recording.

---

# 28A. Delegation, Staging and Defaults

- **Delegation.** If the user says "do it best from your knowledge", choose sensible
  defaults, state the assumptions in one line, and proceed. Use placeholders or deliberate
  omissions instead of inventing facts, URLs or real details.
- **Blocking decisions.** If one decision affects every file (scenario, rights, source of
  truth), ask one concise question, or deliver the Source Analysis and Episode Plan first
  with the decision marked.
- **Staging.** For large packages deliver text files first, then build the PPTX as its own
  step (build, render, inspect), then conditional files. Always say what remains.
- **Compact mode.** For a single focused episode, the Recording Runbook, Notes and
  Publishing Pack may share one file. Keep the Source Analysis, Episode Plan, Speaker
  Script, Demo Runbook and Deck separate. State which packaging was chosen.
- **Synchronization.** When a decision changes (for example the website source), update
  every affected file and the validation table.
- **Hand-off.** Present the files with a short summary: what is included, what to check
  before recording, and what remains.

---

# 29. Most Important Rules

1. **Source-first.**
2. **Do not invent evidence.**
3. **Do not force notebooks.**
4. **Do not force every possible output.**
5. **Prefer a coherent episode over dumping all course content into one video.**
6. **Separate slides, narration, execution instructions, and technical improvements.**
7. **Use actual execution results when available.**
8. **Clearly label anything that still needs validation.**
9. **Protect credentials and private data.**
10. **Every recording action should have an associated narration or explanation.**
11. **Every important demo should have a failure/recovery path.**
12. **Keep all deliverables synchronized.**
13. **Use source traceability for large collections.**
14. **Render and inspect PPTX before delivery.**
15. **Generate conditional artifacts only when they materially improve the YouTube workflow.**
16. **Classify source ownership before using anything.**
17. **Never re-skin third-party material; build an original episode.**
18. **Prefer owned, official or synthetic knowledge sources, and never invent URLs.**
19. **Test refusals, not only happy paths.**
20. **Make agent instructions match the enabled settings.**
21. **When the user delegates, state assumptions and proceed; stage large packages.**
22. **Update every affected file when a decision changes.**
