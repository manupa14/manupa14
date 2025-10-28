---

# 🔍 Manuel Pagliaruzza – Featured Projects

Welcome to a curated snapshot of my most impactful technical work, spanning applied AI, workflow automation, and production-grade engineering.

---

## 📚 RAG — *Crime & Punishment* (Pinecone + Ollama + Gmail)

**Repo:** [RAG-Pinecone-Langchain-GmailAPI](https://github.com/manupa14/RAG-Pinecone-Langchain-GmailAPI)
**Stack:** LangChain 0.2+, `langchain-ollama`, Pinecone serverless, Ollama (`qwen2:7b`, `nomic-embed-text`), Gmail API (OAuth Desktop), `tqdm`, `python-dotenv`

**What it does**

* **Ingest:** chunks the novel, embeds with `nomic-embed-text` (768-d) via Ollama, upserts into a Pinecone index.
* **Answer:** embeds the question, retrieves top-k chunks by cosine, and has `qwen2:7b` answer **only** from context.
* **Email:** sends the answer + brief citations to your inbox via Gmail API.

**Quick start**

```bash
pip install -r requirements.txt
ollama pull qwen2:7b
ollama pull nomic-embed-text
cp .env.example .env  # fill Pinecone key/index/region, optional email defaults
# put data/crime_and_punishment.txt in place

python ingest.py
python ask_and_email.py "Why did Raskolnikov visit Sonya?" you@example.com
```

**Notes**

* Gmail auth is **per user**: each developer creates their **own** Google Cloud project, enables Gmail API, adds their Gmail as a **Test user**, and downloads `credentials.json` (Desktop App) to the repo root. First run creates `token.json`.
* Secrets (`.env`, `credentials.json`, `token.json`) are `.gitignore`d.

---

## 📚 RAG — *Crime & Punishment* (Chroma + Ollama)

**Repo:** *add link to your Chroma repo here*
**Stack:** LangChain 0.2+, ChromaDB, Ollama (`qwen2:7b`, `nomic-embed-text`)

**What it does**

* Same retrieval-augmented flow as above, but uses **Chroma** as the local vector store (handy for offline demos).
* Clean ingest → query pipeline; ideal as a minimal baseline for RAG without external services.

**Typical usage**

* `ingest.py` (or similar) to chunk + embed + persist to Chroma.
* `ask.py` (or similar) to retrieve top-k and answer with `qwen2:7b`.
  *See that repo’s README for the exact commands.*

---

## 🏢 Invisible Technologies – Applied AI & Workflow Automation

A significant portion of my recent work has been dedicated to enhancing Invisible Technologies’ internal agentic automation engine. In this role, I design, implement, and refine production workflows that merge LLM reasoning, structured task orchestration, and data-driven automation.

Due to confidentiality agreements, the source code and architectural details of these projects are private. However, my key contributions include:

* **Agentic Workflow Design:** scalable, YAML-defined automations with reasoning steps, validation layers, and execution delegates.
* **Prompt Vetting & Embedding Pipelines:** Python systems to pre-screen LLM inputs via vector similarity and local embedding searches.
* **Execution Orchestration:** contributions to the modular step execution system (including open-source components like `cem-step-execution`).

These systems are now fundamental to Invisible’s AI-driven process automation platform across multiple client verticals.

---

## 🧠 Melanoma Detection – Deep Learning Thesis

**GitHub:** [MelanomaDetection](https://github.com/manupa14/MelanomaDetection)

End-to-end CNN melanoma classifier trained on dermoscopic imagery; leverages ResNet-style blocks and metadata-aware preprocessing.

* Combines image analysis with patient metadata to improve diagnostic precision.
* Demonstrates practical deep-learning application in a medical setting.

---

## 💳 AutoPaymentApp – Python Web Automation

**GitHub:** [AutoPaymentApp](https://github.com/manupa14/AutoPaymentApp)

Lightweight automation tool (Python + Selenium) for repetitive payment workflows.

* Spreadsheet parsing, state validation, robust browser automation & error handling.
* Originally built for internal use at Invisible Technologies; later generalized and open-sourced.

---

## 🔧 Tech I use a lot

LangChain • Ollama • Pinecone • Chroma • FastAPI • Postgres/pgvector • Redis • Python • YAML workflows • CI/CD • Prompt/embedding evals

---

## 💡 About Me

I’m passionate about applied AI, workflow automation, and building intelligent systems that bridge the gap between reasoning and execution. I’m always open to new collaborations and interesting problems.

---

### Repo hygiene (for collaborators)

* Create your own **Gmail OAuth** project/credentials when using the Pinecone RAG email feature.
* Do **not** commit secrets: `.env`, `credentials.json`, `token.json` are ignored by `.gitignore`.
* The novel text file is local-only (`data/crime_and_punishment.txt`) and not committed.

---

