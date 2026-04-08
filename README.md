📄 RAG Document Q&A Assistant
A Retrieval-Augmented Generation (RAG) system that allows users to ask questions about PDF documents and receive accurate, context-based answers.
________________________________________
⚙️ Tech Stack
•	LangChain 
•	PyMuPDF 
•	ChromaDB (Vector Database) 
•	HuggingFace Embeddings (all-MiniLM-L6-v2) 
•	Ollama (phi3 LLM) 
•	Gradio (UI) 
________________________________________
🧠 How It Works
1.	Load PDF documents using PyMuPDF 
2.	Split text into chunks using a recursive strategy 
3.	Convert chunks into embeddings 
4.	Store embeddings in ChromaDB 
5.	Retrieve relevant chunks based on user query 
6.	Pass context + question to LLM (phi3) 
7.	Return answer with source references 
________________________________________
🔍 Features
✅ Basic Version
•	Document ingestion 
•	Embedding + vector storage 
•	Semantic retrieval 
•	LLM-based answering 
🚀 Improved Version
•	Optimized chunking (overlap tuning) 
•	Retrieval tuning (k=4) 
•	Structured prompt to reduce hallucinations 
•	Source attribution for transparency 
•	Persistent vector database (faster reload) 
•	Simple evaluation pipeline 
________________________________________
📊 Example Output
Question:
What is the main topic of the document?
Answer:
[Generated answer based on context]
Sources:
•	Source 1: [chunk preview] 
•	Source 2: [chunk preview] 
________________________________________
🧪 Evaluation
A small evaluation pipeline was added to test system performance across predefined questions, helping validate retrieval and answer quality.
________________________________________
💡 Key Learnings
•	Retrieval quality is more important than model size 
•	Chunking strategy significantly impacts results 
•	Prompt design reduces hallucinations 
•	Transparency (showing sources) improves trust 
________________________________________
🚧 Future Improvements
•	Add re-ranking for better retrieval precision 
•	Improve UI with chat history 
•	Support multiple document ingestion 
•	Deploy as a web application 
________________________________________
▶️ Run Locally
pip install -r requirements.txt
ollama serve
python app.py

