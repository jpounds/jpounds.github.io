# LangChain Core Concepts Explained

## Overview
LangChain is a framework for building applications powered by large language models (LLMs). It provides abstractions that help developers connect prompts, models, tools, and data sources into reliable workflows.

This document explains the core concepts behind LangChain and how they fit together.

---

## Chains
A **chain** is a sequence of steps that process an input and produce an output. Each step can involve a prompt, a model call, or other logic.

Chains are useful when:
- A task follows a predictable flow
- Each step depends on the previous output

**Example use cases:**
- Summarizing documents
- Transforming text
- Running multi-step prompts

---

## Agents
An **agent** is a dynamic system that decides what actions to take at runtime. Instead of following a fixed sequence, agents use an LLM to choose which tools to call based on the current context.

Agents are useful when:
- The steps are not known ahead of time
- The model needs to reason about which action to take

---

## Tools
**Tools** are functions that agents can call to interact with external systems. Examples include APIs, databases, or custom Python functions.

Tools allow LangChain applications to:
- Retrieve external data
- Perform calculations
- Take real-world actions

---

## Memory
**Memory** allows an application to retain information across interactions. This can include conversation history, user preferences, or intermediate results.

Memory helps create:
- Conversational experiences
- Context-aware responses

---

## How These Concepts Fit Together
A typical LangChain application may:
1. Use a **chain** for predictable preprocessing
2. Invoke an **agent** for decision-making
3. Call **tools** to fetch or act on data
4. Store context using **memory**

Understanding when to use each abstraction helps developers design systems that are both flexible and maintainable.

---

## Summary
LangChain’s abstractions are designed to simplify building LLM-powered applications. By combining chains, agents, tools, and memory, developers can create powerful AI workflows without managing low-level details.
