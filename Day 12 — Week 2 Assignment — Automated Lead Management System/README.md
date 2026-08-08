# Day 12 — Automated Lead Management System

## Project Overview

This project is an automated Lead Management System built using n8n.

The workflow receives new lead information through a webhook, validates the submitted data, calculates a lead score, assigns a priority, routes the lead according to the priority, saves the required information in Google Sheets, and sends automatic email notifications.

## Objective

The objective of this project is to create a complete automated lead-management workflow that can:

- Receive lead information through a webhook
- Validate the submitted information
- Process and score the lead
- Assign High, Medium, or Low priority
- Route leads automatically
- Notify the sales team for high-priority leads
- Save medium-priority leads in Google Sheets
- Save low-priority leads in a follow-up list
- Send an automatic acknowledgment email to the lead

## Technologies Used

- n8n
- Webhooks
- JavaScript / Code Node
- Postman
- Google Sheets
- Gmail
- External API
- HTTP Request
- IF Node
- Switch / Priority Router

## Lead Fields

The workflow accepts the following information:

- Name
- Email
- Company
- Service
- Budget

## Workflow

The workflow follows this structure:

Webhook
↓
Validation
↓
Lead Processing
↓
Lead Scoring
↓
Priority Router
↓
High / Medium / Low Route

### High Priority

High-priority leads are immediately sent to the sales team through Gmail.

After the sales notification, an acknowledgment email is sent to the lead.

### Medium Priority

Medium-priority leads are saved in Google Sheets.

After saving the lead, an acknowledgment email is sent to the lead.

### Low Priority

Low-priority leads are added to the follow-up/nurture Google Sheet.

After saving the lead, an acknowledgment email is sent to the lead.

## Sample Lead

Example input:

{
  "name": "Noor-ul-Huda",
  "email": "saniasohail889@gmail.com",
  "company": "ABC Solutions",
  "service": "AI Automation",
  "budget": 150000
}

## Testing

The workflow was tested using Postman with POST requests.

### High Priority Test

{
  "name": "Noor-ul-Huda",
  "email": "saniasohail889@gmail.com",
  "company": "ABC Solutions",
  "service": "AI Automation",
  "budget": 150000
}

Expected result:

High Priority → Sales Notification → Acknowledgment Email

### Medium Priority Test

{
  "name": "Ali Khan",
  "email": "saniasohail889@gmail.com",
  "company": "Khan Enterprises",
  "service": "Web Development",
  "budget": 100000
}

Expected result:

Medium Priority → Google Sheets → Acknowledgment Email

### Low Priority Test

{
  "name": "Sara Ahmed",
  "email": "saniasohail889@gmail.com",
  "company": "Sara Store",
  "service": "Web Development",
  "budget": 30000
}

Expected result:

Low Priority → Follow-up Google Sheet → Acknowledgment Email

## Results

All three priority routes were tested successfully.

- High Priority route worked successfully.
- Medium Priority route worked successfully.
- Low Priority route worked successfully.
- Google Sheets records were saved successfully.
- Email notifications and acknowledgment emails were sent successfully.

## Conclusion

The Automated Lead Management System successfully automates the complete lead-handling process.

It reduces manual work by automatically validating, scoring, routing, storing, and notifying about new leads.
