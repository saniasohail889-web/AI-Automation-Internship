# Day 15 — LLM Integration inside n8n

## Objective

The objective of Day 15 was to integrate an LLM into an n8n workflow and classify emails automatically.

## Workflow

The workflow follows this process:

Webhook → AI Analysis → Classify → Route by Category

## AI Model

Groq Chat Model was used for email classification.

## Email Categories

The AI classifies emails into one of these categories:

- Sales
- Support
- Complaint
- Invoice
- Spam
- General

## Prompt

The AI prompt instructs the model to analyze the email and return only one category.

The email information is passed dynamically using n8n expressions:

- Subject
- From
- Body

## Testing

The workflow was tested with different email examples.

Successful classifications included:

- General
- Support
- Invoice

Additional categories configured in the Switch node:

- Sales
- Spam
- Complaint

## Result

The AI successfully classified the incoming emails, and the Switch node routed each result to the corresponding category.
