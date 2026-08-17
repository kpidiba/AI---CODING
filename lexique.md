# EADME – AI Developer Glossary (Simple Explanations)

---

# 🤖 AI Developer Glossary

This document explains the most common Artificial Intelligence (AI) terms every software developer should know.

The goal is **not to become an AI researcher**, but to understand how modern AI applications like ChatGPT, Claude, Gemini, GitHub Copilot, Cursor, Windsurf, or AI Agents work.

---

# Table of Contents

1. What is AI?
2. Machine Learning
3. Deep Learning
4. Neural Network
5. LLM (Large Language Model)
6. Prompt
7. Prompt Engineering
8. Context Window
9. Token
10. Embeddings
11. Vector Database
12. RAG
13. Fine-Tuning
14. AI Agent
15. Agentic AI
16. Workflow
17. Tool Calling
18. Function Calling
19. MCP Server
20. Memory
21. Multi-Agent Systems
22. Model
23. Inference
24. Training
25. Hallucination
26. Temperature
27. API
28. Local AI
29. Open Source Models
30. GPU
31. AI IDEs
32. Typical AI Application Architecture
33. Summary

---

# 1. What is AI?

Artificial Intelligence is software capable of performing tasks that usually require human intelligence.

Examples:

- Understanding text
- Writing code
- Recognizing images
- Translating languages
- Answering questions
- Driving a car

Examples of AI:

- ChatGPT
- Claude
- Gemini
- GitHub Copilot

---

# 2. Machine Learning (ML)

Machine Learning is a branch of AI where computers **learn patterns from data instead of being explicitly programmed**.

Example:

Instead of writing:

```
IF email contains "Prize"THEN Spam
```

You give the computer **millions of emails**, and it learns what spam looks like.

---

# 3. Deep Learning

Deep Learning is a more advanced type of Machine Learning that uses **large neural networks**.

It powers:

- ChatGPT
- Image generation
- Speech recognition
- Face recognition

---

# 4. Neural Network

Imagine a simplified version of the human brain.

It consists of many connected "neurons" that learn patterns.

Input

↓

Hidden Layers

↓

Output

Example:

Image

↓

Neural Network

↓

Cat

---

# 5. LLM (Large Language Model)

LLM = **Large Language Model**

This is the "brain" behind ChatGPT.

An LLM has read billions of words and learned how language works.

It predicts the next most likely word.

Example:

You type:

> The sky is...

The model predicts:

> blue

Then:

> because...

and continues.

Examples of LLMs:

- OpenAI GPT-5.5
- Anthropic Claude
- Google Gemini
- Meta Llama
- Mistral AI Mistral

Think of an LLM as:

> A super-intelligent autocomplete.

---

# 6. Prompt

A prompt is simply what you ask the AI.

Example:

```
Write a Java API.
```

or

```
Translate this text.
```

Good prompts produce better results.

---

# 7. Prompt Engineering

Prompt Engineering is the art of writing prompts that produce high-quality answers.

Bad prompt:

```
Create an app.
```

Good prompt:

```
Create a Spring Boot REST APIusing Java 21,JWT,PostgreSQL,Clean Architecture,Docker,Swagger.
```

The more context you provide, the better the result.

---

# 8. Context Window

The Context Window is the amount of information the model can remember during one conversation.

Think of it as RAM.

Large context:

- Entire project
- Documentation
- PDFs
- Source code

Small context:

Only recent messages.

---

# 9. Token

LLMs do not read words.

They read **tokens**.

Example:

```
Hello world
```

may become

```
Helloworld
```

Each token has a cost.

More tokens:

- slower
- more expensive

---

# 10. Embeddings

Embeddings convert text into numbers.

Example:

```
"I love dogs"
```

↓

```
[0.52, -0.17, 0.88, ...]
```

These numbers capture the meaning of the text.

Texts with similar meanings have embeddings that are close together.

---

# 11. Vector Database

A Vector Database stores embeddings.

Popular vector databases:

- Pinecone
- Qdrant
- Weaviate
- Milvus
- ChromaDB

Example:

User asks:

```
Show my invoices.
```

Instead of searching by exact words,

