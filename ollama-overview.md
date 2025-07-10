# 🧠 Running Local LLMs with Ollama

This guide shows how to set up and run local large language models (LLMs) using [Ollama](https://ollama.com/), a simple tool for running models on your own machine — **no internet, no API keys, no data leakage**.

If you're a cybersecurity analyst, this gives you full control over your prompts, results, and files — a must for sensitive environments.

---

## 🚀 What is Ollama?

**Ollama** is a lightweight desktop and command-line interface (CLI) tool that lets you run LLMs (like LLaMA 3, Mistral, and Code LLaMA) directly on your machine. It supports:
- **Offline querying** after the model is downloaded
- Easy model switching with `ollama run`
- Integration with tools like LM Studio, Jupyter, VS Code, or APIs

---

## 💻 System Requirements

Minimum recommended specs:
- **CPU**: Intel i5/i7 or AMD equivalent (can run on CPU)
- **RAM**: 8–16 GB (more = better for larger models)
- **Disk**: 5–10 GB free (models are large)
- **OS**: Windows 10/11, macOS, or most Linux distros

GPU support (for faster inference) is available on Mac and Linux with Apple Silicon or CUDA support.

---

## 📦 Installation

### 🔹 macOS

```bash
brew install ollama
```

### 🔹 Windows
1. Download installer from [ollama.com](https://ollama.com/download)
2. Follow the setup wizard
3. Optionally install via Github [Winget](https://github.com/ollama/ollama#winget)

### 🔹 Linux
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

---
## 📥 Downloading a Model
Ollama uses simple names to pull models.

```bash
ollama run mistral
```
That will:

- Download the mistral model (7B) from the Ollama model registry

- Start an interactive prompt

Other models you might want:

- llama3 — Meta's 8B or 70B model

- codellama — For Python, Bash, and scripting

- gemma — Google’s open-source LLM

Full list: [https://ollama.com/library](https://ollama.com/library)

---

## 💬 Running the Model
Once downloaded, you can start the prompt:
```bash
ollama run mistral
```
You will then see:
```text
> What would you like to do today?
```
You can now type in questions, promopts, and start conversations.
---

## 🔒 Why Use This for Cybersecurity?
Unlike ChatGPT or web LLMs, local models **don’t send your prompts or results anywhere**. That makes Ollama great for:

- Writing draft KQL or Python scripts based on sensitive data
- Exploring logs and IOCs without exposing them online
- Asking for summaries of triage notes, alerts, or tickets
- Using LLMs offline in isolated lab environments
---

## 🧪 Example Prompts for Analysts
```text
You are a cybersecurity analyst. I will paste a detection alert, and you will help me summarize it in 3 bullet points.

Input: "Multiple failed logon attempts detected on WIN-HOST-21 from IP 192.168.100.45 using user 'admin'."
```
```text
Generate a KQL query to find Event ID 4625 (failed logon) grouped by Account and sorted by count.
```
```text
Here is a CSV of firewall logs. What patterns should I check for possible scanning behavior?
```
---

## 🛑 Notes & Limitations
- These models are not trained for security — they may hallucinate technical details
- Use smaller prompts for better results (7B models have limited memory)
- Always verify LLM-generated queries or code
- Don't copy raw output into production environments without review
---

## ✅ Summary
Ollama makes it easy for analysts to explore LLMs in private, secure ways.
You can use this to:

- Prototype ideas
- Speed up investigations
- Learn through guided experimentation
- Avoid sending information to external LLMs
