# Page Assist — Local AI Browser Assistant

[Page Assist](https://github.com/n4ze3m/page-assist?utm_source=chatgpt.com) is an open-source browser extension that provides a **sidebar and web UI for local AI models**. It is particularly useful with **Ollama**, allowing you to interact with your local LLM directly while browsing.

> **Main idea:** Ollama runs the AI model; Page Assist provides the browser interface and context.

---

# 1. Architecture

```text
┌──────────────────────────┐
│        Browser           │
│   Chrome / Firefox       │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│       Page Assist        │
│                          │
│  Sidebar / Web UI        │
│  Webpage context         │
│  PDF / Documents         │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│         Ollama           │
│    localhost:11434       │
└────────────┬─────────────┘
             │
       ┌─────┼─────┐
       ▼     ▼     ▼
     Qwen   Gemma  Phi
```

---

# 2. Installation

The easiest approach is to install the browser extension from the official browser extension store.

Page Assist supports Chromium-based browsers such as **Chrome, Brave, Edge and Vivaldi**, as well as Firefox.

For Chrome:

[Install Page Assist from Chrome Web Store](https://chromewebstore.google.com/detail/page-assist-a-web-ui-for/jfgfiigpkhlkbnfnbobbkinehhfdhndo?utm_source=chatgpt.com)

For Firefox:

[Install Page Assist from Firefox Add-ons](https://addons.mozilla.org/en-US/firefox/addon/page-assist/?utm_source=chatgpt.com)

---

# 3. Prerequisite: Ollama

Install and run Ollama first:

```bash
ollama --version
```

Start Ollama:

```bash
ollama serve
```

Check your models:

```bash
ollama list
```

Example:

```text
NAME                    SIZE
dolphin-phi:latest      1.6 GB
gemma3:4b               3.3 GB
qwen2.5-coder:3b        1.9 GB
phi4-mini:latest        2.5 GB
qwen2.5-coder:7b        4.7 GB
```

Page Assist can use Ollama as its local AI provider.

---

# 4. Main Features

### 🌐 Chat With Webpages

Open any webpage and ask questions about its content.

```text
Webpage
   ↓
Page Assist
   ↓
Ollama
   ↓
Answer
```

Useful for:

```text
Summarization
Explanation
Research
Extracting information
Understanding documentation
Comparing information
```

---

### 📑 Chat With Documents

Page Assist can work with documents including:

```text
PDF
CSV
TXT
Markdown
DOCX
```

This is particularly useful for local document analysis.

Example:

```text
PDF
 ↓
Page Assist
 ↓
Ollama
 ↓
"Summarize this document"
```

---

### 🖥️ Sidebar

Page Assist provides a browser sidebar so you can interact with your local AI while staying on the current webpage.

Useful for:

```text
Documentation
Stack Overflow
GitHub
Technical articles
Research papers
News
Tutorials
```

---

### 💬 Web UI

Page Assist also provides a ChatGPT-like web interface for interacting with local models.

```text
Browser
   ↓
Page Assist Web UI
   ↓
Ollama
   ↓
Local LLM
```

---

# 5. Current Features

Depending on the current Page Assist version, available features include:

```text
✓ Sidebar
✓ Local AI models
✓ Chat with webpages
✓ Vision models
✓ Internet search
✓ Chat with PDF
✓ Chat with documents
✓ Tab mention
✓ MCP client support (beta)
✓ Memory support (beta)
✓ Web UI
```

Supported providers include **Ollama**, Chrome AI (beta), and OpenAI-compatible APIs such as LM Studio, Llama.cpp, Llamafile and vLLM.

---

# 6. Recommended Models

Using the models from your Ollama setup:

| Model              | Page Assist use                      |
| ------------------ | ------------------------------------ |
| `gemma3:4b`        | General webpage/document questions   |
| `phi4-mini`        | Lightweight general conversations    |
| `qwen2.5-coder:3b` | Lightweight coding/documentation     |
| `qwen2.5-coder:7b` | **Coding + technical documentation** |
| `dolphin-phi`      | Lightweight experimentation          |

For your developer workflow:

```text
Page Assist
     │
     └── Ollama
          │
          └── qwen2.5-coder:7b
```

Use a smaller model when you need lower memory usage or faster responses.

---

# 7. Useful Workflow for Developers

### Read documentation

```text
Angular documentation
        ↓
Page Assist
        ↓
"Explain this API"
        ↓
Ollama
        ↓
Answer
```

### Understand GitHub repositories

```text
GitHub repository
        ↓
Page Assist
        ↓
Ask about architecture / code
        ↓
Ollama
```

### Research a technology

```text
Multiple webpages
        ↓
Page Assist
        ↓
Summarize / compare
        ↓
Local model
```

### Analyze a PDF

```text
Technical PDF
        ↓
Page Assist
        ↓
Ollama
        ↓
Summary / questions / extraction
```

---

# 8. Page Assist + Ollama + Your Development Stack

A useful local AI environment:

```text
                 LOCAL DEVELOPMENT
                        │
        ┌───────────────┴────────────────┐
        │                                │
     Browser                         Terminal
        │                                │
        ▼                                ▼
  Page Assist                       Claude Code
        │                                │
        └───────────────┬────────────────┘
                        ▼
                     Ollama
                        │
              ┌─────────┼─────────┐
              ▼         ▼         ▼
            Gemma      Qwen       Phi
                        │
                        ▼
             Spring Boot / Angular
             Laravel / Docker / SQL
```

### Roles

```text
Ollama
→ Local AI runtime

Page Assist
→ Browser AI interface

Claude Code
→ Coding-agent interface

Qwen Coder
→ Local coding model
```

This gives you different interfaces over the same local AI infrastructure.

---

# 9. Privacy

Page Assist states that it does not collect personal data and that its data is stored locally in browser storage; its privacy documentation also describes the share feature separately.

However, **local AI does not automatically mean every webpage is private**.

Be careful when using:

```text
Confidential documents
Passwords
Credentials
Internal URLs
Personal information
Sensitive work information
```

Also remember that enabling features such as internet search or sharing can introduce external network communication.

---

# 10. Manual Installation / Development

For developers who want to modify Page Assist:

```bash
git clone https://github.com/n4ze3m/page-assist.git

cd page-assist

bun install

bun run build
```

The project can also use npm if Bun is not available.

For development:

```bash
bun dev
```

Then load the generated extension through the browser's extension management page.

Chrome:

```text
chrome://extensions
```

Enable:

```text
Developer mode
      ↓
Load unpacked
      ↓
build/
```

---

# 11. Useful Shortcuts

Page Assist provides keyboard shortcuts for its sidebar and Web UI. The exact shortcuts can be changed through the browser's extension settings.

Typical actions include:

```text
Open Sidebar
Open Web UI
New Chat
Toggle Sidebar
Focus input
Toggle Chat / Page mode
```

---

# 12. Best Use Cases

### 👨‍💻 Development

```text
Read documentation
Explain code
Understand GitHub projects
Analyze technical articles
Generate examples
Debug concepts
```

### 📚 Learning

```text
Study tutorials
Summarize courses
Ask questions about articles
Explain difficult concepts
```

### 📄 Documents

```text
PDF analysis
Report summarization
CSV analysis
DOCX/TXT/Markdown analysis
```

### 🔒 Local AI

```text
Local models
Private experiments
Offline-oriented workflows
Local document analysis
AI learning
```

### 🔎 Research

```text
Web research
Page summarization
Information extraction
Technical research
Cross-page investigation
```

---

# 13. Page Assist vs Ollama

They are **not alternatives**.

| Tool            | Role                               |
| --------------- | ---------------------------------- |
| **Ollama**      | Runs the AI models                 |
| **Page Assist** | Browser interface for those models |
| **Claude Code** | Coding-agent interface             |
| **Qwen Coder**  | Coding model                       |
| **Gemma**       | General-purpose model              |

Think of it as:

```text
              INTERFACES
          ┌───────┴────────┐
          ▼                ▼
    Page Assist        Claude Code
          │                │
          └───────┬────────┘
                  ▼
               Ollama
                  │
           ┌──────┼──────┐
           ▼      ▼      ▼
         Qwen   Gemma   Phi
```

---

# 14. Quick Cheat Sheet

```bash
# Start Ollama
ollama serve

# List models
ollama list

# Run model
ollama run qwen2.5-coder:7b

# Check running models
ollama ps

# Page Assist
# Install browser extension
# Configure Ollama as provider
# Select your model
# Open sidebar
# Ask questions about the current page
```

---

# 15. In One Sentence

> **Page Assist is the browser interface that lets you bring your local AI into your everyday web browsing, while Ollama provides the local models underneath.**

### Recommended setup

```text
Ollama
   +
Page Assist
   +
qwen2.5-coder:7b
   +
Chrome / Firefox
```

For your development workflow, this gives you a simple **local AI research + coding + documentation environment** without needing a separate cloud AI interface for every task.
