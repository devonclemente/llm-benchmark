# llm-benchmark

Benchmark local LLMs (via Ollama) and Claude side-by-side on your own tasks.

Runs the same prompts through every model and generates a readable markdown report so you can compare quality and speed at a glance. Built for practical ops tasks — summarization, priority extraction, message drafting, and structured data output.

---

## Background

Built as part of a real automation project — we used this to choose the model running a daily ops bot for a small business. The full story is in the article series on Medium:

- [Why I Don't Trust AI Models I Can't Run Offline](https://medium.com/@devonclemente/why-i-dont-trust-ai-models-i-cant-run-offline-59a49cfe11f3)
- [We Built a Daily Ops Bot for a Small Business on a $1000 Mac Mini](https://medium.com/@devonclemente/daily-ops-bot-small-business-mac-mini-893aa08a6868)
- [The 50-Line Python Script That Runs a Team Standup Every Morning](https://medium.com/@devonclemente/50-line-python-script-team-standup)
- [You wouldn't crack a walnut with a sledgehammer, would you?](https://medium.com/@devonclemente/local-vs-cloud-llm-benchmark-ops-data-be4e0f93b46e)

---

## What it does

Four task types, every model, same prompts:

| Task | What it tests |
|------|--------------|
| `summarize` | Condense a week of open items into a short digest |
| `priorities` | Extract the 3 most urgent items |
| `classify` | Return structured JSON from unstructured task data |
| `draft` | Write a short message based on context |

Output: a markdown report comparing every model side by side — response time, tokens/sec, and raw output.

---

## Requirements

- [Ollama](https://ollama.com) installed and running
- At least one model pulled: `ollama pull llama3.2`
- Python 3.8+
- Optional: [Claude CLI](https://claude.ai/code) for cloud comparison

---

## Quick start

```bash
# Pull a model
ollama pull llama3.2

# Run the benchmark
python3 llm-benchmark.py

# Local models only (no Claude)
python3 llm-benchmark.py --skip-claude

# Specific models and tasks
python3 llm-benchmark.py --models llama3.2 mistral --tasks summarize classify
```

---

## Customizing for your own tasks

Everything is in the `TASKS` dict near the top of the script. Swap in your own prompts, system instructions, and sample data:

```python
TASKS = {
    "your-task": {
        "description": "one line explaining what this tests",
        "system": "optional system prompt / persona",
        "prompt": "the actual prompt sent to every model",
    },
}
```

Update `SAMPLE_CONTEXT` with your own data — or load it from a file.

---

## CLI options

```
--models      Ollama model names to benchmark (must be pulled first)
--tasks       Which tasks to run (default: all)
--skip-claude Skip Claude CLI, run local models only
--output      Output report filename (default: benchmark-YYYY-MM-DD.md)
```

---

[devonclemente.com](https://devonclemente.com)
