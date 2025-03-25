# Information Retrieval System from PDF

An end-to-end interactive Information Retrieval System that allows users to ask questions based on the contents of uploaded PDF files. The app uses local language models (via Ollama) and Hugging Face embeddings to process and retrieve information from documents. Built with LangChain, FAISS, and Streamlit.

## Table of Contents
- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [How It Works](#how-it-works)
- [Installation](#installation)
- [Run the App](#run-the-app)
- [Project Structure](#project-structure)
- [Future Improvements](#future-improvements)
- [License](#license)

## Overview
This project allows users to upload one or more PDF files, processes the contents, creates semantic embeddings using Hugging Face models, and enables a natural language interface powered by a local LLM (like LLaMA or Mistral via Ollama) to ask questions about the documents. Everything runs locally — no external API keys required.

## Tech Stack
Language: Python 3.10+  
Libraries: Streamlit, PyPDF2, LangChain, FAISS, Hugging Face Transformers  
LLM: Local models via Ollama (e.g., LLaMA3, Mistral)  
Embeddings: Hugging Face (`all-MiniLM-L6-v2`)  
Tools: VS Code, Git, Ollama, dotenv

## How It Works
1. PDFs are uploaded via the Streamlit sidebar.  
2. Text is extracted using `PyPDF2`.  
3. The text is split into overlapping chunks.  
4. Hugging Face Embeddings are generated for all chunks.  
5. FAISS is used to store and search semantically similar text.  
6. A local LLM via Ollama answers questions using LangChain's `ConversationalRetrievalChain`.

## Installation
```bash
# Clone the repository
git clone https://github.com/AbhinavS-30/Information-Retrieval-System.git
cd Information-Retrieval-System

# (Optional) Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate    # On Windows
source venv/bin/activate # On Mac/Linux

# Install dependencies
pip install -r requirements.txt

# Install and run a local model with Ollama
# Download from https://ollama.com
ollama run llama3
```

## Run the App
```bash
streamlit run app.py
```

- Go to `http://localhost:8501` in your browser.  
- Upload one or more PDF files.  
- Ask questions in natural language.

## Project Structure
```
├── app.py                      # Main Streamlit app
├── requirements.txt
├── .env                        # (Optional) for keys or config
├── src/
│   └── helper.py               # PDF parsing, chunking, embeddings, and retrieval
├── README.md
└── setup.py                    # Optional: for pip installable package
```

## Future Improvements
- Add support for multi-language documents  
- Streamline model selection through UI  
- Store and reuse FAISS indexes to avoid recomputation  
- Add confidence scores or source page highlights  
- Dockerize the app for easy deployment  

## License
This project is licensed under the [MIT License](LICENSE).
