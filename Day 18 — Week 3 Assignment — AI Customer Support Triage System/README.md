# Day 18 — AI Customer Support Triage System

## Objective
Deliver a production-style AI triage workflow with validated structured output.

## Workflow
Customer Message → Webhook → AI Analysis → Structured JSON → Switch by Category → Build Row → Store Ticket → Send Acknowledgment → Is Urgent? → Urgent Alert if required

## What the system does
The workflow receives a customer support message through an n8n Webhook. The AI analyzes the message and produces validated structured JSON containing:
- category
- priority
- sentiment
- department
- summary
- suggested_response

The Switch routes the ticket according to category. The ticket is then prepared for storage in Google Sheets. The customer receives an acknowledgment email. If priority is Urgent, the TRUE branch of the Is Urgent? node sends an urgent alert. If it is not urgent, the FALSE branch ends normally; no separate Non-Urgent node is required.

## Categories
Billing, Technical, Account, Sales, General

## Priority
Low, Medium, High, Urgent

## Sentiment
Positive, Neutral, Negative

## Department
Billing, Support, Sales, Customer Success

## Tools
- n8n
- AI/LLM node
- Webhook
- Switch
- Google Sheets
- Gmail
- Postman

## Structured Output Validation
The AI uses a JSON Schema with `additionalProperties: false`, required fields, and enum values. This prevents unsupported categories, priorities, sentiments, and departments from being returned.

## Google Sheet Columns
customerMessage | category | priority | sentiment | department | summary | suggestedResponse
