---
name: mayank-youtube-content
description: >
  Generates 7 coordinated content files from a transcript or topic text: (1) PPTX with
  speaker-note scripts, (2) Notes MD reference doc, (3) DOCX improvements guide with code,
  (4) Medium blog post, (5) LinkedIn post, (6) Jupyter notebook with transcript gold blocks
  and slide sync, (7) cell-by-cell narration script WITH platform switch markers embedded
  at exact moments. Trigger on: prepare files from transcript, make slides for my YouTube
  video, generate content files, create PPT and MD and DOCX, add Medium blog, add LinkedIn
  post, update notebook with transcript, cell by cell transcript, or any request to produce
  educational content from lecture notes or video transcripts. Platform switches (Weaviate
  console, Cohere dashboard, HuggingFace, any browser portal) are embedded in the Cell
  Transcript at exact moments with step-by-step screen navigation. Always produce all seven
  files even if only some are mentioned.
---

# Mayank YouTube Content Skill — v3

Generates **seven coordinated content files** from a single transcript or topic text.

**New in v3:**
- Platform switch markers embedded in Cell Transcript for browser-based demos
- Executed notebook diff: extracts real scores, actual warnings, real cell outputs
- Source document support: embeds paper citation, section-to-query mapping, actual results
- Cohere dashboard reality: no Rerank tab in Playground — script uses API Keys + Billing only

| # | File | Format | Purpose |
|---|------|--------|---------|
| 1 | PPTX | `.pptx` | YouTube slide deck with full speaker-note scripts |
| 2 | Notes | `.md` | Clean reference document (no code) |
| 3 | Improvements | `.docx` | Technical depth + content improvement guide (code allowed) |
| 4 | Medium Blog | `.md` | Long-form article ready to paste into Medium |
| 5 | LinkedIn Post | `.md` | Short-form post with hooks, emojis, hashtags |
| 6 | Notebook | `.ipynb` | Jupyter notebook with transcript gold blocks + slide sync |
| 7 | Cell Transcript | `.md` | Cell-by-cell narration with platform switch markers |

---

## Required Inputs

| Input | Required | Notes |
|-------|----------|-------|
| Transcript or topic text | Yes | Raw transcript, lecture notes, or topic outline |
| Working notebook (.ipynb) | Optional | Sync notebook code to PPT — diff first |
| Executed notebook (.ipynb) | Optional | Extract real scores, warnings, actual outputs |
| Instructor diagram (image) | Optional | Digitise as separate reference PPTX slide |
| Platform screenshots (image) | Optional | Identify portals shown → embed switch points |
| Topic/series name | Inferred | Extract from content if not stated |
| Episode number | Inferred | Default to "Episode 1" if not stated |
| Source document / PDF | Optional | Use actual queries, sections, paper details throughout |

---

## Step 0 — Read the Dependency Skills

Before writing any code, read these skill files:

```bash
view /mnt/skills/public/pptx/SKILL.md
view /mnt/skills/public/pptx/pptxgenjs.md
view /mnt/skills/public/docx/SKILL.md
```

---

## Step 1 — Analyse the Transcript

Extract before generating any output:

- **Core topic** and series title
- **Key concepts** (3–7 main ideas)
- **Analogies or examples** — preserve and feature them prominently
- **Real-world use cases** mentioned
- **Statistics or facts** cited — only use what is in the transcript, never invent
- **Before/after comparisons**
- **Natural teaching flow** — respect the instructor's order
- **Actual code packages used** — note exact import paths, model names, API vs local
- **Platform switches** — identify every moment the instructor switches from notebook to a browser portal and back
- **Source document** — if a specific PDF or paper is indexed, note the title, authors, arXiv ID, and which queries come from which sections

---

## Step 2 — Diff Analysis

### From working notebook — check:

