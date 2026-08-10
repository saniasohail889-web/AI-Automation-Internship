# Day 13 — Generative AI & LLM Fundamentals

## Objective

The objective of Day 13 was to understand the basics of Generative AI and Large Language Models (LLMs), and to set up and test API access from different AI providers.

## What I Learned

- Difference between AI, Machine Learning, Generative AI, and LLMs
- Tokens and context windows
- System instructions and user input
- Hallucinations and model limitations
- Basic cost awareness when using AI APIs
- Different AI providers such as Gemini, Groq, OpenAI, Claude, and Ollama

## Practical Task

For this task, I generated API keys for:

- Google Gemini
- Groq

I then tested both APIs using Postman to verify that the model access was working successfully.

## Gemini API Test

- Provider: Google Gemini
- Tool used: Postman
- Request type: POST
- Result: 200 OK
- Status: Successful

The Gemini API successfully returned an AI-generated response.

## Groq API Test

- Provider: Groq
- Tool used: Postman
- Request type: POST
- Result: 200 OK
- Status: Successful

The Groq API successfully returned an AI-generated response.

## Provider Comparison

For classification tasks, I would choose **Groq** because fast responses are useful in automation workflows. For example, it can quickly classify leads into High, Medium, or Low priority.

For long-context work, I would choose **Google Gemini** because suitable Gemini models can work with large amounts of information. This makes it useful for tasks such as document analysis and summarization.

Overall, I would use Groq when speed is the main requirement and Gemini when handling larger amounts of information is more important.