the vector database searches by meaning.

---

# 12. RAG (Retrieval-Augmented Generation)

RAG allows an LLM to answer questions using **your own documents** instead of only what it learned during training.

Example:

User asks:

```
What is our company vacation policy?
```

The system:

User

↓

Search company documents

↓

Find PDF

↓

Send PDF to LLM

↓

Answer

The LLM doesn't memorize your documents—it retrieves the relevant ones first.

---

# 13. Fine-Tuning

Fine-tuning means retraining an existing model on specialized data.

Example:

A hospital trains a model using medical documents.

Result:

The model becomes much better at medical questions.

---

# 14. AI Agent

An AI Agent is an AI that can perform actions instead of only answering questions.

Example:

User:

```
Book my meeting.
```

Agent:

✔ Check calendar

↓

Find free time

↓

Create event

↓

Send invitations

↓

Confirm

Unlike a chatbot, an agent can act.

---

# 15. Agentic AI

Agentic AI refers to AI systems that:

- think
- plan
- decide
- execute
- verify

instead of answering one question.

Example:

```
Create a website.
```

Agent:

Plan

↓

Create folders

↓

Write code

↓

Run tests

↓

Fix bugs

↓

Deploy

---

# 16. Workflow

A workflow is a sequence of tasks.

Example:

Receive Email

↓

Read PDF

↓

Extract Data

↓

Save Database

↓

Send Notification

Platforms:

- n8n
- LangGraph
- Flowise

---

# 17. Tool Calling

Sometimes the AI needs external tools.

Example:

User:

```
What's the weather?
```

LLM:

↓

Calls weather API

↓

Returns result

The AI itself does not know the live weather; it uses a tool.

---

# 18. Function Calling

Function Calling allows the AI to invoke functions defined by developers.

Example:

```
createUser()sendEmail()calculatePrice()generateInvoice()
```

The model decides which function to call and with what parameters.

---

# 19. MCP Server (Model Context Protocol)

One of the most important concepts today.

MCP is a standard that allows AI models to communicate with external tools and data sources in a consistent way.

Think of it like:

```
USB-Cfor AI.
```

Instead of writing custom integrations for every AI and every tool:

```
ChatGPT ↔ GitHubClaude ↔ GitHubGemini ↔ GitHub
```

You expose one MCP server:

```
ChatGPT↓MCP↓GitHub↓Database↓Filesystem↓Jira↓Slack↓Figma
```

The AI can then:

- read files
- edit code
- query databases
- create tickets
- access APIs
- use enterprise systems

without needing a unique integration for each model.

---

# 20. Memory

Memory allows AI to remember useful information across conversations.

Example:

"I am a Spring Boot developer."

Next conversation:

The AI can personalize answers based on that preference.

Memory is different from the temporary conversation context.

---

# 21. Multi-Agent Systems

Instead of one AI,

multiple AI agents collaborate.

Example:

Planner Agent

↓

Developer Agent

↓

Tester Agent

↓

Reviewer Agent

↓

Deployment Agent

Each has a specialized role.

---

# 22. Model

A model is the trained AI itself.

Examples:

- GPT
- Claude
- Gemini
- Llama
- Mistral

Think of the model as the "brain."

---

# 23. Inference

Inference is when the trained model generates an answer.

Training happens once.

Inference happens every time you ask a question.

---

# 24. Training

Training is the process of teaching an AI using massive datasets.

It can take:

- weeks
- thousands of GPUs
- millions of dollars

Most developers never train foundation models; they use them through APIs or open-source checkpoints.

---

# 25. Hallucination

Hallucination occurs when the AI confidently produces incorrect or invented information.

Example:

It invents a book that does not exist or cites a fake API method.

Always verify important outputs.

---

# 26. Temperature

Temperature controls randomness.

Low (0.1):

- deterministic
- factual

High (1.0):

- creative
- more varied
- sometimes less accurate

---

# 27. API

Most AI models are accessed through an API.

Application

↓

HTTP Request

↓

AI Model

↓

Response

This is how applications integrate AI features.

---

# 28. Local AI

Instead of sending requests to the cloud,

the model runs on your own computer.

