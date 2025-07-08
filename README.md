# 📊 SEC 10-K Financial Reports Question & Answering System (RAG + Gradio)

This project is an interactive Gradio-based tool that lets users **query and compare SEC 10-K financial filings** using a **Retrieval-Augmented Generation (RAG)** pipeline with **Mistral-7B-Instruct**, semantic search, and hybrid retrieval.

Built entirely in **Google Colab**, it helps financial analysts and NLP practitioners extract insights from long 10-K documents using **natural language**.

---

## 🚀 Features

- 🔍 Ask natural language questions like:
  - _"What are the key risks?"_
  - _"Summarize operational challenges"_
- 🧠 **Hybrid Search** combining:
  - `BM25` (lexical)
  - `FAISS` (dense vector)
  - Semantic reranking using Sentence-BERT
- 🪄 Multiple Prompt Styles:
  - `default`: General answers  
  - `extract_bullets`: Clean factual bullets  
  - `kpi_extract`: Extract KPIs  
  - `summarize`: Concise summaries  
- 🧱 Sliding window support for handling huge 10-Ks
- 🔄 Compare two filings (e.g., risk disclosures year-over-year)
- 📁 Export answers and sources as `.csv` or `.txt`
- 🌐 Fully interactive **Gradio UI**

---

## 🧠 How It Works

### 1. Preprocess Filings
- SEC 10-K `.html` filings are parsed and chunked.
- Sentence embeddings are generated using `SentenceTransformer`.
- Outputs are saved to `.pkl` files.

### 2. Hybrid Retrieval
- Combines `BM25` and `FAISS` retrieval scores.
- Uses semantic similarity for reranking top results.

### 3. LLM QA (via RAG)
- Constructs a contextual prompt using retrieved chunks.
- Generates answers using `Mistral-7B-Instruct` (via `transformers`).

### 4. Gradio Interface
- Run queries, compare years, and download results—all visually.

---

## 🧪 Requirements

- Python 3.8+
- Google Colab (**recommended**)
- GPU-enabled runtime (for faster inference)

Install dependencies (in Colab):
```python
!pip install -U sec-api beautifulsoup4 sentence-transformers lxml faiss-cpu transformers accelerate bitsandbytes rank_bm25 gradio