| Item | What to check |
|------|--------------|
| LLM model name | Must match between notebook and PPT |
| Embedding method | API-based vs local |
| Import paths | `langchain_classic`, `langchain_community`, `langchain_cohere` etc. |
| Package names | Note any non-standard packages |
| Corpus size | Number of documents or pages indexed |
| Retriever class | `WeaviateHybridSearchRetriever` (broken v4) vs `WeaviateV4HybridRetriever` (custom) |
| Batching method | `retriever.add_documents()` (broken) vs `collection.batch.dynamic()` |
| Client version | `weaviate.Client()` v3 (removed Dec 2024) vs `connect_to_weaviate_cloud()` v4 |
| Credential method | Plaintext strings vs `userdata.get()` Colab Secrets |
| Retriever call | `.invoke()` vs deprecated `.get_relevant_documents()` |

### From executed notebook — additionally extract:

| Item | What to extract |
|------|----------------|
| Cohere rerank scores | Extract Rank1/Rank2/Rank3 exactly — NEVER use placeholder scores |
| Real cell outputs | Document actual output text for key cells |
| Actual warnings | Note all warnings: sunset, deprecated, pip conflict, ignored flags |
| Collection output | "Deleted existing RAG collection" vs "starting fresh" |
| Retrieved document count | Actual number from `.invoke()` test |
| LLM answer style | Verbose/MCQ/concise — affects what to say on camera |
| PDF page count | Actual page count from PyPDFLoader |

Apply all detected differences to ALL seven files before delivering.

---

## Step 3 — Identify All Platform Switches (REQUIRED for browser demos)

Map every moment the recording switches between environments. This feeds directly into Step 11 (Cell Transcript).

### Platform Registry

| Platform | URL | What to show |
|----------|-----|-------------|
| Colab notebook | colab.research.google.com | Default environment — always return here after every switch |
| Weaviate Console | console.weaviate.cloud | Cluster setup, credentials, schema verification, object browse, GraphQL query |
| Cohere Dashboard | dashboard.cohere.com | API key copy — NOT Playground (no Rerank tab exists) |
| Cohere Billing | dashboard.cohere.com → Billing & Usage | Post-run: confirm rerank calls, show $0.00 cost |
| HuggingFace | huggingface.co → Settings → Access Tokens | HF token for text2vec-huggingface module |
| Any other portal | Document URL and purpose | As applicable |

### Cohere Platform Rules (CRITICAL — applies to all episodes using Cohere Rerank)

The Cohere Playground only has **Chat** and **Embed** tabs. There is **no Rerank tab**.
Reranking is a code-only API. When scripting Cohere platform segments:

```
✅ SHOW:  Dashboard → API Keys → copy trial key
✅ SHOW:  Dashboard → Billing & Usage → USAGE tab (post-run confirmation)
❌ NEVER: Playground → Rerank (does not exist)
❌ NEVER: Say "let me show you the reranker in the playground"
```

What to say about Cohere Playground on camera:
> "If you go to the Cohere Playground, you'll only see Chat and Embed tabs.
> There is no Rerank tab — reranking is a code-only API.
> The only things we need from this dashboard are the API key
> and the Billing & Usage page to confirm our calls."

### Billing & Usage Script (post-reranking)

After running reranking cells, switch to Cohere Billing & Usage and say:

> "Look at this — proof the API was called.
> [N] Reranks on [date] — that's our notebook making live API calls to Cohere rerank-v3.5.
> And the cost: zero. The free trial covers this entire demo."

Then use the filter: FILTER BY ENDPOINT → Rerank to show only rerank calls.

### Standard Switch Sequence for Weaviate + Cohere Episodes

