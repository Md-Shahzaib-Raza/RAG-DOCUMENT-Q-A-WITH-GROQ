# RAG Document Q&A Bot

A Streamlit app for asking questions about research papers in PDF format. It
loads PDFs from `research_papers/`, splits and embeds their contents, retrieves
relevant passages, and uses Groq to generate an answer based on that context.

## Live demo

[Open the app on Streamlit](https://rag-document-q-a-with-groq-nexpaonwrop7bhip2553ay.streamlit.app/)

## Features

- Load PDF documents from a local folder
- Create a FAISS vector store using Hugging Face embeddings
- Retrieve relevant passages for each question
- Generate answers with a Groq-hosted language model
- View retrieved passages in the app

## Requirements

- Python 3.13 or newer
- [uv](https://docs.astral.sh/uv/getting-started/installation/)
- A Groq API key
- PDF files to query

## Setup

Clone the repository and enter the project directory:

```shell
git clone <git clone https://github.com/Md-Shahzaib-Raza/RAG-DOCUMENT-Q-A-WITH-GROQ.git>
```

Install the project dependencies with uv:

```shell
uv sync
```

Create a `.env` file in the project root and add your Groq API key:

```dotenv
GROQ_API_KEY=your_groq_api_key
```

Add the PDF files you want to query to `research_papers/`.

Do not commit `.env` or publish your API key.

## Run

Start the Streamlit app:

```shell
uv run streamlit run app.py
```

In the app:

1. Select **Document Embeddings** and wait for the vector database to be ready.
2. Enter a question about the PDFs.
3. Expand **Document similarity search** to view the retrieved passages.

## Configuration

The app currently uses the `openai/gpt-oss-20b` model through Groq. It splits
documents into chunks of 1,000 characters with 200 characters of overlap and
processes up to the first 50 loaded documents when creating embeddings.

## Project structure

```text
.
├── app.py
├── research_papers/       # Add PDF files here
├── src/
│   └── rag_bot/
├── pyproject.toml         # Project metadata and dependencies
├── uv.lock                # Locked dependency versions
└── README.md
```

## Updating dependencies

Add or remove project dependencies in `pyproject.toml`, then update the lock
file and sync the environment:

```shell
uv lock
uv sync
```