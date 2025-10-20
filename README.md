# AI Agent for Document Discussion

An intelligent conversational AI system that enables natural language interaction with PDF documents through advanced retrieval-augmented generation (RAG) technology.

## Overview


This project creates an AI agent that can understand and discuss the contents of books and documents. Users can upload PDF files and engage in meaningful conversations about the content, receiving accurate, contextually relevant responses based on the document's information.

**Key Capabilities:**
- Process and understand multiple PDF documents
- Engage in natural conversations about document content
- Provide accurate, source-based answers
- Export conversation results
- Automatically handle document updates

## System Architecture

### Core Pipeline

1. **Document Ingestion** - Extracts and processes text from PDF files
2. **Content Vectorization** - Creates semantic embeddings using SentenceTransformer
3. **Intelligent Retrieval** - Finds relevant content through similarity search
4. **Response Generation** - Produces contextual answers using Gemma2 LLM
5. **Web Interface** - User-friendly Django application

### Technology Stack

| Component | Technology |
|-----------|-----------|
| Backend Language | Python 3.8+ |
| Machine Learning | PyTorch |
| Text Embeddings | SentenceTransformer (HuggingFace) |
| Language Model | Gemma2 (via Ollama) |
| Natural Language Processing | NLTK |
| Numerical Computing | NumPy |
| Web Framework | Django |
| Document Processing | PyPDF2 |

## Project Structure

```
RAG/
├── Documents.py      # PDF processing and change detection
├── Processing.py     # Text chunking and preprocessing
├── Embedding.py      # Vector embedding generation
├── Retriever.py      # Semantic similarity search
├── LLM.py           # Language model interface
├── Main.py          # System orchestration
└── Source_files/    # Document storage directory

Website/
└── RAGapp/          # Django web application
    ├── views.py     # Request handling
    ├── models.py    # Data models
    ├── urls.py      # URL routing
    └── templates/   # HTML templates
```

## Installation Guide

### System Requirements
- Python 3.8 or higher
- 8GB RAM minimum (16GB recommended)
- Ollama runtime environment
- Internet connection for model downloads

### Quick Setup

1. **Clone Repository**
```bash
git clone https://github.com/your-username/ai-document-agent.git
cd ai-document-agent
```

2. **Install Python Dependencies**
```bash
pip install -r requirements.txt
```

3. **Setup Ollama**
   - Download: https://ollama.com/download
   - Install Gemma2 model:
```bash
ollama pull gemma2:2b
```

4. **Initialize Database**
```bash
cd Website
python manage.py migrate
```

## Usage Instructions

### Local Development Setup

1. **Start Ollama Service**
```bash
ollama serve
```

2. **Launch Web Application**
```bash
cd Website
python manage.py runserver
```

3. **Access Interface**
   - Open browser to: http://localhost:8000
   - Upload PDF documents
   - Start asking questions about your documents

### Cloud Setup with Google Colab

For enhanced performance using Google Colab's GPU resources:

1. **Configure Ngrok Tunnel**
   - Sign up at: https://ngrok.com/
   - Get authentication token

2. **Setup Colab Environment**
   - Open `ollama_server.ipynb` in Google Colab
   - Add your ngrok token:
```python
AUTH_TOKEN = "your_actual_ngrok_token"
```
   - Execute cells to get public URL

3. **Connect Local Application**
```bash
# Windows PowerShell
$env:OLLAMA_HOST="https://your-ngrok-url.ngrok-free.app"

# Linux/Mac
export OLLAMA_HOST="https://your-ngrok-url.ngrok-free.app"
```

4. **Update Configuration**
   - Edit `RAG/LLM.py`
   - Set `ollama_host` to your ngrok URL

## Key Features

### Intelligent Document Processing
- **Smart Change Detection** - Avoids reprocessing unchanged documents
- **Efficient Chunking** - Optimizes text segments for better retrieval
- **Multi-format Support** - Handles various PDF structures and layouts

### Advanced Conversational AI
- **Context-Aware Responses** - Maintains conversation context
- **Source Attribution** - References specific document sections
- **Relevance Filtering** - Identifies when questions are outside document scope

### User Experience
- **Intuitive Web Interface** - Clean, responsive design
- **Real-time Processing** - Fast query responses
- **Export Options** - Save conversations as PDF or text
- **Document Management** - Easy upload and organization

## Model Configuration

Choose the appropriate Gemma2 variant based on your hardware:

- **gemma2:2b** - Fast responses, lower memory usage (4GB RAM)
- **gemma2:9b** - Balanced performance and quality (8GB RAM)
- **gemma2:27b** - Highest quality responses (16GB+ RAM)

View all available models: https://ollama.com/library/gemma2

## Development Roadmap

### Planned Enhancements
- **Multi-Model Support** - Integration with GPT, Claude, and LLaMA
- **Advanced UI** - Modern React-based frontend
- **Conversation Memory** - Persistent chat history
- **Real-time Streaming** - Live response generation
- **Enhanced Analytics** - Usage statistics and insights
- **API Development** - RESTful API for external integrations

### Performance Optimizations
- **Caching System** - Faster repeated queries
- **Batch Processing** - Efficient multi-document handling
- **Compression** - Reduced storage requirements

## Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes and test thoroughly
4. Submit a pull request with detailed description

### Development Guidelines
- Follow PEP 8 style guidelines
- Add unit tests for new features
- Update documentation as needed
- Ensure backward compatibility

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support and Contact

For questions, issues, or suggestions:
- **GitHub Issues**: Report bugs and request features
- **Documentation**: Check the [Wiki](../../wiki) for detailed guides
- **Community**: Join discussions in the [Discussions](../../discussions) section

---

**Built with ❤️ for the AI community**
