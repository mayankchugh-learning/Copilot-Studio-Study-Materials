# Episode Plan: Build a RAG Agent in Copilot Studio
### by Mayank Chugh • AI Engineer • Azure • GenAI • RAG

## 1. Episode identity

| Item | Decision |
|------|----------|
| Working title | Build a RAG Agent in Copilot Studio (No Code) |
| Title candidates | 1. Build a RAG Agent in Microsoft Copilot Studio, No Code. 2. Stop AI Hallucinations: Ground a Copilot Studio Agent in Your Own Docs. 3. From FAQ Document to Working AI Agent in 20 Minutes |
| Series | Copilot Studio for IT Professionals (Episode 1) |
| Audience | IT professionals, architects and engineers new to Copilot Studio |
| Difficulty | Beginner to intermediate |
| Duration | About 21-22 minutes |
| Prerequisites | Copilot Studio access (validate licence needs), a short FAQ document, the public Microsoft Learn Copilot Studio docs URL |

## 2. Learning outcome

By the end, the viewer can:

1. Explain RAG and why a grounded agent beats a bare LLM for company questions.
2. Build an agent in Copilot Studio with a clear name, description and instructions.
3. Add a document and a scoped website as knowledge sources.
4. Test three kinds of question: answered from the document, answered from the website, and correctly declined.
5. Name common ways a RAG agent fails and how to reduce them.

## 3. Demo scenario (original)

A **learner-support concierge agent for your own training programme** (assumed: AI Pioneers) with two knowledge sources of different scope:

1. **Your FAQ document (Word/PDF):** programme questions such as format, requirements, enrolment and contact. Facts such as dates, fees and policies come only from **your real document**. None are invented here.
2. **Public website: Microsoft's Copilot Studio documentation**, `https://learn.microsoft.com/microsoft-copilot-studio/`. It answers "how do I do this in Copilot Studio?" questions, which suits a Copilot Studio video. Microsoft's own docs use a Learn docs URL as a public-website knowledge example. Show "Source: Microsoft Learn" on screen. **Validate on recording day** that the source reaches Ready status and answers well.

Scope rule for the agent instructions: programme questions come from your document, Copilot Studio how-to questions come from the website, and everything else is declined.

## 4. Scope

**Included:** agent anatomy in one slide, RAG mental model, build, two knowledge sources, testing, failure modes.
**Not included (Episode 2 or later):** custom topics and triggers, tools/actions, publishing to channels, fine-tuning deep dive, practice exercises.

## 5. Teaching narrative and timing

| # | Segment | Time | Your angle |
|---|---------|------|-----------|
| 1 | Hook: a bot that confidently answers wrong about *your* programme | 1:30 | Show a bare LLM guessing your cohort details |
| 2 | Problem: LLMs don't know your private or recent data | 2:30 | Hallucination and cutoff, in one example |
| 3 | RAG mental model | 3:00 | Your own IT analogy: a support engineer who checks the runbook before replying to a ticket. Original diagram: question, retrieve, augment, generate |
| 4 | Build the agent | 4:00 | Name, description, instructions written by you (drafted in the script file) |
| 5 | Add knowledge | 3:30 | FAQ document plus the Microsoft Learn Copilot Studio docs as a public website; open web search off, and say why. Mention that public-website sources rely on Bing indexing and have URL depth limits |
| 6 | Test | 4:00 | Three questions: a programme question answered from your FAQ, a Copilot Studio how-to answered from the website, and an out-of-scope or trick question that is declined. Show the source citations each time |
| 7 | What can go wrong | 2:30 | Poor retrieval, stale documents, conflicting sources, instructions that contradict settings |
| 8 | Takeaways and CTA | 1:00 | Episode 2 teaser; standard outro |

Opening: "Hello guys! My name is Mayank Chugh and welcome to my YouTube channel!"
Closing: "I'm Mayank Chugh, thank you for watching! Please Like, Share, and Subscribe. Take care!"

## 6. Safety and responsible use

- Use only public-safe programme information. No learner names, emails or payment data in documents.
- Do not show tenant IDs, account details or admin screens on camera.
- Say clearly that the agent's answers are only as good as the documents behind it.

## 7. What I need from you to continue

1. Confirm the programme is AI Pioneers (or tell me which brand).
2. Fill in the knowledge template (`Copilot_RAG_Agent_Knowledge_Template.md`) with your real answers. Skip any question you can't answer; the agent should decline those.
3. Nothing is needed for the website source. It is the Microsoft Learn docs URL above. If you would rather use a page you own, send the URL and I'll swap it in.

## 8. Next files, in skill order

Notes, PPTX deck (original design, your palette), speaker script, recording runbook, demo runbook (including the agent prompt written from scratch), improvements DOCX, publishing pack, LinkedIn post.
