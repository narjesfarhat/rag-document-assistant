# 📄 RAG Document Q&A Assistant

> Ask questions about any PDF — get accurate, sourced answers powered by a fully local AI pipeline.

Built as part of an AI engineering assignment, then improved beyond the original spec.  
No API keys. No cloud. Runs entirely on your machine.

---

## 🧠 What It Does

Upload a PDF document and ask it anything in natural language.  
The system retrieves the most relevant chunks, feeds them to a local LLM, and returns a concise answer — with the exact source passages it used.

If the answer isn't in the document, it says **"I don't know"** instead of hallucinating.

---

## ⚙️ Tech Stack

| Component | Tool |
|---|---|
| Document Loading | PyMuPDF (fitz) |
| Text Splitting | LangChain RecursiveCharacterTextSplitter |
| Embeddings | HuggingFace `all-MiniLM-L6-v2` |
| Vector Database | ChromaDB (persistent) |
| LLM | phi3 via Ollama (runs locally) |
| UI | Gradio |
| Orchestration | LangChain |

---

## 🚀 Getting Started

### 1. Prerequisites

- Python 3.10+
- [Ollama](https://ollama.com) installed and running
- phi3 model pulled:

```bash
ollama pull phi3
ollama serve
```

### 2. Clone the repository

```bash
git clone https://github.com/narjesfarhat/rag-document-assistant.git
cd rag-document-assistant
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add your PDF

Place your PDF file in the project folder and update this line in `rag_assistant.py`:

```python
PDF_PATH = "your_document.pdf"
```

### 5. Run the app

```bash
python rag_assistant.py
```

Then open your browser at `http://127.0.0.1:7860`

---

## 🔍 Key Features

- **Persistent vector store** — ChromaDB saves embeddings so they are not rebuilt on every run
- **Source attribution** — every answer shows the exact passages it was retrieved from
- **Hallucination control** — structured prompt forces the model to say "I don't know" when the answer is not in the document
- **Optimized retrieval** — overlap chunking and k=4 retrieval for better context coverage
- **Evaluation mode** — built-in test function to measure response quality
- **Full logging** — every pipeline stage is logged for easy debugging

---

## 📁 Project Structure

```
rag-document-assistant/
├── rag_assistant.py      # Main pipeline and Gradio UI
├── requirements.txt      # Python dependencies
├── .gitignore            # Excludes PDF, chroma_db, venv
└── README.md
```

---

## 💡 What I Learned

This project went through two full rewrites.

The first challenge was environment setup — Ollama crashed on first install, the installer broke mid-way on the second attempt, and LangChain + ChromaDB had released breaking API changes that made every tutorial online outdated. The code had to be rewritten from scratch to match current library versions.

The second challenge was quality. A working pipeline is not the same as a reliable one. Chunking without overlap lost context. The vector store rebuilt itself every run. The LLM hallucinated when it lacked information. Each problem had a specific fix, and understanding each fix is what made this project worth building.

---

## 🔮 What's Next

- [ ] Hybrid search (dense + sparse)
- [ ] Rerankers for better retrieval precision
- [ ] Context compression
- [ ] Memory-aware multi-turn chat
- [ ] Deployment to Hugging Face Spaces

---

## 👩‍💻 Author

**Narjes Farhat**  
AI Student · Building in public  
[GitHub](https://github.com/narjesfarhat) · [LinkedIn](https://linkedin.com/in/narjesfarhat)

---

## 📄 License

MIT License — free to use, modify, and build on.
