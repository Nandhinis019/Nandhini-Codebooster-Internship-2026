
# Day 6 - GenAI + Prompt Engineering (Groq API)

## Overview

Day 6 focused on understanding Generative AI (GenAI), Prompt Engineering techniques, and integrating Groq API with LangChain to build intelligent AI applications.

---

## Topics Covered

### 1. Generative AI (GenAI)

Generative AI refers to artificial intelligence models capable of generating new content such as text, images, code, audio, and videos based on user prompts.

#### Applications

* Chatbots
* Content Generation
* Code Generation
* Virtual Assistants
* Recommendation Systems

---

### 2. Prompt Engineering

Prompt Engineering is the process of designing effective prompts to obtain accurate and relevant outputs from Large Language Models (LLMs).

#### Benefits

* Improves response quality
* Reduces ambiguity
* Enhances reasoning capability
* Optimizes AI performance

---

## Prompting Techniques

### Zero-Shot Prompting

No examples are provided to the model.

**Example**

```text
Translate "Good Evening" into Tamil.
```

---

### One-Shot Prompting

One example is provided before the actual task.

**Example**

```text
English: Hello
Tamil: வணக்கம்

English: Good Evening
Tamil:
```

---

### Few-Shot Prompting

Multiple examples are provided to guide the model.

**Example**

```text
English: Hello
Tamil: வணக்கம்

English: Thank You
Tamil: நன்றி

English: Good Evening
Tamil:
```

---

### Chain of Thought (CoT)

The model reasons step-by-step before generating the final answer.

**Example**

```text
Solve 25 × 12 step by step.
```

---

### Tree of Thoughts (ToT)

The model explores multiple reasoning paths, evaluates them, and selects the best solution.

**Workflow**

```text
Problem
   ↓
Reasoning Path 1
Reasoning Path 2
Reasoning Path 3
   ↓
Evaluation
   ↓
Best Path
   ↓
Final Answer
```

---

### Role Prompting

Assigning a specific role to the model.

**Example**

```text
Act as a Software Engineer and explain LangChain.
```

---

## LangChain Components

### LLM (Large Language Model)

Processes prompts and generates responses.

### Prompt Template

Creates reusable and dynamic prompts.

### Output Parser

Converts model output into a structured format.

### Chain

Connects Prompt → LLM → Parser.

**Workflow**

```text
User Input
    ↓
Prompt Template
    ↓
LLM
    ↓
Output Parser
    ↓
Final Response
```

---

## Groq API Integration

Groq provides high-speed inference for Large Language Models.

### Installation

```python
!pip install langchain langchain-groq langchain-core
```

### Import Libraries

```python
import os
from langchain_groq import ChatGroq
from langchain_core.prompts import PromptTemplate
from langchain_core.output_parsers import StrOutputParser
```

### Initialize LLM

```python
llm = ChatGroq(
    model="llama-3.3-70b-versatile",
    temperature=0
)
```

---

## Tree of Thoughts Prompt

```python
prompt = PromptTemplate(
    input_variables=["question"],
    template="""
You are an advanced reasoning assistant.

Step 1: Generate THREE different reasoning paths.

Step 2: Evaluate each path.

Step 3: Choose the best path.

Step 4: Provide the final answer.

Question: {question}
"""
)
```

---

## Twilio WhatsApp Integration

Twilio WhatsApp Sandbox allows sending AI-generated responses directly to WhatsApp.

### Installation

```python
!pip install twilio
```

### Import

```python
from twilio.rest import Client
```

### Send WhatsApp Message

```python
msg = client.messages.create(
    body=response,
    from_="whatsapp:+14155238886",
    to="whatsapp:+91XXXXXXXXXX"
)
```

---

## Integrated AI Agent Architecture

```text
User Question
      ↓
Prompt Template
      ↓
LangChain
      ↓
Groq LLM
      ↓
Tree of Thoughts
      ↓
Best Solution
      ↓
Twilio WhatsApp
      ↓
User Receives Result
```

---

## Key Learnings

* Introduction to Generative AI
* Prompt Engineering Fundamentals
* Zero-Shot, One-Shot, Few-Shot Prompting
* Chain of Thought Reasoning
* Tree of Thoughts Reasoning
* LangChain Components
* Groq API Integration
* Twilio WhatsApp Messaging
* Building End-to-End AI Agents

---

## Outcome

Successfully developed an AI-powered reasoning assistant using LangChain and Groq API, implemented advanced prompting techniques such as Tree of Thoughts, and integrated Twilio WhatsApp Sandbox to deliver AI-generated responses directly to users.
