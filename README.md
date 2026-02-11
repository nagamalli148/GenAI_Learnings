# 🚀 GenAI Workshop: From LangChain to Intelligent Agents

## 6-Hour Comprehensive Bootcamp

Welcome to this hands-on workshop where we'll build an **AI-Powered Research Assistant** from scratch, progressively learning LangChain, LangSmith, LangGraph, and Hugging Face Transformers.

---

## 🎯 Problem Statement: AI Research Assistant

**What we're building:** An intelligent research assistant that can:
- Answer questions using LLMs
- Remember conversation context
- Search and analyze documents (RAG)
- Execute multi-step research tasks
- Self-correct and handle errors
- Run locally with open-source models

**Why this approach?** Instead of learning tools in isolation, we'll discover each technology by hitting limitations and solving them with the next tool.

---

## 📚 Workshop Journey

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        THE LEARNING PROGRESSION                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  😤 PROBLEM           →    💡 SOLUTION         →    🎉 OUTCOME              │
│                                                                              │
│  "I need to call      →    LangChain Basics    →    Easy LLM calls         │
│   LLMs easily"                                                               │
│         ↓                                                                    │
│  "I need multi-step   →    Chains              →    Sequential workflows   │
│   workflows"                                                                 │
│         ↓                                                                    │
│  "LLM forgets our     →    Memory              →    Context retention      │
│   conversation"                                                              │
│         ↓                                                                    │
│  "I need answers      →    RAG                 →    Document Q&A           │
│   from my docs"                                                              │
│         ↓                                                                    │
│  "I can't debug       →    LangSmith           →    Full observability     │
│   what went wrong"                                                           │
│         ↓                                                                    │
│  "I need complex      →    LangGraph           →    Stateful agents        │
│   agent workflows"                                                           │
│         ↓                                                                    │
│  "I want to run       →    HuggingFace         →    Local inference        │
│   models locally"                                                            │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## ⏰ Session Schedule (6 Hours)

| Session | Duration | Topic | File |
|---------|----------|-------|------|
| **1** | 60 min | LangChain Fundamentals | `01_langchain_basics.ipynb` |
| **2** | 50 min | Chains & Memory | `02_chains_and_memory.ipynb` |
| **☕ Break** | 10 min | - | - |
| **3** | 55 min | RAG - Document Q&A | `03_rag_implementation.ipynb` |
| **🍽️ Lunch** | 45 min | - | - |
| **4** | 45 min | LangSmith Observability | `04_langsmith_observability.ipynb` |
| **5** | 55 min | LangGraph & Agents | `05_langgraph_agents.ipynb` |
| **☕ Break** | 10 min | - | - |
| **6** | 45 min | HuggingFace & Transformers | `06_huggingface_transformers.ipynb` |
| **7** | 45 min | Final Project & Wrap-up | `07_complete_agent.ipynb` |

---

## 🛠️ Setup Instructions

### 1. Prerequisites
- Python 3.9+
- Ollama (for LOCAL models - no API key needed!)
- LangSmith Account (free tier, optional)

### 2. Install Ollama (2 minutes)

```bash
# Windows: Download from https://ollama.ai/download
# Mac: 
brew install ollama
# Linux:
curl -fsSL https://ollama.ai/install.sh | sh
```

Then pull TinyLlama (very small, runs on ANY computer):
```bash
ollama serve      # Start Ollama in one terminal
ollama pull qwen2:0.5b   # Pull the model (~600MB, runs on minimal hardware!)
```

### 3. Python Setup

```bash
# Clone or create workspace
cd GenAI_Workshop

# Create virtual environment
python -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Activate (Mac/Linux)
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt
```

### 4. Environment Setup (Optional)

Copy `.env.example` to `.env` if you want to use cloud APIs later:

```bash
cp .env.example .env
```

---

## 📖 Session Details

### Session 1: LangChain Fundamentals (60 min)

**The Problem:** Calling models directly is verbose and provider-specific.

```python
# Without LangChain - Verbose HTTP calls
import requests
response = requests.post("http://localhost:11434/api/generate", 
    json={"model": "tinyllama", "prompt": "Hello"})
print(response.json()["response"])
```

**The Solution:** LangChain provides a unified interface.

```python
# With LangChain - Clean and portable!
from langchain_ollama import ChatOllama
llm = ChatOllama(model="tinyllama")
response = llm.invoke("Hello")
print(response.content)
```

**What you'll learn:**
- ✅ Why LangChain exists and its architecture
- ✅ LLM vs ChatModel
- ✅ Prompt Templates
- ✅ Output Parsers
- ✅ LCEL (LangChain Expression Language)

**Key Concepts:**
- **Model I/O**: The foundation - prompts, models, output parsers
- **LCEL**: Pipe operator (`|`) for composing components
- **Runnables**: Everything is a Runnable with `.invoke()`, `.batch()`, `.stream()`

---

### Session 2: Chains & Memory (50 min)

**The Problem:** Single LLM calls aren't enough for complex tasks. And LLMs have no memory!

**What you'll learn:**
- ✅ What are Chains and why we need them
- ✅ Sequential Chains
- ✅ Conversation Memory types
- ✅ Building a chatbot that remembers

**Key Concepts:**
- **Chain**: Sequence of calls (LLM, tools, or other chains)
- **Memory**: Conversation Buffer, Summary, Window memory
- **History**: Managing chat history for context

---

### Session 3: RAG - Retrieval Augmented Generation (50 min)

**The Problem:** LLMs don't know about your private documents or recent events.

**What you'll learn:**
- ✅ What is RAG and why it's crucial
- ✅ Document Loaders
- ✅ Text Splitters
- ✅ Embeddings & Vector Stores
- ✅ Retrieval Chains

