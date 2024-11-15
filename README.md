# PDF Query System with LangChain, ChromaDB, and Local LLM Integration

This project is a PDF Query System that allows users to interact with uploaded PDFs by asking questions and receiving relevant, context-driven responses. The system uses **LangChain** for retrieval-augmented generation, **ChromaDB** for vector storage, and a locally hosted **Large Language Model (LLM)** via **Ollama** to ensure privacy and offline functionality. 

## Project Components

### 1. **Backend Framework**: LangChain
   - We use **LangChain** for its robust support for retrieval-augmented generation (RAG) applications, enabling effective document query and response generation.
   - **LangChain** helps structure the application around the interaction between the retrieval system and the language model for optimal performance.

### 2. **Frontend Framework**: Streamlit
   - **Streamlit** is used to create a simple, interactive web interface where users can upload PDF files, enter questions, and view responses.
   - This open-source framework allows for quick, flexible app development, ideal for data science and machine learning projects.

### 3. **Vector Store**: ChromaDB
   - **ChromaDB** manages and queries embeddings, allowing efficient retrieval of document chunks relevant to user queries.
   - Vector storage is a critical component for maintaining an index of PDF content, enabling quick access to relevant sections.

### 4. **Embedding Model**: Sentence Transformers
   - **Sentence Transformers** (specifically, the "all-MiniLM-L6-v2" model) are used to generate vector embeddings from PDF content.
   - This model is run locally to ensure no external dependencies, maintaining the privacy and offline functionality of the application.

### 5. **Local Language Model (LLM)**: Ollama
   - A locally hosted LLM is accessed via **Ollama**, providing conversational responses to user queries without the need for any external API keys.
   - This setup keeps the application entirely local, ensuring data privacy and independence from internet connectivity for querying the language model.

## Project Structure

- **`app.py`**: The main application script that initializes the vector store, embedding model, LLM, and Streamlit UI.
- **`requirements.txt`**: Lists required packages.
- **`README.md`**: Project documentation.
- **`/content/chroma_db/`**: Persistent directory for ChromaDB storage.
- **`sample_pdfs/`**: A directory for sample PDFs used for testing.

## Installation and Setup

### Prerequisites

- Python 3.8+
- [Streamlit](https://streamlit.io) for UI
- [Ollama](https://ollama.com) for the local LLM server
- Required Python packages (listed in `requirements.txt`)

### Install Required Packages

```bash
pip install -r requirements.txt
```

### Running the Ollama Server Locally

The application is configured to run completely locally without the need for external API keys. Ensure that the Ollama server is up and running on `http://127.0.0.1:11434`.

```bash
# Check if Ollama is running on the correct port
lsof -i :11434

# Start server (if needed)
# Note: Port conflicts may require using a different port.
```

### Running the Application

1. Clone the repository and navigate to the project folder:

    ```bash
    git clone <repository_url>
    cd <project_folder>
    ```

2. Add your PDF files to the `pdf_paths` list in `app.py`.

3. Run the Streamlit application:

    ```bash
    streamlit run app.py
    ```

4. Access the application at `http://localhost:8501`.

## Usage

1. Start the application and ensure your PDFs are uploaded.
2. Enter a question related to the PDF content.
3. The system retrieves relevant chunks from ChromaDB and provides a response generated by the local LLM.
4. Sources of the response are displayed for reference.

## Code Highlights

- **Custom LLM Integration**: The `CustomOllamaLLM` class in `app.py` is designed to interface with Ollama's local server, ensuring all queries are processed locally without external API keys.
- **LangChain and ChromaDB**: Using LangChain with ChromaDB facilitates efficient retrieval and response generation, enabling accurate document querying.
- **Local Embedding Generation**: Sentence Transformers run locally to convert document content into embeddings, stored in ChromaDB for quick access.

## Known Issues

- **Port Conflicts**: Ensure no multiple instances of Ollama are running. Use `lsof` to troubleshoot conflicts.
- **Server Unavailability**: If the Ollama server is unreachable, confirm it’s installed and running on the expected port.

## Future Improvements

- **Real-time PDF Uploads**: Add Streamlit-based upload functionality for a more dynamic interface.
- **Advanced LLMs**: Experiment with alternative LLMs for enhanced conversational capabilities.
- **Expanded Retrieval Options**: Explore additional retrieval methods within LangChain to improve response accuracy.

## Requirements

- Python 3.8+
- `fitz` for PDF handling
- `langchain` for LLM-based document processing
- `streamlit` for UI development
- `chromadb` for vector storage and retrieval
