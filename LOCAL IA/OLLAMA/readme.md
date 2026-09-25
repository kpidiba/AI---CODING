# Ollama — Local AI Development

[Ollama](https://ollama.com/?utm_source=chatgpt.com) lets you run open AI models locally and expose them through a CLI and API. It is useful for **private AI experiments, coding assistance, document processing, automation and local development**.

> **Main idea:** run AI models on your own machine instead of depending entirely on external APIs.

---

## 1. Installation

### Linux

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

[Linux installation](https://ollama.com/download/linux?utm_source=chatgpt.com)

Check installation:

```bash
ollama --version
```

Start the server if necessary:

```bash
ollama serve
```

---

# 2. Essential Ollama CLI

### List installed models

```bash
ollama list
```

Example:

```text
NAME                    ID              SIZE
dolphin-phi:latest      c5761fc77240    1.6 GB
gemma3:4b               a2af6cc3eb7f    3.3 GB
qwen2.5-coder:3b        f72c60cabf62    1.9 GB
phi4-mini:latest        78fad5d182a7    2.5 GB
qwen2.5-coder:7b        dae161e27b0e    4.7 GB
```

### Download a model

```bash
ollama pull <model>
```

Example:

```bash
ollama pull qwen2.5-coder:7b
```

### Run a model

```bash
ollama run <model>
```

Example:

```bash
ollama run qwen2.5-coder:7b
```

`ollama run` will also download the model if it isn't already installed.

### Show model information

```bash
ollama show <model>
```

### Remove a model

```bash
ollama rm <model>
```

### Copy/create model variants

```bash
ollama cp <source> <destination>
```

### See running models

```bash
ollama ps
```

### Stop a running model

```bash
ollama stop <model>
```

---

# 3. Docker

Ollama also provides an official Docker image.

### CPU

```bash
docker run -d \
  -v ollama:/root/.ollama \
  -p 11434:11434 \
  --name ollama \
  ollama/ollama
```

### NVIDIA GPU

```bash
docker run -d \
  --gpus=all \
  -v ollama:/root/.ollama \
  -p 11434:11434 \
  --name ollama \
  ollama/ollama
```

Run a model inside the container:

```bash
docker exec -it ollama ollama run qwen2.5-coder:7b
```

### Useful Docker commands

```bash
docker ps
docker ps -a
docker start ollama
docker stop ollama
docker restart ollama
docker logs ollama
docker exec -it ollama bash
docker rm ollama
```

---

# 4. My Installed Models

| Model              | Size                         | **⭐ Meilleur usage**                          | Best use                                                                                                                                                                                                                       |
| ------------------ | ---------------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `qwen2.5-coder:7b` | 4.7 GB                       | ⭐⭐⭐⭐⭐ Assistant de développement principal    | **Ton modèle principal pour développer, corriger du code, expliquer une erreur, créer des composants, API, SQL, tests, etc. Qwen2.5-Coder est spécifiquement entraîné pour le code et supporte un contexte jusqu'à 128K.**     |
| `qwen2.5-coder:3b` | 1.9 GB                       | ⭐⭐⭐⭐ Codage rapide                            | À utiliser quand tu veux une réponse rapide et que la tâche n'est pas complexe : petites fonctions, HTML/CSS, petits composants Angular/React, commandes, regex, etc.                                                          |
| `gemma3:4b`        | 3.3 GB                       | ⭐⭐⭐⭐ Assistant général + images               | Plus adapté que Qwen Coder pour discuter, résumer, expliquer un concept, analyser du texte et certaines tâches multimodales. Gemma 3 apporte notamment la compréhension d'images et un long contexte.                          |
| `phi4-mini`        | 2.5 GB                       | ⭐⭐⭐⭐ Questions générales / raisonnement léger | Bon petit modèle pour les questions générales, explications techniques, raisonnement simple et tâches où tu ne veux pas charger un 7B.                                                                                         |
| `dolphin-phi`      | 1.6 GB                       | ⭐⭐ Expérimentation / tâches très légères      |                                                                                                                                                                                                                                |
| StarCoder2:7B      | ~4–5 GB selon quantification | ⭐⭐⭐⭐ Complétion de code                       | Très intéressant pour la génération/complétion de code, notamment le Fill-in-the-Middle : compléter du code au milieu d'un fichier. Mais il est conçu comme modèle de code plutôt que comme assistant conversationnel général. |

### Quick selection

```text
Coding                → qwen2.5-coder:7b
Fast/light coding     → qwen2.5-coder:3b
General AI             → gemma3:4b
Lightweight AI         → phi4-mini
Experimentation        → dolphin-phi
```

**Important:** model quality depends heavily on the task, model version, context length and available RAM/VRAM. The table above is a practical role assignment, not a benchmark ranking.

---

# 5. Ollama + Claude Code

Ollama can be used with coding agents such as **Claude Code, Codex and OpenCode**. Current Ollama versions provide the `ollama launch` command for setting up these integrations.

### Claude Code

```bash
ollama launch claude
```

Or select a specific model:

```bash
ollama launch claude --model <model>
```

For example:

```bash
ollama launch claude --model qwen2.5-coder:7b
```

This allows the coding agent to use a local Ollama model rather than requiring every coding request to go through an external model provider.

For coding agents, Ollama recommends using models with sufficiently large context windows; its current guidance recommends **at least 64K context** for coding-agent workloads when the selected model supports it.

---

# 6. Ollama API

Ollama exposes a local API, normally available at:

```text
http://localhost:11434
```

Example:

```bash
curl http://localhost:11434/api/chat \
  -d '{
    "model": "qwen2.5-coder:7b",
    "messages": [
      {
        "role": "user",
        "content": "Explain this Spring Boot controller."
      }
    ],
    "stream": false
  }'
```

This makes Ollama useful as a **local AI backend** for:

- Spring Boot

- Angular

- Laravel

- Python

- Node.js

- CLI tools

- internal applications

- automation

Ollama also provides Python and JavaScript libraries for interacting with the API.

---

# 7. Best Use Cases

### 👨‍💻 Software Development

Use local models for:

```text
Code generation
Code explanation
Refactoring
Debugging
Unit tests
Documentation
SQL queries
API development
Architecture brainstorming
```

Particularly useful:

```text
qwen2.5-coder
       ↓
Spring Boot / Angular / Laravel / SQL / Docker
```

---

### 🔒 Private / Confidential AI

Ollama is especially interesting when information should remain on your machine.

Examples:

```text
Internal documents
Source code
Private projects
Local experiments
Confidential text
```

Ollama describes locally run models as staying on the local machine rather than being sent to an external provider.

---

### 📄 Documents

Ollama can be used as the AI engine behind applications that process:

```text
PDF
TXT
DOCX
Markdown
Code
Reports
```

For example:

```text
PDF
 ↓
Text extraction
 ↓
Ollama
 ↓
Summarization / classification / extraction
 ↓
Database / Excel / application
```

---

### 🤖 AI Agents

Ollama can act as the local model layer for:

```text
Claude Code
OpenCode
Codex
Personal assistants
Automation
Tool-calling agents
```

Current Ollama integrations include several coding-agent tools, and supported models can expose tool-calling capabilities.

---

### 🧪 AI Learning & Experimentation

Ollama is excellent for learning:

```text
LLMs
Prompt engineering
RAG
Embeddings
Agents
Tool calling
Local AI
AI APIs
Model evaluation
```

without having to pay for every experiment through an external API.

---

# 8. Recommended Local Architecture

For development projects:

```text
                 ┌─────────────────┐
                 │ Angular / React │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │   Spring Boot  │
                 │    / Laravel   │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │     Ollama      │
                 │ localhost:11434 │
                 └────────┬────────┘
                          │
             ┌────────────┼────────────┐
             ▼            ▼            ▼
          Gemma        Qwen Coder    Phi
```

This gives you a **local AI service** that your applications can consume through HTTP.

---

# 9. Useful Command Cheat Sheet

```bash
# Installation
ollama --version

# Server
ollama serve

# Models
ollama list
ollama pull <model>
ollama run <model>
ollama show <model>
ollama rm <model>
ollama ps
ollama stop <model>

# Docker
docker ps
docker ps -a
docker start ollama
docker stop ollama
docker restart ollama
docker logs ollama
docker exec -it ollama ollama list

# Claude Code
ollama launch claude
ollama launch claude --model <model>

# API
curl http://localhost:11434/api/chat
```

---

## 10. In One Sentence

> **Ollama = a local AI runtime that lets you download, run and integrate open models into your development workflow, applications and coding agents.**

**For a developer:**  
`Ollama + Qwen Coder + Docker + Spring Boot/Angular/Laravel + Claude Code` is a practical foundation for experimenting with **local AI-assisted development**.

## CONFIGURATION FILE

```yaml
name: Main Config
version: 1.0.0
schema: v1
models:
  - name: Qwen
    provider: Ollama
    model: qwen2.5-coder:7b
    apiBase: http://192.168.0.39:11434
    roles:
      - chat
      - edit
      - apply
  - name: Autodetect
    provider: ollama
    model: AUTODETECT
    roles:
      - chat
      - edit
      - apply
      - autocomplete
```
