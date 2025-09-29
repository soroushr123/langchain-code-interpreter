# LangChain Multi-Agent System

A Python-based multi-agent system built with LangChain that demonstrates agent orchestration, featuring a grand router agent that delegates tasks to specialized sub-agents for Python code execution and CSV data analysis.

## Overview

This project showcases a hierarchical agent architecture where a main "grand agent" intelligently routes queries to either a Python execution agent or a CSV analysis agent based on the nature of the question. The system is designed to answer questions by executing Python code or analyzing CSV data.

## Features

- **Python Agent**: Executes Python code to answer natural language questions
- **CSV Agent**: Analyzes CSV files using pandas operations
- **Grand Router Agent**: Intelligently delegates tasks to the appropriate specialized agent
- **ReAct Pattern**: Uses the Reasoning and Acting pattern for agent decision-making
- **Verbose Logging**: Detailed execution logs for debugging and understanding agent behavior

## Tech Stack

- **Python 3.x**
- **LangChain**: Framework for building LLM-powered applications
- **OpenAI GPT-4 Turbo**: Language model for agent reasoning
- **LangChain Experimental**: Advanced agent toolkits
- **python-dotenv**: Environment variable management

## Project Structure

```
.
├── main.py                 # Main application file
├── episode_info.csv        # Sample CSV data file
├── .env                    # Environment variables (not tracked)
└── README.md              # This file
```

## Prerequisites

- Python 3.8 or higher
- OpenAI API key
- Required Python packages (see Installation)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd <repository-name>
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install langchain langchain-openai langchain-experimental python-dotenv
```

4. Create a `.env` file in the project root:
```
OPENAI_API_KEY=your_openai_api_key_here
```

## Usage

Run the main script:
```bash
python main.py
```

### Example Queries

The grand agent can handle various types of questions:

**CSV Analysis:**
```python
"which season has the most episodes?"
"print the seasons by ascending order of the number of episodes they have"
```

**Python Execution:**
```python
"generate and save 15 QR codes that point to www.udemy.com"
"calculate the fibonacci sequence up to 100"
```

## How It Works

### 1. Python Agent
- Uses `PythonAstREPLTool` to execute Python code safely
- Converts natural language questions into executable Python code
- Returns results after code execution

### 2. CSV Agent
- Built with `create_csv_agent` for pandas-based data analysis
- Analyzes the `episode_info.csv` file
- Performs data queries and calculations

### 3. Grand Router Agent
- Top-level agent that receives user queries
- Determines which specialized agent to use
- Routes the question to the appropriate sub-agent
- Returns the final answer

## Configuration

### Agent Settings

- **Temperature**: Set to 0 for deterministic responses
- **Model**: Uses GPT-4 Turbo for all agents
- **Verbose Mode**: Enabled for detailed logging

### Safety Note

The CSV agent uses `allow_dangerous_code=True` which allows execution of arbitrary Python code. Only use this with trusted data sources in controlled environments.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

[Specify your license here]

## Acknowledgments

- Built with [LangChain](https://github.com/langchain-ai/langchain)
- Powered by OpenAI's GPT-4 Turbo
