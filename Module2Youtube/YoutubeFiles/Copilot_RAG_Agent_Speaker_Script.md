# Speaker Script: Build a RAG Agent in Copilot Studio (No Code)
### by Mayank Chugh • about 22 minutes

Written for your voice. Edit freely. **[SCREEN]** = what to show.

---

## 0:00 Hook and intro (1:30)

**[SCREEN: a general chatbot answering a question about your programme, wrongly]**

Hello guys! My name is Mayank Chugh and welcome to my YouTube channel!

Ask a general AI chatbot about *your* training programme, or your company's policies, and it will answer in a very confident tone, and it will often be wrong. It isn't lying. It simply never saw your documents.

Today we fix that. We'll build an AI agent in Microsoft Copilot Studio, with no code, that answers from your own document and from one trusted website, and politely refuses everything else. By the end you'll know what RAG really is, how to build the agent, and where it can fail.

---

## 1:30 The problem (2:30)

**[SCREEN: slide, "What an LLM knows"]**

A large language model learned from huge amounts of public text, up to a cutoff date. Two gaps follow from that.

First, it doesn't know your private information: internal policies, programme details, product documents. Second, it doesn't know what changed after its cutoff.

When a model has no answer, it can still produce a fluent one. We call that a hallucination. For a support assistant, a fluent wrong answer about fees or dates is worse than no answer.

---

## 4:00 RAG in plain terms (3:00)

**[SCREEN: your own diagram: Question, Retrieve, Augment, Generate]**

RAG stands for Retrieval-Augmented Generation. Let me explain it the way I'd explain it to an IT team.

Imagine a support engineer who gets a ticket. A weak engineer answers from memory. A good engineer first opens the runbook, finds the relevant page, and then writes the reply using that page.

That is RAG, in four steps. One: the user asks a question. Two: the system **retrieves** the most relevant pieces from your knowledge. Three: it **augments** the prompt by adding those pieces. Four: the model **generates** the answer from them.

The model itself isn't retrained. We change what it sees at question time. That makes RAG cheaper and easier to keep current than fine-tuning: update the document and the answers follow.

Conceptually, the platform prepares your content so it can be searched. I won't go into the plumbing today.

---

## 7:00 Build the agent (4:00)

**[SCREEN: Copilot Studio, create agent, Configure]**

Let's build. In Copilot Studio I create a new agent and open the configuration view. *(Validate labels before recording.)*

I'll name it **AI Pioneers Learner Concierge**, and add a short description saying who it helps and what it does.

Now the instructions. This is where most of your quality comes from. Mine has three parts. **Scope:** programme questions come from my document, Copilot Studio how-to questions come from Microsoft's docs, and everything else is out of scope. **Style:** short, friendly, and always say which source you used. **Boundaries:** never invent fees, dates or prerequisites, and say "I don't have that information" when it isn't in the sources.

**[SCREEN: paste instructions from the Demo Runbook]**

Notice I'm telling the model what to do when it *doesn't* know. That single rule prevents many embarrassing answers.

One more setting: I'm keeping general web search **off**. If I leave it on, my agent can wander outside my sources, which contradicts the scope I just wrote.

---

## 11:00 Add knowledge (3:30)

**[SCREEN: Knowledge, Add knowledge]**

An agent needs to exist before you can attach files, so we create it first.

Source one: a Word document. This is a short sample FAQ for my AI Pioneers programme. It's sample content for this demo. It covers the format, the 90-minute session structure, the materials and homework. I upload it, give it a clear name and description, and add it.

**[SCREEN: Public websites]**

Source two: a public website. I'm adding Microsoft's Copilot Studio documentation, so the agent can answer how-to questions with official sources.

Two things to know. Public-website sources rely on pages the search index has already crawled, and the URL can only go two levels deep. Sites behind a login won't work.

Let both sources reach **Ready** before testing.

---

## 14:30 Test it (4:00)

**[SCREEN: Test pane]**

Test one, the document. I ask: *How is each session structured?* The agent gives the warm-up, concepts, live coding, lab and wrap-up, and it cites my FAQ. That's grounding.

Test two, the website. *How do I add a public website as a knowledge source in Copilot Studio?* It answers with steps and points to Microsoft's documentation.

Test three, the one that matters. *How much does the programme cost?* My document doesn't say, so the agent tells me it doesn't have that information. A weaker setup would invent a price. This refusal is the whole point of the instructions.

Test four, a trick: a political question. It declines and stays in scope.

I always include refusal tests, because real users will try them.

---

## 18:30 What can go wrong (2:30)

**[SCREEN: slide, four failure modes]**

RAG isn't magic. Four common failures.

**Poor retrieval.** The answer exists, but the system pulled the wrong passage. Clear, well-structured documents help.

**Stale documents.** The agent is only as current as its sources. Someone must own updates.

**Conflicting sources.** If your document and a website disagree, the agent may pick either. Decide which source wins.

**Instructions that contradict settings.** Telling the agent to use only your documents while web search is on is a classic mistake.

---

## 21:00 Takeaways (1:00)

**[SCREEN: slide, three takeaways]**

Three things to remember. RAG means retrieve, augment, generate. Grounding comes from good sources and clear instructions. And always test refusals, not just happy paths.

In the next video I'll show you topics and triggers to control the conversation flow.

I'm Mayank Chugh, thank you for watching! Please Like, Share, and Subscribe. Take care!