```
COLAB  → cells 1–3: install, imports
  ↓
[SWITCH TO WEAVIATE CONSOLE]
  Show: cluster URL, API Keys tab, text2vec-huggingface module enabled
  Get:  WEAVIATE_URL, WEAVIATE_API_KEY
  ↓
COLAB  → cell 4: Colab Secrets (userdata.get())
  ↓
[SWITCH TO HUGGINGFACE]  (only if HF token needed for embeddings)
  Show: Settings → Access Tokens → create Read token
  Get:  HF_TOKEN_READ
  ↓
COLAB  → cell 5: load credentials
  ↓
[SWITCH TO COHERE CONSOLE → API Keys]
  Show: trial key, note NO Rerank tab in Playground
  Get:  COHERE_API_KEY
  ↓
COLAB  → cell 6: Weaviate v4 client, connection test
  ↓
COLAB  → cell 7: delete existing collection
  ↓
[SWITCH TO WEAVIATE CONSOLE → Collections]
  Show: empty collections list (just deleted)
  ↓
COLAB  → cells 8–9: create collection, schema
  ↓
[SWITCH TO WEAVIATE CONSOLE → Collections → RAG]
  Show: collection created, schema properties, object count = 0
  ↓
COLAB  → cell 10+: custom retriever, LLM, load PDF
  ↓
COLAB  → batch index cell (reconnect with HF header first)
  ↓
[SWITCH TO WEAVIATE CONSOLE → Collections → RAG → Browse]
  Show: object count = N (all pages indexed)
  Optional: run GraphQL test query to confirm hybrid search
  ↓
COLAB  → baseline chain, reranking cells
  ↓
[SWITCH TO COHERE CONSOLE → Billing & Usage → USAGE tab]
  Show: Rerank TRIAL | Default | N Reranks | $0.00
  Filter by Endpoint: Rerank
  Explain: Jun 7 = 4 docs sent, Jun 8 = top_n=3 returned
  ↓
COLAB  → reranked chain, second query, closing
```

---

## Step 4 — Plan the Slides

Design 8–10 slides:

| Slide | Purpose |
|-------|---------|
| 1 | Title slide — topic, "by Mayank Chugh" branding, source paper if applicable |
| 2 | What is [Topic]? — definition + simple analogy |
| 3 | The Problem / Why It Matters — use source paper examples if available |
| 4 | Architecture or Core Concept Diagram (shapes only, no images) |
| 5 | Concept Breakdown |
| 6 | Analogy Deep-Dive (librarian, chef, expert reviewer etc.) |
| 7 | Real-World Use Case (before/after — use ACTUAL scores from executed notebook) |
| 8 | Real-World Impact / Stats — cite paper results if source document provided |
| 9 | Key Takeaways + What's Next |

---

## Step 5 — Generate the PPTX

Use `pptxgenjs` at `/home/claude/.npm-global/lib/node_modules/pptxgenjs`.

### Color Palette

```
darkBg:   "0A1628"
midBg:    "0D2137"
teal:     "00B4D8"
orange:   "FF6B35"
green:    "4CAF82"
purple:   "9B72CF"
lightTxt: "E8F4FD"
subTxt:   "90B8D4"
cardBg:   "102235"
white:    "FFFFFF"
```

### Layout Rules

- NEVER use `#` prefix on hex colors
- NEVER reuse shadow/style objects — use factory functions
- Architecture diagram Phase labels must match actual notebook model/package names
- Slide 7 Before/After table: use ACTUAL Cohere scores from executed notebook — never placeholder 0.99
- Slide 8 impact bullets: use actual paper results if source document provided
- QA: render every slide as JPEG and inspect before delivering

### Speaker Notes Format

```
[SLIDE N – Slide Title]

[Opening]

[Main explanation — use instructor's exact phrasing]

[Source citation if applicable: "Source: Lewis et al., NeurIPS 2020, Table 6"]

[Transition]

---
[👍 Like, Share and Subscribe! — slides 1, analogy, stats, final only]
```

Slide 1 opens: "Hello guys! My name is Mayank Chugh and welcome to my YouTube channel!"
Final slide closes: "I'm Mayank Chugh, thank you so much for watching! Please Like, Share, and Subscribe."

---

## Step 6 — Generate the Notes Markdown

**Rules:** No code blocks. If source document used, include paper citation at top.
If executed notebook provided, include execution notes table.

