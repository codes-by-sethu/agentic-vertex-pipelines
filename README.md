# Agentic AI & Reliable Prompt Pipelines with Vertex AI

> **Note:** This project was developed as part of the Master's curriculum at ESILV. It explores the implementation of reliable AI agents using Google Vertex AI (Gemini 2.5), Chain-of-Thought reasoning, and Tool Use (Function Calling).

## 🎯 The Business Problem
Large Language Models (LLMs) are powerful but prone to **hallucinations** and **inconsistency**. In production environments (like E-commerce Support or Financial Analysis), a model cannot just "guess"; it must:
1.  **Reason** before answering (Chain-of-Thought).
2.  **Self-Correct** its own output (Reflexion/Critique).
3.  **Execute Actions** reliably (Function Calling).
4.  **Output Structured Data** for downstream applications (JSON enforcement).

## 🛠️ The Solution
This repository implements a suite of **production-ready prompt engineering patterns** designed to maximize reliability and determinism.

### Key Features Implemented:
* **⛓️ Agentic Prompt Chaining:** A multi-step pipeline that takes raw text, extracts key points, expands on them, synthesizes a summary, and **critiques its own work** to ensure quality.
* **🧠 Chain-of-Thought (CoT):** Implemented step-by-step reasoning prompts to solve complex logic problems with higher accuracy than zero-shot methods.
* **🛠️ ReAct / Tool Use:** Integrated Function Calling to allow the LLM to access external tools (Calculators, Knowledge Bases) rather than relying solely on training data.
* **🛡️ Structured Output Enforcement:** Utilized `Pydantic` schemas to force the LLM to output valid, parseable JSON for seamless API integration.

## 🏗️ Architecture: The "Self-Correcting" Pipeline

This project moves beyond simple prompting by implementing a **feedback loop**:

```mermaid
graph TD;
    Input[User Input] --> Extract[Agent 1: Extraction];
    Extract --> Expand[Agent 2: Expansion];
    Expand --> Synth[Agent 3: Synthesis];
    Synth --> Critique[Agent 4: Critique & Revise];
    Critique --> Output[Final Reliable Output];
