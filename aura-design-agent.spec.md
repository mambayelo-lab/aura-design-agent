# Aura Design Agent — SpecKit Specification

## Overview
Aura Design Agent is an AI-driven conversational system that conducts adaptive business interviews to understand an organization’s activity, processes, events, actors, and constraints. It then structures this information into business capabilities, processes, applications, data architecture, and organizational patterns.

The goal is to provide the "business discovery + event storming" layer of Aura (Augmented Reasoning Unified Ontology Architecture).

This specification defines:
- A frontend chat interface
- A backend API to handle the interview logic
- A memory/storage layer for structured interview data
- An agent pipeline for dynamic questioning (“what-if” probing)
- Export of structured insights in JSON

---

## System Components

### 1. Frontend (Next.js + React)
- A chat interface similar to ChatGPT
- Displays messages from user and agent
- Sends messages to backend API `/api/interview`
- Shows loading indicators
- Allows conversation history scrolling
- Supports sessions (one session per interview)

---

### 2. Backend API (Node/TypeScript)
#### Endpoint: `POST /api/interview`
Input:
```json
{
  "session_id": "string",
  "messages": [
    { "role": "user", "content": "string" },
    { "role": "assistant", "content": "string" }
  ]
}
