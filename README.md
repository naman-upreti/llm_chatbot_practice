# 🤖 LLM Chatbot Practice - Local AI Assistant

A comprehensive project demonstrating how to build and deploy local Large Language Model (LLM) chatbots using modern Python frameworks. This project showcases various implementations from basic completions to advanced conversational AI with memory and LangChain integration.

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Technologies Used](#technologies-used)
- [Implementation Examples](#implementation-examples)
- [Configuration](#configuration)
- [Resources](#resources)

## 🎯 Overview

This project demonstrates building AI chatbots that run entirely on your local machine using quantized LLM models. It includes multiple implementations ranging from simple text completions to sophisticated conversational interfaces with memory management and streaming responses.

**Key Highlights:**
- 🏠 **100% Local** - No API keys required, runs completely offline
- ⚡ **Fast & Efficient** - Uses quantized GGUF models for optimal performance
- 💬 **Interactive UI** - Beautiful chat interfaces powered by Chainlit
- 🧠 **Memory Management** - Maintains conversation context across sessions
- 🔗 **LangChain Integration** - Advanced prompt engineering and chains

## ✨ Features

### Core Capabilities
- **Simple Text Completion** - Basic LLM inference
- **Streaming Responses** - Real-time token-by-token output
- **Prompt Engineering** - System prompts and instruction formatting
- **Conversational Memory** - Context-aware multi-turn conversations
- **Model Switching** - Dynamic switching between Orca and Llama2 models
- **Web Interface** - Modern chat UI with Chainlit
- **LangChain Integration** - Advanced prompt templates and memory buffers

### Supported Models
- **Orca Mini 3B** - Fast, efficient 3 billion parameter model
- **Llama 2 7B** - More powerful 7 billion parameter model
- Both models use GGUF quantization for optimal performance

## 📁 Project Structure

```
llm_chatbot_gpt/
├── solutions/
│   ├── simple_completion.py          # Basic LLM inference
│   ├── stream_answer.py              # Streaming token output
│   ├── chat_prompt.py                # Prompt engineering basics
│   ├── conversational_memory.py      # CLI conversation with memory
│   ├── chainlit_hello_world.py       # Chainlit basics
│   ├── chainlit_stream.py            # Streaming in Chainlit
│   ├── chainlit_use_model.py         # LLM integration with Chainlit
│   ├── chainlit_conversational_memory.py  # Full chatbot with memory
│   ├── exercises/
│   │   ├── basic_prompting.py        # Prompt engineering exercises
│   │   ├── change_chatbots.py        # Multi-model chatbot
│   │   └── llama2.py                 # Llama2-specific implementation
│   └── langchain/
│       ├── langchain_demo.py         # LangChain basics
│       └── chainlit_with_langchain.py # Full LangChain + Chainlit app
├── .devcontainer/
│   └── devcontainer.json             # Development container config
├── requirements.txt                   # Python dependencies
├── .flake8                           # Linting configuration
├── .mypy.ini                         # Type checking configuration
├── .pylintrc                         # Code quality configuration
└── README.md                         # This file
```

## 🚀 Installation

### Prerequisites
- Python 3.10 or higher (Python 3.12 recommended)
- pip package manager
- 4GB+ RAM recommended
- 10GB+ disk space for models

### Setup Steps

1. **Clone the repository**
```bash
git clone https://github.com/naman-upreti/llm_chatbot_practice.git
cd llm_chatbot_practice
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

This will install:
- `ctransformers` - For running quantized LLM models
- `chainlit` - For building chat interfaces
- `langchain` & `langchain-community` - For advanced LLM orchestration
- `fastapi` & `uvicorn` - For web server functionality
- And all other required dependencies

3. **Verify installation**
```bash
python -m py_compile solutions/simple_completion.py
```

## 💻 Usage

### Basic Examples

#### 1. Simple Completion
```bash
python solutions/simple_completion.py
```
Demonstrates basic text completion with the Orca model.

#### 2. Streaming Response
```bash
python solutions/stream_answer.py
```
Shows real-time token streaming for better UX.

#### 3. Chat with Prompt Engineering
```bash
python solutions/chat_prompt.py
```
Implements system prompts for better responses.

#### 4. Conversational Memory (CLI)
```bash
python solutions/conversational_memory.py
```
Multi-turn conversation with context retention.

### Chainlit Web Applications

#### 5. Basic Chainlit App
```bash
chainlit run solutions/chainlit_hello_world.py
```
Simple "Hello World" chat interface.

#### 6. Streaming Chatbot
```bash
chainlit run solutions/chainlit_stream.py
```
Real-time streaming responses in web UI.

#### 7. Full Conversational Chatbot
```bash
chainlit run solutions/chainlit_conversational_memory.py
```
Complete chatbot with memory and streaming.

#### 8. Multi-Model Chatbot
```bash
chainlit run solutions/exercises/change_chatbots.py
```
Switch between Orca and Llama2 models on-the-fly.
- Type "use llama2" to switch to Llama2
- Type "use orca" to switch to Orca
- Type "forget everything" to clear conversation history

### LangChain Integration

#### 9. LangChain Demo
```bash
python solutions/langchain/langchain_demo.py
```
Demonstrates LangChain prompt templates and memory.

#### 10. LangChain + Chainlit
```bash
chainlit run solutions/langchain/chainlit_with_langchain.py
```
Full-featured chatbot with LangChain orchestration.

## 🛠️ Technologies Used

### Core Frameworks
- **[CTransformers](https://github.com/marella/ctransformers)** - Efficient inference for transformer models
- **[Chainlit](https://docs.chainlit.io/)** - Build production-ready chat applications
- **[LangChain](https://python.langchain.com/)** - Framework for LLM application development

### Models
- **[Orca Mini 3B GGUF](https://huggingface.co/zoltanctoth/orca_mini_3B-GGUF)** - Quantized 3B parameter model
- **[Llama 2 7B GGUF](https://huggingface.co/TheBloke/Llama-2-7b-Chat-GGUF)** - Quantized 7B parameter model

### Supporting Libraries
- **FastAPI** - Modern web framework
- **Uvicorn** - ASGI server
- **Pydantic** - Data validation
- **Python-dotenv** - Environment management

## 📚 Implementation Examples

### Example 1: Basic Prompt Engineering
```python
def get_prompt(instruction: str) -> str:
    system = "You are an AI assistant that gives helpful answers."
    prompt = f"### System:\n{system}\n\n### User:\n{instruction}\n\n### Response:\n"
    return prompt
```

### Example 2: Conversational Memory
```python
def get_prompt(instruction: str, history: list[str] | None = None) -> str:
    system = "You are an AI assistant that gives helpful answers."
    prompt = f"### System:\n{system}\n\n### User:\n"
    if history is not None and len(history) > 0:
        prompt += f"This is the conversation history: {''.join(history)}. "
    prompt += f"{instruction}\n\n### Response:\n"
    return prompt
```

### Example 3: Chainlit Integration
```python
@cl.on_message
async def on_message(message: cl.Message) -> None:
    message_history: list[str] = cl.user_session.get("message_history")
    msg = cl.Message(content="")
    await msg.send()
    
    prompt: str = get_prompt(message.content, message_history)
    answer: str = ""
    for word in llm(prompt, stream=True):
        await msg.stream_token(word)
        answer += word
    message_history.append(answer)
    await msg.update()
```

## ⚙️ Configuration

### Code Quality Tools
- **Black** - Code formatting (line length: 160)
- **Flake8** - Linting (ignores: E501, E402, F841, F401, E302, E305)
- **MyPy** - Type checking (minimal configuration)
- **Pylint** - Advanced code analysis

### VS Code Settings
The project includes `.vscode/settings.json` with:
- Auto-formatting on save
- Flake8 integration
- Black formatter configuration

### Development Container
Includes `.devcontainer/devcontainer.json` for:
- Python 3.11 environment
- Pre-installed dependencies
- VS Code extensions

## 📖 Resources

### Official Documentation
- **Chainlit**: https://docs.chainlit.io/get-started/overview
- **LangChain**: https://python.langchain.com/docs/get_started/introduction
- **CTransformers**: https://github.com/marella/ctransformers

### Model Resources
- **Orca Mini Model**: https://huggingface.co/zoltanctoth/orca_mini_3B-GGUF
- **Llama 2 Models**: https://huggingface.co/TheBloke/Llama-2-7b-Chat-GGUF
- **Open Orca Dataset**: https://huggingface.co/datasets/Open-Orca/OpenOrca

### Learning Resources
- **Hugging Face Hub**: https://huggingface.co/
- **GGUF Format**: Efficient quantized model format for local inference
- **Prompt Engineering Guide**: Best practices for LLM prompts

## 🎓 Course Information

This project is based on **"The Local LLM Crash Course - Build Your Own GPT in 2 hours"**
- Course Link: [Udemy Course](https://www.udemy.com/course/the-local-llm-crash-course-build-a-hugging-face-ai-chatbot/?referralCode=EAD6017AA0001257DD9A)
- GitHub Codespaces compatible
- Includes exercises and solutions

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## 📝 License

This project is for educational purposes. Please refer to individual model licenses for commercial use.

## 🔧 Troubleshooting

### Common Issues

**Model Download Fails**
- Ensure stable internet connection
- Models are downloaded automatically on first run
- Check available disk space (10GB+ recommended)

**Out of Memory**
- Use smaller models (Orca Mini 3B instead of Llama 2 7B)
- Reduce `max_new_tokens` parameter
- Close other applications

**Chainlit Not Starting**
- Verify installation: `pip show chainlit`
- Check port availability (default: 8000)
- Try: `chainlit run <script> --port 8080`

## 📧 Contact

For questions or support, please open an issue on GitHub.

---

**Built with ❤️ using Python, Chainlit, and LangChain**
