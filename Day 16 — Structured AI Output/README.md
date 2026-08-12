# Day 16 — Structured AI Output

## Objective

The objective of this task was to create a reliable AI workflow that produces structured and predictable output instead of free-form text.

The workflow uses an AI model to analyze customer messages and return the result in a fixed JSON format. The response is then validated, and unexpected responses are sent to a fallback path.

## Tools Used

- n8n
- Groq Chat Model
- Structured Output Parser
- JSON Schema

## Workflow

Manual Trigger → Test Input → Basic LLM Chain → Structured Output Parser → Validate Output → IF → Success / Fallback

## Input Example

The customer received the wrong product and is very unhappy. Please help resolve this issue quickly.

## Structured Output

The AI returns the following fields:

```json
{
  "category": "Returns",
  "priority": "High",
  "sentiment": "Negative",
  "department": "Customer Service",
  "summary": "Wrong product received"
}
