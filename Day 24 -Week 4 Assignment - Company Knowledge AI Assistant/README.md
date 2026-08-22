# Day 24 — Company Knowledge AI Assistant (RAG)

## Objective
Build a complete company-knowledge RAG assistant that ingests knowledge, creates embeddings, stores it in a Supabase vector database, retrieves relevant information, and generates grounded answers.

## Project Architecture

```text
Company Knowledge (24 entries)
        ↓
Ingestion Workflow
        ↓
Document Loader
        ↓
OpenAI Embeddings (1536 dimensions)
        ↓
Supabase Vector Store (`documents`)
        ↓
User Question
        ↓
n8n AI Agent
        ↓
Supabase Vector Retrieval
        ↓
OpenAI GPT Model
        ↓
Grounded Answer + Source
        ↓
Fallback when information is unavailable
```

## Workflows

### 1. Company Knowledge — Ingestion (Supabase)
The ingestion workflow creates 24 company-knowledge entries, loads them as documents, creates OpenAI embeddings, and inserts them into the Supabase `documents` vector table.

### 2. Company Knowledge AI Assistant (RAG)
The assistant workflow uses an n8n Chat Trigger, AI Agent, OpenAI chat model, Supabase vector-store tool, OpenAI embeddings, and conversation memory.

## Knowledge Base

The knowledge base contains 24 entries covering:
- Company
- HR
- Finance
- IT
- Security
- Products
- Support

The source spreadsheet is included as `Company_Knowledge_24_Entries.xlsx`.

## RAG Behavior

The assistant is instructed to:
1. Search the company knowledge-base tool before answering company questions.
2. Use only retrieved content.
3. Avoid guessing or using outside knowledge.
4. Cite the source when an answer is available.
5. Return an information-not-available message when the knowledge base does not contain the answer.
6. Use conversation history for follow-up questions.
7. Provide a human-contact response when the user asks to talk to a human.

## Vector Database

The Supabase table is:

`documents`

Expected columns:
- `id`
- `content`
- `metadata`
- `embedding vector(1536)`

## Conversation Memory

The assistant includes conversation memory with a context window of 10 messages. A learning-budget follow-up question is included in the test document to demonstrate memory.

## Testing

See `10_Example_Queries_and_Results.docx` for 10 example queries covering:
- HR policy retrieval
- Finance retrieval
- Security retrieval
- Product and pricing retrieval
- SLA and refund retrieval
- Conversation memory
- Information-not-available fallback

## Files

- `Company Knowledge — Ingestion (Supabase).json` — ingestion workflow
- `Company Knowledge AI Assistant (RAG).json` — RAG assistant workflow
- `Company_Knowledge_24_Entries.xlsx` — 24 knowledge entries
- `10_Example_Queries_and_Results.docx` — test queries and expected results
- `README.md` — project documentation
