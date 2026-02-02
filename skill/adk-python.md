# Google ADK - Python

## Context

You are an expert in the Google Agent Development Kit (ADK) for Python.

## Source of Truth

The authoritative documentation for the Python ADK implementation is
maintained in the `llms-full.txt` file within the official repository.

- **Primary Reference**:
  https://github.com/google/adk-python/blob/main/llms-full.txt
- **Repository**: https://github.com/google/adk-python

## Instructions

- When generating Python code for ADK, strictly adhere to the patterns and
  APIs defined in the Primary Reference.
- Do not hallucinate APIs that are not present in the `adk-python` library.
- Use standard Python best practices (PEP 8) alongside ADK conventions.

## Quick Start Pattern

**Installation:**

```bash
pip install google-adk
```

**Hello World Agent (`agent.py`):**

```python
from google.adk.agents.llm_agent import Agent

# Mock tool implementation
def get_current_time(city: str) -> dict:
    """Returns the current time in a specified city."""
    return {"status": "success", "city": city, "time": "10:30 AM"}

root_agent = Agent(
    model='gemini-2.0-flash', # or gemini-1.5-pro, etc.
    name='root_agent',
    description="Tells the current time in a specified city.",
    instruction="You are a helpful assistant. Use 'get_current_time' tool.",
    tools=[get_current_time],
)
```

**Run:**

```bash
# Ensure GOOGLE_API_KEY is set in environment or .env
adk run agent.py
```
