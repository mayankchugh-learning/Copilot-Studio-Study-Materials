# Recording Runbook, Teaching Notes and Publishing Pack
### by Mayank Chugh

---

# Part A: Recording runbook

## Before you hit record
1. Run the **pre-recording validation** in the Demo Runbook (licence, both sources Ready, all four tests).
2. Screen: 1920x1080, browser zoom 110-125%, notifications off, clean browser profile.
3. Hide tenant names, user emails and admin menus. Blur or crop anything personal.
4. Keep rehearsal screenshots of all four test answers as fallback.
5. Have the script, the instructions text and the FAQ document open on a second screen.

## Take order
1. Record the **demo segments first** (build, knowledge, test), because they carry the most risk.
2. Record the talking-head or slide segments (hook, problem, RAG, failure modes, takeaways).
3. Record intro and outro last.

## Common mistakes to avoid
- Naming a model or quoting a limit you haven't validated.
- Saying "the R stands for retriever". It is **Retrieval**.
- Editing the agent's answers to look better. Show real behaviour.
- Letting open web search stay on while the instructions say "only my sources".

---

# Part B: Teaching notes

## Core ideas
- **Agent** = model + instructions + knowledge (+ tools, later).
- **RAG** = retrieve relevant content, add it to the prompt, generate the answer.
- **Grounding** = answers anchored in named sources, which you can cite.
- **Guardrails** = scope, tone and refusal rules written in the instructions and proven by tests.

## Your analogy
A support engineer checks the runbook before answering the ticket. Use it in the video and in the post.

## RAG vs fine-tuning (one-liner for the video)
Fine-tuning changes the model; RAG changes what the model sees at question time. RAG is usually cheaper to update.

## What makes this episode original
- Your own scenario, document, prompt, diagram and script.
- A refusal-first testing approach with a deliberately incomplete FAQ.
- A "what can go wrong" segment based on real configuration pitfalls.

## Further reading (official)
- Microsoft Learn: Add a public website as a knowledge source
  `https://learn.microsoft.com/microsoft-copilot-studio/knowledge-add-public-website`

## Optional credit
If a course helped you learn the basics, a one-line thank-you in the description is good practice. It is optional because this video is built from your own material.

---

# Part C: Publishing pack

## Title (pick one)
1. **Build a RAG Agent in Microsoft Copilot Studio (No Code)**
2. Stop AI Hallucinations: Ground a Copilot Studio Agent in Your Own Docs
3. From FAQ Document to Working AI Agent in 20 Minutes

## Thumbnail text
"RAG AGENT, NO CODE" with a small "Copilot Studio" label. Use your channel colours.

## Description

Ask a general chatbot about your own documents and it will often guess. In this video I build a no-code RAG agent in Microsoft Copilot Studio that answers from a document and a trusted website, and politely refuses everything else.

What you'll learn:
- What RAG is, in plain IT terms
- How to build an agent: name, description, instructions
- How to add a document and a public website as knowledge
- How to test grounded answers and refusals
- Four ways a RAG agent can fail

Chapters:
0:00 Why chatbots guess
1:30 The problem with LLMs
4:00 RAG explained
7:00 Build the agent
11:00 Add knowledge
14:30 Test it
18:30 What can go wrong
21:00 Takeaways

Official docs: https://learn.microsoft.com/microsoft-copilot-studio/knowledge-add-public-website

Note: the FAQ used in this demo is sample content. Always validate settings in your own tenant; screens can differ by account and version.

[Add your own links here: channel, programme page, socials]

Hello guys! My name is Mayank Chugh. Please Like, Share, and Subscribe. Take care!

## Tags
copilot studio, RAG, retrieval augmented generation, AI agent, no code AI, Microsoft Copilot Studio tutorial, GenAI, grounded AI, AI hallucination, knowledge source, Azure, AI for IT professionals

## Pinned comment
Which would you try first: a document-grounded agent for your team's policies or for customer FAQs? Tell me below, and I'll cover topics and triggers next.

## LinkedIn post

Ask a general chatbot about your own documents and it will often answer with confidence, and be wrong.

I just published a no-code walkthrough of fixing that in Microsoft Copilot Studio:

- Explain RAG the way IT teams already think: a support engineer opens the runbook before replying to the ticket
- Build an agent with clear scope and refusal rules
- Add a document plus a trusted public website
- Test not only good answers, but refusals

The biggest lesson: the quality of a RAG agent comes from clear instructions and clean sources, not from a bigger model.

Watch it here: [add your video link]

What would you ground an agent in first? Policies, product docs, or programme FAQs?

#GenAI #RAG #CopilotStudio #AIAgents #Azure
