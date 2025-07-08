# 📊 SEC 10-K Financial Reports Question Answering & Comparison (RAG + Gradio)

This project provides a powerful, interactive Gradio application for querying and comparing **SEC 10-K financial filings** using a **Retrieval-Augmented Generation (RAG)** pipeline powered by **Mistral-7B-Instruct** and semantic search.

Built entirely in **Google Colab**, this solution enables both financial analysts and NLP practitioners to extract insights from lengthy filings efficiently using natural language queries.

---

## 🚀 Features

- 🔍 **Ask Natural Language Questions** about any 10-K filing (e.g., "What are the key risks?" or "Summarize operational challenges").
- 🧠 **Hybrid Search** using BM25 + FAISS + Semantic Reranking
- 🪄 **Prompt Variants**:
  - `default`: General answers
  - `extract_bullets`: Clean factual bullets
  - `kpi_extract`: Extract KPIs
  - `summarize`: Concise summaries
- 🧱 **Sliding Window Support** for handling long context windows (10-Ks are huge!)
- 🔄 **Compare Two Filings** (e.g., compare risk disclosures between years)
- 📁 **Data Download**: Export results and sources as CSV or TXT
- 🌐 **Gradio UI**: Fully interactive interface with dropdowns, file selection, and pre-loaded examples

---

## 📝 How It Works

1. **Preprocess Filings**:
   - SEC 10-K HTML files are chunked and embedded using `SentenceTransformer`.
   - Embeddings and metadata are stored as a `.pkl` file.

2. **Hybrid Retrieval**:
   - Combines **BM25** lexical scores with **FAISS** dense retrieval for top-ranked chunks.
   - Uses semantic similarity with Sentence-BERT for final reranking.

3. **LLM Answering**:
   - Contextual prompts are constructed and passed to **Mistral-7B-Instruct** (via `transformers`).
   - Responses are deduplicated and formatted based on the selected prompt style.

4. **Gradio UI**:
   - Users can run queries, compare filings, and export results visually.

---

## 🧪 Requirements

- Python 3.8+
- Google Colab (preferred)
- GPU-enabled runtime (recommended for faster inference)

Dependencies are loaded via:

```python
!pip install transformers accelerate sentence-transformers faiss-cpu gradio rank_bm25
