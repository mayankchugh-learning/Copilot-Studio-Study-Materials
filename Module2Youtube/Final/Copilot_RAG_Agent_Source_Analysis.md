# Build a RAG Agent in Copilot Studio: Source Analysis & Coverage
### by Mayank Chugh

## 1. How the sources are used

The supplied Module 2 material is a third-party course (credited in the Word file to Dr. Ryan Ahmed, with "All rights reserved" notices on every slide). It is used here as a **topic map for your own learning only**. Nothing in this package reuses its wording, prompts, slide layouts, scenario, practice exercise, custom-topic example or script flow. Everything you record must come from your own build, your own documents and your own words.

If you mention the course on camera, a one-line credit ("I learned the basics of Copilot Studio from...") is good practice.

## 2. Source inventory

| File | Type | Likely purpose | Key content (concept level) | Reliability | Used in |
|------|------|----------------|-----------------------------|-------------|---------|
| Videos 4-16 transcripts (.txt) | Transcript | Third-party lectures | Agent anatomy, RAG idea, Copilot Studio build flow, testing, topics | Spoken, informal, a few errors | Concept check only |
| Module_2.pptx | Slides | Third-party slides | Agent/RAG diagrams, RAG vs fine-tuning table | Copyrighted, not reusable | Not reused |
| Module_2.docx | Prompt library | Third-party prompts and links | Agent prompt, knowledge list, test questions | Copyrighted, not reusable | Not reused |
| Eleven_Madison_Park.png | Image | Third-party logo | Restaurant logo | Trademark of another business | Not used |
| mayank-youtube-content-SKILL-v4.md | Skill | Your production workflow | Package structure, branding, QA | Authoritative for format | This package |

## 3. What is general knowledge (safe to teach in your own words)

- An agent = an LLM plus instructions, knowledge and (optionally) tools.
- RAG = retrieve relevant content, add it to the prompt, then generate. It is **R**etrieval-**A**ugmented **G**eneration.
- Grounding reduces hallucination and stale answers without retraining the model.
- Guardrails belong in the agent instructions and should be tested with out-of-scope and trick questions.

## 4. Conflicts, errors and validation items

| Topic | What the source says | Resolution | Recording action |
|-------|----------------------|------------|------------------|
| Instructions vs web search | Instructions say "answer only from the internal knowledge base", yet open web search and a website were also enabled | Your video keeps open web search **off** and uses one scoped website source | Show the setting and explain why |
| Model choices | Lists GPT-4.1 / GPT-5 variants | Model lists change often | **Validate in your tenant on recording day**; avoid naming models in slides |
| Upload size limit | "About 512 MB" mentioned | Unverified | Do not state a number |
| What RAG stands for | One lecture says "the R stands for retriever" | Wrong: R is Retrieval | Say it correctly on camera |
| Indexing detail | Says files are chunked and vectorized behind the scenes | Plausible, but not verified for Copilot Studio specifically | Say "conceptually, the platform indexes your content" |
| UI labels and order | Describe / Configure tabs, knowledge only after Create | UI changes by account and version | **UI may differ by account/version. Validate immediately before recording.** |
| Licence requirement | Says you need an appropriate licence | Plans and licensing change | Check current requirements before telling viewers |
| Public website rules | Course shows adding a site with no restrictions | Microsoft's docs say public-website sources rely on Bing-indexed content, allow up to two URL levels of depth, and don't support sites needing authentication | Mention these limits on camera; confirm the Learn URL reaches Ready status |

## 5. Gaps (what only you can supply)

1. **Your real FAQ content** for the programme or brand the agent will serve (see the knowledge template file).
2. **Website source:** none needed from you. The plan uses Microsoft's public Copilot Studio documentation (`https://learn.microsoft.com/microsoft-copilot-studio/`). Check on recording day that it reaches Ready status.
3. Your Copilot Studio access, to run the demo and capture real results.

## 6. Scope recommendation

One focused episode (about 20-25 minutes). Custom topics/triggers, tools and publishing are better as Episode 2.
