# Day 21 — Company / HR Policy RAG Assistant

## Project Overview

The Company / HR Policy RAG Assistant is an AI-powered question-answering system built using n8n, an OpenAI chat model, and an in-memory Vector Store.

The assistant answers questions about company and HR policies using information stored in its knowledge base.

The system is designed to avoid making up policies. If the requested information is not available in the knowledge base, the assistant provides a clear fallback response.

## Objective

The main objectives of this project are:

* Build a Retrieval-Augmented Generation (RAG) assistant.
* Store company policies in a vector database.
* Retrieve relevant policy information for user questions.
* Generate answers using an AI model.
* Prevent the AI from inventing company policies.
* Provide the source of the information where possible.
* Provide a safe fallback when information is unavailable.

## Technologies Used

* n8n
* OpenAI Chat Model (gpt-4o-mini)
* OpenAI Embeddings (text-embedding-3-small)
* In-Memory Vector Store
* Recursive Character Text Splitter
* RAG
* AI Agent
* Chat Trigger

## Knowledge Base

The knowledge base contains five main HR policy areas:

1. Leave Policy
2. Working Hours
3. Attendance Policy
4. Internship Guidelines
5. Code of Conduct

## RAG Architecture

### Document Ingestion

```text
HR Policy Document
        ↓
Document Loader
        ↓
Text Splitter
        ↓
OpenAI Embeddings
        ↓
In-Memory Vector Store
```

The policy document is divided into smaller chunks along its section headers. Each chunk is converted into an embedding and stored in the vector store.

### Question Answering

```text
User Question
        ↓
Chat Trigger
        ↓
AI Agent
        ↓
Vector Store Retriever (top-4 chunks)
        ↓
Relevant Policy Information
        ↓
OpenAI Chat Model
        ↓
Answer + Source
```

## How the System Works

When the user asks a question, the system searches the Vector Store for relevant information.

The retrieved policy information is provided to the AI Agent.

The AI Agent generates an answer using only the retrieved information.

If the required information does not exist in the knowledge base, the assistant does not guess the answer. Instead, it returns the fallback response.

## Grounding Rules

The AI assistant follows these rules:

```text
You are a Company HR Policy Assistant.

Answer questions ONLY using information retrieved from the company's HR knowledge base.

Never invent, guess, assume, or create a company policy.

Do not use general knowledge to fill missing information.

If the knowledge base does not contain enough information to answer the question, respond:

"⚠️ Information not available in the HR policy knowledge base. Please check with HR directly."

Whenever possible, mention the source policy used for the answer.

Keep answers clear and concise.
```

## Source Citation

The assistant mentions the policy source whenever possible.

Example:

```text
Answer:
Employees are entitled to 12 Casual Leaves (CL) per calendar year.

Source:
Section 1 — Leave Policy
```

This allows the user to understand where the answer came from.

## Fallback Handling

The system includes a fallback for questions that cannot be answered from the knowledge base.

Example:

```text
Question:
What is the exact salary of a senior software engineer?

Answer:
⚠️ Information not available in the HR policy knowledge base. Please check with HR directly.

Source:
Not available
```

The knowledge base does not contain individual salary figures, so the assistant does not invent one.

## Test Cases

### Test Case 1 — Leave Policy

**Question:**

How many casual leaves are allowed per year?

**Expected Answer:**

Employees are entitled to 12 Casual Leaves (CL) per calendar year, credited at 1 per month.

**Source:**

Section 1 — Leave Policy

---

### Test Case 2 — Working Hours

**Question:**

What are the standard working hours?

**Expected Answer:**

Standard working hours are 9:00 AM to 6:00 PM, Monday to Friday, with a flexible start window between 8:30 AM and 10:00 AM.

**Source:**

Section 2 — Working Hours

---

### Test Case 3 — Attendance

**Question:**

How many late-ins are allowed before a leave gets deducted?

**Expected Answer:**

A 15-minute grace period is allowed. 3 late-ins in a calendar month result in a 0.5 day Casual Leave deduction.

**Source:**

Section 3 — Attendance Policy

---

### Test Case 4 — Internship

**Question:**

Do interns get a certificate at the end?

**Expected Answer:**

Yes, if the intern completes at least 80% attendance and a final evaluation with their reporting manager.

**Source:**

Section 4 — Internship Guidelines

---

### Test Case 5 — Fallback

**Question:**

What is the exact salary of a senior software engineer?

**Expected Answer:**

⚠️ Information not available in the HR policy knowledge base. Please check with HR directly.

**Source:**

Not available

## Conclusion

The Company / HR Policy RAG Assistant demonstrates how RAG can be used to answer questions from a controlled company knowledge base.

The system retrieves relevant information from an in-memory vector store and uses an OpenAI chat model to generate a grounded response.

The fallback mechanism prevents the AI from inventing policies when the required information is not available.
