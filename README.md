# Hello RAG

A small learning project that demonstrates the basic flow of Retrieval-Augmented Generation (RAG) using Python and Ollama.

The project loads a text dataset of cat facts, turns each line into an embedding, retrieves the most relevant facts for a user question, and sends those facts to a local language model to generate an answer.

## What This Project Shows

- Loading a simple text dataset from `cat-facts.txt`
- Creating embeddings for each text chunk with Ollama
- Storing chunks and embeddings in an in-memory vector database
- Comparing a user query against stored embeddings with cosine similarity
- Retrieving the most relevant chunks
- Passing retrieved context into a chat model
- Streaming the model response back in the terminal

## Project Files

- `ingest.py` - Main Python script for embedding, retrieval, and chat
- `cat-facts.txt` - Source dataset used as the knowledge base

## Requirements

- Python 3
- Ollama installed and running
- Python `ollama` package

Install the Python package:

```bash
pip install ollama
```

The script uses these Ollama models:

- Embedding model: `hf.co/CompendiumLabs/bge-base-en-v1.5-gguf`
- Language model: `hf.co/bartowski/Llama-3.2-1B-Instruct-GGUF`

## How To Run

From the project folder:

```bash
python ingest.py
```

Then type a question when prompted, for example:

```text
Ask me a question: Why do cats purr?
```

The script will:

1. Load facts from `cat-facts.txt`
2. Embed each fact
3. Retrieve the most relevant facts for your question
4. Ask the language model to answer using only that retrieved context

## Notes

This is a learning project, so the vector database is stored only in memory. Each time the script runs, it rebuilds the embeddings from scratch.

Possible next improvements:

- Save embeddings to disk so startup is faster
- Split larger documents into chunks
- Add a real vector database such as Chroma or FAISS
- Turn the script into a small web app
- Add support for multiple source documents