**Structure:**
```
# [Topic]
### by Mayank Chugh | Episode N | Updated [Month Year]

## 📄 Source Document (if applicable)
Full citation: Title, Authors, Venue, arXiv, file name

## ⚠️ Execution Notes (if executed notebook provided)
| Issue | What Happened | Fix Applied |

## Table of Contents

## 1. What is [Topic]?
## 2. The Problem [Topic] Solves
## 3. Architecture Overview (ASCII diagram)
## 4. Key Components
## 5. Demo Queries (if source document)
   Primary query → paper section
   Secondary query → paper section
   Additional queries to try
## 6. Live Demo Results (if executed notebook)
   Retrieved count, Cohere scores, score interpretation
## 7. Paper Results (if source document)
   Cite tables and numbers
## 8. Real-World Use Case (comparison table)
## 9. Key Takeaways
## 10. What's Coming Next

*Made with ❤️ by Mayank Chugh*
```

---

## Step 7 — Generate the DOCX

Use `docx` at `/home/claude/.npm-global/lib/node_modules/docx`.

**Rules:** Code blocks allowed. No transcript. Improvements and technical depth only.
Include breaking changes table if v3→v4 or package migrations are involved.

**Validate after creating:**
```bash
python /mnt/skills/public/docx/scripts/office/validate.py [file].docx
```

---

## Step 8 — Generate the Medium Blog Post

- Use ACTUAL scores from executed notebook — not placeholder numbers
- If source document: cite actual paper results with table references
- Include "What Broke" section if breaking changes were found during execution

---

## Step 9 — Generate the LinkedIn Post

- If actual scores available: lead hook with the number (e.g. "0.6641, not 0.99")
- If executed notebook: mention the honest finding (e.g. real score vs tutorial claim)

---

## Step 10 — Generate the Notebook (.ipynb)

### Header cell must include:
- If models updated: June [Year] update table (Old → New for each component)
- Source document name and arXiv if applicable
- Actual live scores: `> 📊 Actual scores: Rank1: 0.6641 · Rank2: 0.3853 · Rank3: 0.0860`
- Runtime note: T4 GPU required

### Gold block format — unchanged from v2

### Install cells — adapt to actual packages:

For Weaviate + Cohere + Qwen3 episodes:
```python
# Cell 1
!pip install -q weaviate-client langchain langchain_community langchain_classic \
             pypdf bitsandbytes accelerate cohere langchain-cohere \
             "transformers>=4.51.0"

# Cell 2
!pip install -q --upgrade langchain langchain_community
```

### Code Quality Rules

| Rule | Correct | Wrong |
|------|---------|-------|
| Weaviate client | `weaviate.connect_to_weaviate_cloud()` | `weaviate.Client()` — removed Dec 2024 |
| Weaviate batching | `collection.batch.dynamic()` | `retriever.add_documents()` — v3 only |
| Retriever class | `WeaviateV4HybridRetriever` (custom) | `WeaviateHybridSearchRetriever` — broken v4 |
| CohereRerank import | `from langchain_cohere import CohereRerank` | `from langchain.retrievers.document_compressors` |
| ContextualCompression | `from langchain_classic.retrievers import ContextualCompressionRetriever` | `from langchain.retrievers` |
| RetrievalQA | `from langchain_classic.chains import RetrievalQA` | `from langchain.chains` |
| EnsembleRetriever | `from langchain_classic.retrievers import EnsembleRetriever` | `from langchain.retrievers` |
| Text splitter | `from langchain_text_splitters import RecursiveCharacterTextSplitter` | `from langchain.text_splitter` |
| Retriever call | `.invoke(query)` | `.get_relevant_documents(query)` — deprecated |
| LLM pipeline flags | `do_sample=False` only for Qwen3 | `temperature=`, `top_k=`, `top_p=` — ignored, warns |
| Qwen3 tokenizer | `AutoTokenizer.from_pretrained(model_name)` | `bos_token_id = 1` override — not needed |
| Credentials | `userdata.get('KEY_NAME')` | Plaintext strings in notebook |
| Schema properties | `content` only | Adding `source`, `page` without matching batch code |

### Clean Notebook Rules

- No inline comments in code cells during recording
- Tell audience: "All comments are in the GitHub committed version"
- Two notebook versions: WithTranscript (gold blocks) and Clean (no gold, no slide refs)

---

## Step 11 — Generate the Cell-by-Cell Transcript (.md)

Output as `[Topic]_CellByCell_Transcript.md`.

### Header Block (required at top of file)

