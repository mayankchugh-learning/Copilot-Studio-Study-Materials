# Master File Order and Execution Plan
### Build a RAG Agent in Copilot Studio | by Mayank Chugh

This is the single reference for **which file to open, in what order, and what to do with it**. For a gentler walkthrough see `Copilot_RAG_Agent_Start_Here_Step_by_Step.md`.

## 1. All generated files in execution order

| Order | File | Type | When to use | Action | Output / done when |
|-------|------|------|-------------|--------|--------------------|
| 1 | `Copilot_RAG_Agent_Start_Here_Step_by_Step.md` | Guide | First | Skim the 6 phases and the file map | You know the route |
| 2 | `Copilot_RAG_Agent_YouTube_Episode_Plan.md` | Plan | Before anything else | Read goals, scope, timing table, scenario | You can state the episode goal in one sentence |
| 3 | `Copilot_RAG_Agent_Source_Analysis.md` | Analysis | After the plan | Read the rights statement and the validation table | List of items to check on recording day |
| 4 | `Copilot_RAG_Agent_Knowledge_Template.md` | Template (optional) | Before building the demo | Fill with real facts, or skip to keep the sample FAQ | Chosen FAQ content |
| 5 | `Copilot_RAG_Agent_Demo_Runbook.md` | Runbook | Demo preparation | Build the FAQ .docx, create the agent, add sources, run 4 tests | Agent works; 4 rehearsal screenshots |
| 6 | `Copilot_RAG_Agent_Improvements.docx` | Guide (3 pages) | After the demo works | Read sections 1 and 10; apply fixes | Corrections and open items settled |
| 7 | `Copilot_RAG_Agent_Speaker_Script.md` | Script | Rehearsal | Read aloud once; adjust wording | Comfortable delivery for each segment |
| 8 | `Copilot_RAG_Agent_YouTube_Lecture.pptx` | Deck (8 slides) | Alongside the script | Open in PowerPoint; check all slides and the speaker notes | Slides match script order |
| 9 | `Copilot_RAG_Agent_Recording_Notes_and_Publishing_Pack.md` **Part A** | Recording runbook | Right before recording | Set up screen, hide private details, set the take order | Ready to record |
| 10 | Same file, **Part B** | Teaching notes | Reference while rehearsing or editing | Check analogy, key ideas, further reading | Terminology consistent |
| 11 | Same file, **Part C** | Publishing pack | After editing | Pick title, paste description, add your own links, tags, pinned comment | Video published |
| 12 | Same file, LinkedIn post (in Part C) | Post | After publishing | Add the video link and post | Post live |
| 13 | `mayank-youtube-content-SKILL-v5.md` | Skill | Next video | Give it to Claude with your next source folder | New package generated |

## 2. Execution sequence with checkpoints

### Stage A: Understand (about 20 minutes)
1. Start Here guide, then Episode Plan, then Source Analysis.
- **Checkpoint A:** you have a list of items to validate and you know what is out of scope.

### Stage B: Prepare the demo (about 60 to 90 minutes)
2. Decide sample or real FAQ content (Knowledge Template, optional).
3. Follow the Demo Runbook sections 1 to 5 in order:
   1. Create the FAQ Word file.
   2. Create the agent (name, description).
   3. Paste the instructions.
   4. Turn open web search off.
   5. Upload the document, add the Microsoft Learn website, wait for **Ready**.
   6. Run the four tests and save screenshots.
- **Checkpoint B:** all four tests pass. If not, fix the instructions or sources and re-test.

### Stage C: Review and rehearse (about 60 minutes)
4. Read the Improvements guide (sections 1 and 10).
5. Read the Speaker Script aloud with the deck open.
6. Check slides and speaker notes (especially slide 5).
- **Checkpoint C:** script, slides and demo all follow the same order.

### Stage D: Record (about 60 to 90 minutes)
7. Read Recording Notes Part A and complete the pre-recording checklist.
8. Record in this order: demo segments, then slide and talking segments, then intro and outro.
- **Checkpoint D:** clean takes of all 8 segments. If the website source is not Ready, say so and use the rehearsal screenshot.

### Stage E: Publish (about 45 minutes)
9. After editing, update the chapter timestamps to match the final cut.
10. Use Part C: title, description, your own links, tags, pinned comment.
11. Post the LinkedIn text with the video link.
- **Checkpoint E:** video public, description complete, post live.

### Stage F: Reuse
12. Keep `mayank-youtube-content-SKILL-v5.md` for the next topic.

## 3. Dependencies (why this order)

| File | Depends on |
|------|-----------|
| Demo Runbook | Plan (scenario), Knowledge Template (if you use real facts) |
| Speaker Script | Demo Runbook (test questions and results) |
| Deck | Script (segment order) |
| Recording Part A | Demo Runbook validation, Script, Deck |
| Publishing Part C | Final edited video (for timestamps and your links) |

## 4. Shortest path if you have under two hours

1. Plan (5 min), then Demo Runbook (50 min).
2. Script, read once (20 min), then Deck check (10 min).
3. Recording Part A (10 min), then record the demo segments only.
4. Publish later using Part C.

## 5. Always validate on recording day

- Licence and access to Copilot Studio.
- Both knowledge sources show Ready.
- Screen labels and tab names match the script.
- No model names or limits shown on slides.
- Sample FAQ labelled as sample content.
- Your own links added; none invented.
