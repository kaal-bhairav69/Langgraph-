# LangGraph Multi-Agent Regulatory Intelligence System

A **multi-agent AI system** built with LangGraph that monitors regulatory sources (SEC, RBI, SEBI, IRS) and provides automated financial analysis and compliance intelligence.

## ⚡ Quick Start

### 1. Install Dependencies
```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 2. Configure Environment
```bash
cp .env.example .env
# Edit .env and add your API keys
```

### 3. Run
```python
import asyncio
from graph import build_graph

async def main():
    graph = build_graph()
    state = {
        "user_query": "What are latest SEC regulations?",
        "filters": {},
        "client_impact_results": {},
        "monitoring_results": {},
        "analysis_results": {},
        "briefing": "",
        "run_client_analysis": False,
        "run_briefing": True
    }
    result = await graph.ainvoke(state)
    print(result["briefing"])

asyncio.run(main())
```

## 🤖 System Components

### Agents
- **Router Agent** - Routes queries to appropriate agents
- **Monitoring Agent** - Fetches latest documents from regulatory sources
- **Analysis Agent** - Analyzes and summarizes documents
- **Briefing Agent** - Generates executive summaries
- **Client Impact Agent** - Assesses impact on client portfolios

### Data Sources
- **SEC** - US Securities regulations
- **RBI** - Indian Banking regulations
- **SEBI** - Indian Market regulations
- **IRS** - US Tax regulations

## 📁 Project Structure

```
├── graph.py                    # Main workflow orchestration
├── extractor.py               # PDF extraction
├── webcrawl.py                # Web crawling
├── summarise.py               # AI summarization
├── sec.py                     # SEC connector
│
├── agents/                    # Agent implementations
│   ├── router_agent.py
│   ├── analysis_agent.py
│   ├── briefing_agent.py
│   ├── client_impact_agent.py
│   └── monitoring_agent.py
│
├── sources/                   # Regulatory source connectors
│   ├── sec_2.py
│   ├── rbi.py
│   ├── sebi.py
│   ├── irs.py
│   └── income_tax.py
│
├── clients/data.json          # Client configuration
├── requirements.txt           # Dependencies
└── .env.example               # Environment template
```

## 🔧 Configuration

Create `.env` file:
```env
GROQ_API_KEY=your_groq_api_key_here
OPENAI_API_KEY=your_openai_api_key_here
DEBUG=True
LOG_LEVEL=INFO
```

## 📊 Workflow

```
User Query
    ↓
Router Agent (classify query)
    ↓
Monitoring Agent (fetch documents)
    ↓
Analysis Agent (analyze & summarize)
    ↓
Briefing Agent (generate brief)
    ↓
Client Impact Agent (optional)
    ↓
Output
```

## 🚀 Features

- ✅ Multi-agent orchestration with LangGraph
- ✅ Autonomous document fetching & analysis
- ✅ Real-time regulatory monitoring
- ✅ AI-powered summarization
- ✅ Client portfolio impact analysis
- ✅ Async processing
- ✅ State management

## 📚 Usage Examples

### Example 1: Monitor SEC
```python
state["user_query"] = "Latest SEC regulations for financial institutions"
result = await graph.ainvoke(state)
```

### Example 2: RBI Analysis
```python
state["user_query"] = "RBI guidelines for Indian banks"
result = await graph.ainvoke(state)
```

### Example 3: Client Impact
```python
state["user_query"] = "How do new SEBI rules impact fintech clients?"
state["run_client_analysis"] = True
result = await graph.ainvoke(state)
```

## 🛠️ Requirements

- Python 3.8+
- Groq API key (free tier available)
- OpenAI API key (optional)

## 📦 Dependencies

- **langgraph** - Graph orchestration
- **langchain** - LLM framework
- **phi** - Agent framework
- **groq** - LLM provider
- **pypdf** - PDF processing
- **crawl4ai** - Web crawling

See `requirements.txt` for full list.

## 🔐 Security

- Store API keys in `.env` (never commit)
- Use environment variables for all secrets
- Review `.gitignore` for excluded files

## 🐛 Troubleshooting

**ModuleNotFoundError**
```bash
pip install -r requirements.txt
```

**API Key Error**
```bash
# Check .env has your API key
echo $GROQ_API_KEY
```

**PDF Extraction Fails**
```bash
pip install pypdf --upgrade
```

## 📖 Learn More

- [LangGraph Docs](https://python.langchain.com/docs/langgraph/)
- [Groq API](https://www.groq.com/)
- [Python Async](https://docs.python.org/3/library/asyncio.html)

## 📝 License

MIT License

## 🤝 Contributing

Feel free to fork, modify, and contribute improvements!

---

**Status**: Production Ready ✅