```markdown
> 📄 Source Document (if applicable):
> Title, Authors, Venue, arXiv, file name

> ✅ Actual Cohere scores (from live execution):
> Rank 1: X.XXXX · Rank 2: X.XXXX · Rank 3: X.XXXX

> ⚠️ Key execution facts:
> - List all breaking changes confirmed in executed notebook
> - Cohere Playground: NO Rerank tab — use API Keys + Billing & Usage
> - Cell N output: exact output text
```

### Platform Switch Key Table (required in every transcript with browser demos)

```markdown
## 🖥️ PLATFORM SWITCH KEY

| Marker | Action |
|--------|--------|
| `[SWITCH TO WEAVIATE CONSOLE]` | Open browser tab → console.weaviate.cloud |
| `[SWITCH TO COHERE CONSOLE]` | Open browser tab → dashboard.cohere.com |
| `[SWITCH TO HUGGINGFACE]` | Open browser tab → huggingface.co |
| `[SWITCH TO COLAB]` | Return to Colab notebook tab |
| `[SHOW SLIDE N]` | Switch to PPTX slide N |
| `[COME BACK TO NOTEBOOK]` | Return to Colab |
| `[TYPE/PASTE]` | Type or paste code into cell |
| `[RUN]` | Press Shift+Enter |
```

### Platform Switch Block Format

Each switch must follow this exact structure:

```markdown
## ⏸️ PLATFORM SWITCH — [Platform Name + Purpose]

`[SWITCH TO WEAVIATE CONSOLE]`   (or COHERE CONSOLE, HUGGINGFACE, etc.)

**Open your browser → [URL]**

**Step 1 — [Action]:**
- Sub-step a
- Sub-step b
- What to get / copy

**Step 2 — [Action]:**
- Sub-steps

**What to say on camera:**
> "[Exact narration text while on this platform]"

> 📌 [Tip or important note for the viewer]

`[SWITCH TO COLAB]`
```

### Weaviate Console Switch Templates

**Switch: Get credentials**
```markdown
## ⏸️ PLATFORM SWITCH — Weaviate Cloud Setup

`[SWITCH TO WEAVIATE CONSOLE]`

**Open your browser → console.weaviate.cloud**

**Step 1 — Create a free sandbox cluster:**
- Click "Create cluster"
- Name it [suggested name]
- Select Free Sandbox — 14 days, no credit card
- Click Create — takes about 30 seconds

**Step 2 — Get your WEAVIATE_URL:**
- Click the cluster name → copy the Cluster URL (https://xxx.weaviate.network)
- This goes into Colab Secrets as `WEAVIATE_URL`

**Step 3 — Get your WEAVIATE_API_KEY:**
- Same page → API Keys → copy Admin key
- This goes into Colab Secrets as `WEAVIATE_API_KEY`

**Important:** Point out the text2vec-huggingface module is enabled — this is why
we pass the HuggingFace token as a header. Weaviate calls HF server-side.

`[SWITCH TO COLAB]`
```

**Switch: Verify empty collection**
```markdown
## ⏸️ PLATFORM SWITCH — Verify Empty Collection

`[SWITCH TO WEAVIATE CONSOLE]`

**console.weaviate.cloud → Collections tab**

Should show no RAG collection — we just deleted it. After the next cell,
come back and you'll see it reappear with the correct schema.

`[SWITCH TO COLAB]`
```

**Switch: Confirm collection created**
```markdown
## ⏸️ PLATFORM SWITCH — Confirm Collection Created

`[SWITCH TO WEAVIATE CONSOLE]`

**console.weaviate.cloud → Collections → RAG**

Show:
- Vectorizer: text2vec-huggingface
- Model: [actual model name]
- Properties: content (text)
- Object count: 0 — not indexed yet

`[SWITCH TO COLAB]`
```

