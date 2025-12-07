# academic-pdf-rag
A Python-based RAG (Retrieval-Augmented Generation) engine tailored for academic research. It ingests PDF documents into a local Chroma vector database and uses OpenAI's GPT-4o to answer questions with strict academic tone and precise page-level citations.
# Academic QA Engine 📚

A specialized Retrieval-Augmented Generation (RAG) system built with **LangChain** and **OpenAI**. This tool allows researchers and students to chat with their PDF documents, extracting answers supported by direct citations and page numbers.

## 🚀 Features

* **PDF Ingestion:** Automatically loads and splits PDF research papers.
* **Vector Search:** Uses **ChromaDB** for efficient semantic searching of document chunks.
* **Academic Tone:** Prompts GPT-4o to answer strictly based on context, avoiding hallucinations.
* **Source Citations:** Returns answers with exact filenames and page numbers (e.g., `paper.pdf (Page 4)`).

## 🛠️ Tech Stack

* **Python 3.9+**
* **LangChain** (Orchestration)
* **OpenAI GPT-4o** (LLM & Embeddings)
* **Chroma** (Vector Store)
* **PyPDF** (Document Loading)

## 📦 Installation

1.  **Clone the repository**
    ```bash
    git clone [https://github.com/yourusername/academic-qa-engine.git](https://github.com/yourusername/academic-qa-engine.git)
    cd academic-qa-engine
    ```

2.  **Install dependencies**
    ```bash
    pip install langchain langchain-community langchain-openai chromadb pypdf
    ```

3.  **Set up API Key**
    Open the script and replace the placeholder with your actual OpenAI API key:
    ```python
    API_KEY = "sk-..." 
    # Or better yet, use an environment variable (recommended)
    ```

## 📖 Usage

1.  Place your research papers (PDFs) in the project directory.
2.  Initialize the engine and ingest your documents:

    ```python
    from main import AcademicQAEngine

    # Initialize
    engine = AcademicQAEngine()

    # Ingest Documents (Run this once or when adding new files)
    engine.ingest_documents(["./research_paper_1.pdf", "./thesis.pdf"])
    ```

3.  Query the system:
    ```python
    response = engine.query("What are the limitations of the proposed method?")
    
    print(f"Answer: {response['answer']}")
    print(f"Sources: {response['citations']}")
    ```

## ⚙️ Configuration

You can adjust the chunking parameters in the `ingest_documents` method to optimize for different document types:

```python
text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=1000,  # Increase for larger context
    chunk_overlap=200 # Increase to ensure continuity between chunks
)
