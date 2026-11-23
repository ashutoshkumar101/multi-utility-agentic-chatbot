# Multi-Utility Agentic Chatbot

An AI-powered multi-utility chatbot built using **Google Gemini, LangGraph, LangChain, and Streamlit**. The application combines conversational AI, Retrieval-Augmented Generation (RAG), and agentic tool calling to perform multiple tasks through a single interface.

## Features

- **AI-Powered Conversations:** Uses Google Gemini for natural language understanding and response generation.
- **PDF Question Answering:** Upload PDF documents and ask questions based on their content.
- **Retrieval-Augmented Generation (RAG):** Uses document chunking, Gemini embeddings, and FAISS vector search to retrieve relevant information.
- **Agentic Workflow:** Uses LangGraph to manage conversation flow and dynamically execute tools.
- **Web Search:** Retrieves online information using DuckDuckGo.
- **Calculator:** Performs mathematical calculations through tool calling.
- **Stock Price Lookup:** Fetches stock market information using Alpha Vantage.
- **Conversation Persistence:** Uses LangGraph checkpointing with SQLite to maintain conversation history.
- **Observability and Monitoring:** Integrates LangSmith to trace and monitor agent execution.

## Tech Stack

| Component | Technology |
|---|---|
| Programming Language | Python |
| Large Language Model | Google Gemini |
| Agent Framework | LangGraph |
| LLM Integration | LangChain |
| Embedding Model | Gemini Embeddings |
| Vector Store | FAISS |
| PDF Processing | PyPDFLoader |
| Frontend | Streamlit |
| Checkpointing | SQLite |
| Web Search | DuckDuckGo |
| Monitoring | LangSmith |
| Stock Data | Alpha Vantage |

## Project Structure

```text
multi-utility-agentic-chatbot/
│
├── app.py
│
├── backend/
│   ├── __init__.py
│   └── langgraph_rag_backend.py
│
├── requirements.txt
├── .env.example
├── .gitignore
├── README.md

```

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ashutoshkumar101/multi-utility-agentic-chatbot.git

cd multi-utility-agentic-chatbot
```

### 2. Create a Virtual Environment

```bash
python -m venv myvenv
```

Activate the environment.

**Windows PowerShell:**

```powershell
.\myvenv\Scripts\Activate.ps1
```

### 3. Install Dependencies

```bash
python -m pip install --upgrade pip

pip install -r requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file in the root directory using `.env.example` as a reference.

Configure the following variables:

```env
GOOGLE_API_KEY=your_gemini_api_key

LANGSMITH_TRACING=true
LANGSMITH_API_KEY=your_langsmith_api_key
LANGSMITH_PROJECT=Gemini-PDF-RAG-Chatbot

ALPHA_VANTAGE_API_KEY=your_alpha_vantage_api_key
```

**Note:** Depending on your backend configuration, you may use `GEMINI_API_KEY` instead of `GOOGLE_API_KEY`.

Never upload your actual `.env` file or expose API keys publicly.

### 5. Run the Application

```bash
streamlit run app.py
```

The Streamlit application will open in your default browser.

## Architecture Overview

The application follows an agentic workflow:

1. The user interacts with the Streamlit frontend.
2. The request is passed to the LangGraph backend.
3. Google Gemini processes the request and determines whether a tool is required.
4. LangGraph executes the selected tool when necessary.
5. For PDF-related questions, the RAG pipeline retrieves relevant document chunks using FAISS.
6. The retrieved context or tool output is returned to Gemini.
7. Gemini generates the final response.
8. LangGraph checkpointing maintains conversation state, while LangSmith provides execution tracing.

## Environment Variables

| Variable | Description |
|---|---|
| `GOOGLE_API_KEY` | Google Gemini API authentication |
| `GEMINI_API_KEY` | Alternative Gemini API variable, if supported by backend |
| `LANGSMITH_TRACING` | Enables or disables LangSmith tracing |
| `LANGSMITH_API_KEY` | LangSmith authentication |
| `LANGSMITH_PROJECT` | LangSmith project name |
| `ALPHA_VANTAGE_API_KEY` | Alpha Vantage API authentication |

## Future Improvements

- OCR support for scanned PDF documents.
- Persistent vector storage across application restarts.
- Improved agent routing and tool selection.
- Enhanced conversation and document management.
- Deployment with a publicly accessible application URL.
- Additional tools and utility integrations.

## Author

**Ashutosh Kumar**

B.Tech – Mathematics and Computing  
Indian Institute of Information Technology, Bhagalpur

---

*Developed as a project exploring Agentic AI, Retrieval-Augmented Generation, and LLM-based tool integration.*