**Switch: Confirm documents indexed**
```markdown
## ⏸️ PLATFORM SWITCH — Confirm Paper Indexed

`[SWITCH TO WEAVIATE CONSOLE]`

**console.weaviate.cloud → Collections → RAG → Browse**

Object count is now [N] — all [source] pages indexed.
Click Browse to see the objects. Each has a `content` property.

Optional GraphQL test query:
```graphql
{
  Get {
    RAG(hybrid: {query: "[test query]", alpha: 0.5}, limit: 2) {
      content
    }
  }
}
```

`[SWITCH TO COLAB]`
```

### Cohere Console Switch Templates

**Switch: Get API key**
```markdown
## ⏸️ PLATFORM SWITCH — Cohere API Key

`[SWITCH TO COHERE CONSOLE]`

**Open your browser → dashboard.cohere.com**

**Step 1 — Log in or create a free account** — no credit card needed.

**Step 2 — Left sidebar → API Keys:**
- Copy your trial key

**Step 3 — Back in Colab Secrets:**
- `COHERE_API_KEY` → paste → enable notebook access

**Important for viewers:** If you go to the Playground you'll only see Chat and
Embed tabs. There is NO Rerank tab — reranking is a code-only API. All we need
from this dashboard is the API key and the Billing & Usage page.

`[SWITCH TO COLAB]`
```

**Switch: Verify rerank calls (post-reranking)**
```markdown
## ⏸️ PLATFORM SWITCH — Verify Rerank Calls in Cohere Console

`[SWITCH TO COHERE CONSOLE]`

**dashboard.cohere.com → Billing & Usage → USAGE tab**

Point to the table:
- Rerank TRIAL | Default | [N] Reranks | [date] | $0.00

What to say:
> "This is live proof the API was called. [N] reranks on [date].
> Jun 7 = 4 documents sent for scoring. Jun 8 = top_n=3 returned.
> The scores [X.XXXX / X.XXXX / X.XXXX] came from these calls.
> Cost: zero. The free trial covers this entire demo."

Filter → FILTER BY ENDPOINT → select Rerank to show only rerank calls.

`[SWITCH TO COLAB]`
```

### Cell Block Format

```markdown
## 📓 CELL N — [Cell Description]

`[TYPE/PASTE]`

[Narration — conversational, what you say while typing or the cell is visible]

`[RUN]`

[Output narration — what you say about the output]
```

### Wait Time Commentary (for long-running cells)

When a cell takes >60 seconds (model loading, large indexing), include:

```markdown
*While this loads/runs, say on camera:*

> "[Interesting fact about the topic, paper result, or context while waiting]"
```

Examples for Weaviate + Cohere episodes:
- While Qwen3-8B loads: cite paper result (e.g. "RAG-Sequence achieves 44.5 EM vs T5-11B's 34.5")
- While indexing: "We're indexing [N] pages. The original paper indexed 21M Wikipedia chunks."

### Slide Sync Points

Include `[SHOW SLIDE N]` + `[COME BACK TO NOTEBOOK]` at these moments:
- Before concept definition section → Slide 2
- Before problem/roadmap section → Slide 3
- Before architecture ASCII diagram → Slide 4
- Before keyword search theory → Slide 5
- Before analogy section → Slide 6
- Before alpha weighting formula → Slide 7
- Before naive vs hybrid comparison → Slide 8
- At key takeaways → Slide 9

### Opening Block (before Cell 1)

```markdown
## 🎬 OPENING (before any cell)

`[SHOW SLIDE 1 — Title]`

"Hello guys! My name is Mayank Chugh and welcome to my YouTube channel!

[Episode intro — 2–3 sentences. Include source document name and arXiv if applicable.
Mention the meta angle if interesting, e.g. 'building a RAG system to query the paper that invented RAG.']

[Note on actual scores if they differ from tutorial claims:
'The actual Cohere scores from our live run are X.XXXX, X.XXXX, and X.XXXX — not 0.99.
I'll explain what those scores mean.']

T4 GPU runtime. Let's go."

`[COME BACK TO NOTEBOOK]`
```

### Closing Block (after last cell)