Examples:

- Ollama
- LM Studio
- vLLM (server)
- llama.cpp

Advantages:

- Privacy
- No internet required
- No per-request API cost

Disadvantages:

- Requires powerful hardware
- Large models need substantial RAM and often a capable GPU

---

# 29. Open Source Models

Popular open-weight models include:

- Llama
- Mistral
- Qwen
- Gemma
- DeepSeek

These can often be run locally or hosted on your own infrastructure, depending on their licenses and hardware requirements.

---

# 30. GPU

GPU = Graphics Processing Unit

AI models rely heavily on GPUs because they can perform many mathematical operations in parallel.

Without GPUs:

Training modern LLMs would be impractically slow.

---

# 31. AI IDEs

Modern development tools integrate AI into coding workflows.

Examples:

- VS Code + GitHub Copilot
- Cursor
- Windsurf
- Zed
- JetBrains AI Assistant

They can:

- explain code
- generate code
- refactor
- write tests
- find bugs
- generate documentation

---

# 32. Typical AI Application Architecture

```json
               User
                 │
                 ▼
          Web / Mobile App
                 │
                 ▼
        Backend (Spring/Laravel)
                 │
        ┌────────┴────────┐
        ▼                 ▼
   Authentication      Database
                             │
                             ▼
                      Vector Database
                             │
                             ▼
                          RAG Search
                             │
                             ▼
                        AI Model (LLM)
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
         MCP Server      External APIs     Tools
              │
    GitHub • Files • SQL • Jira • Slack
```

---

# 33. Summary

| Term               | Simple Definition                                              |
| ------------------ | -------------------------------------------------------------- |
| AI                 | Software that performs tasks requiring human-like intelligence |
| Machine Learning   | Learns patterns from data                                      |
| Deep Learning      | Machine learning using deep neural networks                    |
| Neural Network     | Mathematical model inspired by brain connections               |
| LLM                | AI specialized in understanding and generating language        |
| Prompt             | Your instruction to the AI                                     |
| Prompt Engineering | Writing effective prompts                                      |
| Token              | Small unit of text processed by an LLM                         |
| Context Window     | Information the model can consider in one interaction          |
| Embeddings         | Numeric representations of meaning                             |
| Vector Database    | Database optimized for similarity search on embeddings         |
| RAG                | Retrieves relevant documents before generating answers         |
| Fine-Tuning        | Additional training for a specific domain                      |
| AI Agent           | AI that can plan and perform actions                           |
| Agentic AI         | Autonomous AI that plans, acts, and iterates                   |
| Workflow           | Ordered sequence of tasks                                      |
| Tool Calling       | AI using external tools or APIs                                |
| Function Calling   | AI invoking developer-defined functions                        |
| MCP Server         | Standard interface connecting AI to tools and data             |
| Memory             | Information retained across conversations or sessions          |
| Multi-Agent System | Multiple AI agents collaborating                               |
| Model              | The trained AI itself                                          |
| Inference          | Running the model to produce an output                         |
| Training           | Teaching the model from data                                   |
| Hallucination      | Confidently generated incorrect information                    |
| Temperature        | Controls creativity vs. consistency                            |
| API                | Interface for applications to communicate with AI              |
| Local AI           | Running AI models on your own hardware                         |
| Open Source Model  | AI model that can often be self-hosted or adapted              |
| GPU                | Processor optimized for AI computations                        |
| AI IDE             | Development environment with integrated AI assistance          |

---

## What to learn next as a software developer

A practical learning order is:

1. AI fundamentals (AI, ML, Deep Learning, LLMs)
2. Prompt Engineering
3. Tokens, Context Windows, and Embeddings
4. Vector Databases and RAG
5. AI APIs and Function Calling
6. AI Agents and Agentic Workflows
7. MCP Servers
8. Local AI (Ollama, LM Studio)
9. AI frameworks (LangChain, LangGraph, LlamaIndex)
10. Model deployment and observability
11. Fine-tuning and evaluation
12. AI security, privacy, and responsible AI practices

With these concepts, you'll understand the architecture behind most modern AI-powered applications and be well prepared to build them yourself.
