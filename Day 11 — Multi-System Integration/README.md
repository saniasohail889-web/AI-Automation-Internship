# Day 11 – Lead Processing Workflow

## Objective
Build a Lead Processing Workflow using a webhook, external API, Google Sheets, and Gmail.

## Workflow

Webhook → Edit Fields → IF → HTTP Request → Google Sheets → Gmail

## Steps

1. Receive lead data through a Webhook.
2. Validate the submitted information.
3. Call the Agify API to predict the lead's age.
4. Save the lead information in Google Sheets.
5. Send a confirmation email using Gmail.

## Technologies Used

- n8n
- Webhook
- HTTP Request (Agify API)
- Google Sheets
- Gmail

## Sample Input

```json
{
  "Name": "Noor-ul-Huda",
  "Email": "noor@example.com",
  "City": "Karachi"
}
```

## Sample Output

- Name: Noor-ul-Huda
- Email: noor@example.com
- City: Karachi
- Predicted Age: 37