```markdown
## 🎬 CLOSING (after all cells)

`[SHOW SLIDE 9 — Key Takeaways]`

[Numbered key lessons — match actual executed results:]
"One — [breaking change #1 confirmed in execution]
Two — [breaking change #2]
Three — [actual scores and what they mean]
Four — [key import fix]
Five — [LLM flag caveat]

[Source paper summary if applicable:
'Source: Lewis et al., NeurIPS 2020. arXiv:XXXX.XXXXX. Key results: ...']

Complete notebook on GitHub — link in description.
In Episode Three — [next episode topic].

I'm Mayank Chugh — thank you for watching! Please Like, Share, Subscribe. Take care!"
```

### Quick Reference Card (at end of every transcript)

Include a pinned cheat sheet at the bottom of every Cell Transcript:

```markdown
## 📋 QUICK REFERENCE — Pin This While Recording

```
PAPER:   [Full citation if applicable]
         File: [filename]

QUERIES: Q1 — "[query]" (Section X.X)
         Q2 — "[query]" (Section X.X)

SCORES:  Rank 1: X.XXXX | Rank 2: X.XXXX | Rank 3: X.XXXX ([date] live run)
         Billing: [date] = N Reranks $0.00 | [date] = N Reranks $0.00

PAPER FACTS FOR WAIT TIMES:
  - [Fact 1 to say while model loads]
  - [Fact 2 to say while indexing]

WARNINGS — tell viewers EXPECTED:
  [Warning 1] → [explanation]
  [Warning 2] → [explanation]

PLATFORM NOTES:
  [Platform] = [what to show / what NOT to show]
  Cohere Playground = Chat + Embed ONLY. NO Rerank tab.

KEY CELL OUTPUTS:
  Cell N: [actual output]
  Cell N: [actual output]
  Cell N: [Cohere scores]
```
```

---

## Step 12 — Copy to Outputs and Present

```bash
cp /home/claude/[project]/[Topic]_YouTube_Lecture.pptx        /mnt/user-data/outputs/
cp /home/claude/[project]/[Topic]_Notes.md                     /mnt/user-data/outputs/
cp /home/claude/[project]/[Topic]_Improvements.docx            /mnt/user-data/outputs/
cp /home/claude/[project]/[Topic]_Medium_Blog.md               /mnt/user-data/outputs/
cp /home/claude/[project]/[Topic]_LinkedIn_Post.md             /mnt/user-data/outputs/
cp /home/claude/[project]/[Topic]_WithTranscript.ipynb         /mnt/user-data/outputs/
cp /home/claude/[project]/[Topic]_CellByCell_Transcript.md     /mnt/user-data/outputs/
```

Call `present_files` with all seven paths in this order:
1. PPTX
2. Notes MD
3. DOCX
4. Medium Blog MD
5. LinkedIn Post MD
6. Notebook (.ipynb)
7. Cell-by-Cell Transcript MD

---

## File Naming Convention

| File | Pattern | Example |
|------|---------|---------|
| PPTX | `[Topic]_YouTube_Lecture.pptx` | `HybridSearch_RAG_YouTube_Lecture.pptx` |
| Notes MD | `[Topic]_Notes.md` | `HybridSearch_RAG_Notes.md` |
| DOCX | `[Topic]_Improvements.docx` | `HybridSearch_RAG_Improvements.docx` |
| Medium Blog | `[Topic]_Medium_Blog.md` | `HybridSearch_RAG_Medium_Blog.md` |
| LinkedIn Post | `[Topic]_LinkedIn_Post.md` | `HybridSearch_RAG_LinkedIn_Post.md` |
| Notebook (with) | `[Topic]_WithTranscript.ipynb` | `HybridSearch_RAG_WithTranscript.ipynb` |
| Notebook (clean) | `[Topic]_Clean.ipynb` | `HybridSearch_RAG_Clean.ipynb` |
| Cell Transcript | `[Topic]_CellByCell_Transcript.md` | `HybridSearch_RAG_CellByCell_Transcript.md` |
| Mermaid Diagram | `[Topic]_Architecture_Mermaid.md` | `HybridSearch_Architecture_Mermaid.md` |
| Formula Ref | `[Topic]_Formula_Reference.md` | `HybridSearch_Formula_Reference.md` |
| Formula + Transcript | `[Topic]_Formula_Reference_WithTranscript.md` | `HybridSearch_Formula_Reference_WithTranscript.md` |
| Arch Diagram Transcript | `[Topic]_Architecture_Diagram_YouTube_Transcript.md` | (new in v3) |

