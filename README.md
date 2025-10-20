# Agentic RAG System

An intelligent Retrieval-Augmented Generation (RAG) system that enables semantic querying of PDF documents using advanced language models and vector embeddings.

## Overview

This project implements an agentic RAG pipeline that allows users to:
- Upload and process multiple PDF documents
- Query documents using natural language
- Receive contextually relevant, AI-generated responses
- Export answers as PDF or text files
- Automatically detect and handle document updates

## Architecture

### Core Components

**RAG Pipeline**
1. **Document Processing** - Extracts and chunks text from PDF files
2. **Embedding Generation** - Creates vector embeddings using SentenceTransformer
3. **Intelligent Retrieval** - Finds relevant chunks via cosine similarity
4. **LLM Response** - Generates answers using Gemma2 language model
5. **Web Interface** - Django-based frontend for user interaction

### Technology Stack

| Component | Technology |
|-----------|-----------|
| Language | Python |
| Deep Learning | PyTorch |
| Embeddings | SentenceTransformer (HuggingFace) |
| LLM | Gemma2 (via Ollama) |
| NLP | NLTK |
| Numerics | NumPy |
| Web Framework | Django |

## Project Structure

```
RAG/
├── Documents.py      # PDF loading & change detection
├── Processing.py     # Text chunking
├── Embedding.py      # Vector embedding generation
├── Retriever.py      # Similarity search
├── LLM.py           # Language model interface
├── Main.py          # Orchestration layer
└── Source_files/    # PDF documents

Website/
└── RAGapp/          # Django web application
```

## Installation

### Prerequisites
- Python 3.8+
- Ollama installed locally
- Ngrok account (for Colab setup)

### Setup

1. **Clone the repository**
```bash
git clone <repository-url>
cd Agentic-RAG-main
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Install Ollama**
   - Download from: https://ollama.com/download/windows
   - Pull the Gemma2 model:
```bash
ollama run gemma2:2b
```

## Usage

### Running with Google Colab (Recommended)

For enhanced performance, use Google Colab with a local tunnel:

1. **Setup Ngrok**
   - Create account: https://ngrok.com/
   - Save your authentication token

2. **Configure Colab**
   - Open `ollam_server.ipynb` in Google Colab
   - Run the first two cells
   - In the third cell, set your token:
```python
AUTH_TOKEN = "your_ngrok_token_here"
```
   - Run the cell to get your ngrok URL (ends with `ngrok-free.app`)

3. **Configure Local Environment**
   - Open PowerShell and set the Ollama host:
```powershell
$env:OLLAMA_HOST="https://your-url.ngrok-free.app"
```

4. **Update LLM Configuration**
   - Edit `RAG/LLM.py`
   - Set `self.ollama_host` to your ngrok URL

5. **Start the Application**
```bash
cd Website
python manage.py runserver
```

6. **Access the Interface**
   - Navigate to: http://localhost:8000

### Running Locally

If running without Colab, ensure Ollama is running locally:

```bash
ollama serve
cd Website
python manage.py runserver
```

## Features

### Smart Document Management
- **Automatic Change Detection** - Uses file hashing to avoid redundant processing
- **Incremental Updates** - Only reprocesses modified documents
- **Multi-document Support** - Handle multiple PDFs simultaneously

### Intelligent Querying
- **Semantic Search** - Vector-based similarity matching
- **Context Awareness** - Identifies out-of-scope queries
- **Relevant Responses** - LLM-generated answers based on retrieved context

### Export Capabilities
- Save responses as PDF documents
- Export answers as text files

## Example

![Alt text for the image](example.PNG)

## Model Options

Explore different Gemma2 variants:
- `gemma2:2b` - Lightweight, faster inference
- `gemma2:9b` - Balanced performance
- `gemma2:27b` - Maximum accuracy

Full model list: https://ollama.com/library/gemma2

## Future Enhancements

- [ ] Multi-LLM support (GPT, Claude, LLaMA)
- [ ] Enhanced UI/UX with modern frontend framework
- [ ] Optimized chunking strategies for large documents
- [ ] Real-time streaming responses
- [ ] Conversation history and memory
- [ ] Advanced query refinement

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

[Add your license here]

## Contact

[Add your contact information here]