**Key Concepts:**
- **Embeddings**: Convert text to vectors for similarity search
- **Vector Store**: Database optimized for similarity search
- **Retriever**: Fetches relevant documents for a query

**RAG Pipeline:**
```
Documents → Split → Embed → Store → Query → Retrieve → Generate
```

---

### Session 4: LangSmith Observability (40 min)

**The Problem:** "It's not working and I don't know why!"

**What you'll learn:**
- ✅ Why observability matters in LLM apps
- ✅ Setting up LangSmith
- ✅ Tracing chains and agents
- ✅ Debugging failures
- ✅ Evaluating outputs

**Key Concepts:**
- **Traces**: Full execution path visibility
- **Runs**: Individual component executions
- **Feedback**: Collect human ratings
- **Datasets**: Test sets for evaluation

---

### Session 5: LangGraph & Agents (60 min)

**The Problem:** Chains are linear. Real-world tasks need loops, conditions, and state.

**What you'll learn:**
- ✅ Limitations of simple chains
- ✅ What is LangGraph
- ✅ Graph-based workflows
- ✅ State management
- ✅ Building a ReAct Agent

**Key Concepts:**
- **State**: Persistent data across nodes
- **Nodes**: Processing steps (functions)
- **Edges**: Connections (conditional or direct)
- **Graph**: The complete workflow

**Agent Loop:**
```
        ┌──────────────┐
        │    START     │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │   REASON     │◄────────┐
        │  (LLM call)  │         │
        └──────┬───────┘         │
               │                 │
               ▼                 │
        ┌──────────────┐         │
        │   DECIDE     │         │
        │ Tool or End? │         │
        └──────┬───────┘         │
               │                 │
       ┌───────┴───────┐         │
       │               │         │
       ▼               ▼         │
   ┌───────┐    ┌──────────┐     │
   │  END  │    │  ACTION  │─────┘
   │       │    │(use tool)│
   └───────┘    └──────────┘
```

---

### Session 6: HuggingFace & Transformers (50 min)

**The Problem:** API costs add up. You want local, private, open-source models.

**What you'll learn:**
- ✅ HuggingFace ecosystem overview
- ✅ Transformers library basics
- ✅ Loading and using models
- ✅ Pipelines for common tasks
- ✅ Integrating with LangChain

**Key Concepts:**
- **Transformers**: The neural network architecture
- **Tokenizers**: Convert text to numbers
- **Pipelines**: High-level API for common tasks
- **Models**: Pre-trained weights you can download

---

### Session 7: Complete Agent (30 min)

**Bringing it all together:**
- Multi-tool research agent
- Document + web search
- Memory persistence
- Observable with LangSmith
- Option for local models

---

## 🏗️ Project Structure

```
GenAI_Workshop/
├── README.md                         # This file (student guide)
├── INSTRUCTOR_GUIDE.md               # Session delivery plan
├── requirements.txt                  # Dependencies
├── .env.example                      # Environment template
│
├── 01_langchain_basics.ipynb         # Session 1: LangChain Fundamentals
├── 02_chains_and_memory.ipynb        # Session 2: Chains & Memory
├── 03_rag_implementation.ipynb       # Session 3: RAG
├── 04_langsmith_observability.ipynb  # Session 4: LangSmith
├── 05_langgraph_agents.ipynb         # Session 5: LangGraph & Agents
├── 06_huggingface_transformers.ipynb # Session 6: HuggingFace
├── 07_complete_agent.ipynb           # Session 7: Complete Agent
│
└── data/                             # Sample documents for RAG
    └── sample_docs/
```

---

## 🆓 FREE API - Google Gemini

This workshop uses **Gemma 3 27B via Google's Gemini API** which is **completely FREE!**

- No credit card required
- Generous free tier
- State-of-the-art open model
- Get your key at: https://aistudio.google.com

---

## 🔑 Key Takeaways

By the end of this workshop, you will:

1. **Understand the LLM application stack** - From raw API calls to production agents
2. **Know when to use what** - LangChain vs LangGraph vs raw Transformers
3. **Build production-ready apps** - With proper observability and debugging
4. **Run models locally** - Reduce costs and increase privacy
5. **Have working code** - Reference implementations for all concepts

---

## 📚 Resources

### Documentation
- [LangChain Docs](https://python.langchain.com/docs/)
- [LangSmith Docs](https://docs.smith.langchain.com/)
- [LangGraph Docs](https://langchain-ai.github.io/langgraph/)
- [HuggingFace Docs](https://huggingface.co/docs)

### Community
- [LangChain Discord](https://discord.gg/langchain)
- [HuggingFace Forums](https://discuss.huggingface.co/)

---

## ❓ FAQ

**Q: Do I need a GPU?**
A: No, but it helps for Session 6 (HuggingFace). We'll use small models or CPU-friendly options.

**Q: Is the Google Gemini API really free?**
A: Yes! Google provides a generous free tier. Get your key at https://aistudio.google.com

**Q: Can I use OpenAI or Azure OpenAI instead?**
A: Yes! LangChain supports multiple providers. Just install `langchain-openai` and update the imports.

**Q: What if I don't have API keys?**
A: You can follow along with the instructor. The Gemini API is free and easy to set up!

**Q: Will the code work after the workshop?**
A: Yes! All code is self-contained and documented.

**Q: Why Jupyter notebooks?**
A: Notebooks make it easy to learn interactively - run cells one by one and see results immediately!

---

## 🤝 Let's Build!

Ready to start? Open `01_langchain_basics.ipynb` and let's begin our journey!

---

*Workshop created with ❤️ for learning GenAI development*
*Using FREE Gemma 3 27B via Google Gemini API*