---

## Branding Constants

| Element | Value |
|---------|-------|
| YouTube intro | "Hello guys! My name is Mayank Chugh and welcome to my YouTube channel!" |
| YouTube outro | "I'm Mayank Chugh, thank you for watching! Please Like, Share, and Subscribe. Take care!" |
| Like/Subscribe badge | Orange rounded rectangle on PPTX slides 1, analogy, stats, final |
| Slide 1 byline | "by Mayank Chugh" — italic teal below title |
| Channel handle | @itaienthusiast |
| GitHub | mayankchugh-learning |
| Medium | @mayankchugh.jobathk |
| Gumroad | mayanklearns.gumroad.com |

---

## Platform Rules at a Glance

| Rule | PPTX Notes | Notes MD | DOCX | Medium | LinkedIn | Notebook | Cell Transcript |
|------|-----------|----------|------|--------|----------|----------|----------------|
| Code | ❌ | ❌ | ✅ | ❌ | ❌ | ✅ | ❌ |
| Transcript text | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ gold blocks | ✅ narration |
| Platform switches | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ required |
| Actual scores | ✅ slide 7 | ✅ section 6 | ✅ | ✅ | ✅ hook | ✅ header | ✅ cell 30+ |
| Paper citations | ✅ notes | ✅ section 7 | ✅ | ✅ | optional | ✅ header | ✅ closing |
| Inline comments | ✅ notes | N/A | ✅ | N/A | N/A | ❌ clean code | N/A |
| External links | ❌ | ❌ | ❌ | ✅ | "in comments" | ❌ | ❌ |
| Hashtags | ❌ | ❌ | ❌ | 4–5 end | 3–5 end | ❌ | ❌ |

---

## Common Pitfalls

### Content
- Never invent facts — only use stats from transcript or executed notebook outputs
- Never use placeholder scores (0.99) — always extract real scores from executed notebook
- Don't say "Cohere Playground → Rerank" — that tab does not exist
- Don't add code to MD, Medium, or LinkedIn — prose only
- Don't copy speaker notes into Medium — rewrite fresh
- Don't use markdown formatting in LinkedIn — emojis only

### Platform Switching
- Every switch must have: WHAT URL, WHAT TO DO step-by-step, WHAT TO SAY, RETURN marker
- Cohere: only show API Keys and Billing & Usage — never Playground for rerank
- Weaviate: show console minimum 4 times: credentials, empty check, schema confirm, post-index browse
- Always include a GraphQL test query when showing Weaviate console post-indexing
- Billing & Usage: always show cost = $0.00 — emphasise free trial covers the whole demo

### PPTX
- Don't use `#` in hex colors — causes pptxgenjs file corruption
- Don't skip PPTX QA — always visually inspect every slide
- Don't use placeholder 0.99 in slide 7 — use actual score from executed notebook
- Don't label LLM as a different model than what the notebook uses

### Notebook
- Don't use `weaviate.Client()` — removed December 2024
- Don't use `WeaviateHybridSearchRetriever` with v4 client — broken
- Don't use `retriever.add_documents()` with v4 client — use `collection.batch.dynamic()`
- Don't import `CohereRerank` from `langchain.retrievers.document_compressors` — use `langchain_cohere`
- Don't import `ContextualCompressionRetriever` from `langchain.retrievers` — use `langchain_classic.retrievers`
- Don't pass `temperature`, `top_k`, `top_p` to Qwen3 pipeline — silently ignored, generates warning
- Don't add `bos_token_id = 1` for Qwen3 — only needed for Zephyr
- Don't hardcode API keys — always `userdata.get()`
- Don't add inline comments to recording notebook — clean code, verbal explanation

### File delivery
- Don't rely on inline code blocks for scripts user needs — save as .md file
- Don't present files one at a time if user reports download issues — present all together
- Don't show Mermaid only inline — always save as downloadable .md
