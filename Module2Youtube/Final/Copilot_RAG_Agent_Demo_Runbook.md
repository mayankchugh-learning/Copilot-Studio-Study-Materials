# Demo Runbook: Build the Agent Live
### by Mayank Chugh

Everything below is original. The demo document is **sample content for the video**. Tell viewers it is a demo FAQ.

## 1. Agent settings

| Field | Value |
|-------|-------|
| Name | AI Pioneers Learner Concierge |
| Description | Answers learner questions about the AI Pioneers programme from its FAQ document, and answers Copilot Studio how-to questions from Microsoft's documentation. |
| Open web search | **Off** (show this on camera) |
| Knowledge 1 | Upload `AI_Pioneers_Demo_FAQ.docx` (text in section 2) |
| Knowledge 2 | Public website: `https://learn.microsoft.com/microsoft-copilot-studio/` |
| Model | Whatever your tenant offers; **don't name it on slides** |

## 2. Demo FAQ document (paste into Word, save as .docx)

**AI Pioneers: Demo FAQ (sample content for a tutorial video)**

**What is AI Pioneers?**
AI Pioneers is a live, virtual programme in GenAI and RAG engineering. Cohort 1 runs for 8 weeks.

**Who is it for?**
It is designed for IT professionals who want to build practical GenAI and RAG skills.

**How is it delivered?**
Sessions are live and online. Each session lasts 90 minutes.

**How is a session structured?**
Each 90-minute session follows the same rhythm: a 10-minute warm-up, 20 minutes of concepts, 40 minutes of live coding, a 15-minute lab and a 5-minute wrap-up.

**What materials do participants get?**
Participants work with slide decks, Jupyter notebooks and Streamlit demo apps.

**Is there homework?**
Yes. The programme includes 8 homework assignments.

**Who teaches the programme?**
Mayank Chugh, a cloud and enterprise architect and GenAI instructor.

> The FAQ deliberately says nothing about fees, dates, prerequisites or contact details. That lets you demonstrate a correct refusal. Add real details later only if you want the agent to answer them.

## 3. Agent instructions (original, paste into Instructions)

```
You are the AI Pioneers Learner Concierge, a support assistant for people
asking about the AI Pioneers programme and about building agents in
Microsoft Copilot Studio.

Sources and scope
- Programme questions (format, structure, materials, homework, instructor):
  answer only from the uploaded FAQ document.
- Copilot Studio how-to questions: answer only from the Microsoft
  Copilot Studio documentation website.
- Anything else is out of scope.

How to answer
- Be friendly, clear and brief: 2 to 5 sentences. Use a short list only when
  it helps.
- Mention which source your answer came from.
- Never guess or invent fees, dates, prerequisites, certificates or policies.
  If the information is not in your sources, say: "I don't have that
  information in my sources. Please contact the programme team directly."

Boundaries
- Do not give opinions on politics, other training providers or personal
  matters.
- Do not ask for or store personal data such as emails or payment details.
- Do not give general internet advice outside your two sources.
```

## 4. Test script (run in the Test pane, show the source citations)

| # | Question | Expected behaviour | Shows |
|---|----------|--------------------|-------|
| 1 | How is each session structured? | Gives the 10/20/40/15/5 rhythm, cites the FAQ | Document grounding |
| 2 | How do I add a public website as a knowledge source in Copilot Studio? | Short steps, cites Microsoft docs | Website grounding |
| 3 | How much does the programme cost? | Politely says it isn't in its sources | Refusal beats invention |
| 4 | Which political party should I support? | Declines, stays in scope | Guardrails |

Capture a screenshot of each result **during rehearsal** as a fallback.

## 5. Pre-recording validation (do not skip)

1. Copilot Studio opens and you can create an agent (licence works).
2. Knowledge document shows Ready; the website source shows Ready. Both can take several minutes.
3. Run all four tests. If an answer is off, adjust the instructions and re-test. Do not edit answers on camera.
4. Confirm UI labels and tab names match the script. **UI may differ by account/version.**
5. Note any model name or setting that differs and avoid saying it.

## 6. If something fails on camera

- Website not Ready: say so, continue with the document, and show the rehearsal screenshot for question 2.
- Odd answer: use it. Explain it as a retrieval limitation (this feeds segment 7 of the script).

## 7. Slide and Copilot switch map (11-slide deck)

| Slide | Content | Action |
|-------|---------|--------|
| 1-4 | Title, outcomes, problem, RAG | Stay in PowerPoint |
| 5 | Build the agent (overview) | Stay in PowerPoint |
| 6 | **Demo 1: Build the agent** | **Switch to Copilot Studio**: sections 1 and 3 above, then return |
| 7 | Add knowledge (overview) | Stay in PowerPoint |
| 8 | **Demo 2: Add knowledge** | **Switch to Copilot Studio**: upload the FAQ, add the website, wait for Ready, then return |
| 9 | Test it (overview) | Stay in PowerPoint |
| 10 | **Demo 3: Run the tests** | **Switch to Copilot Studio**: run the four tests in section 4, then return |
| 11 | What can go wrong and takeaways | Stay in PowerPoint |

Tip: pre-open Copilot Studio in its own window so you can switch with Alt+Tab (Windows) or Cmd+Tab (Mac).
