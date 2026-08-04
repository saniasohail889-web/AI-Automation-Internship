# Candidate Screening Automation

## Project Name
Candidate Screening Automation

## Problem Statement
Companies receive many internship applications, and checking each one manually takes a lot of time. This workflow automates the screening process and sends the appropriate email to each candidate.

## Objective
The objective of this project is to automate the candidate screening process using n8n. It reads candidate information from Google Sheets, validates the data, categorizes the candidates, updates the results in the sheet, and sends a personalized email.

## Workflow Architecture
Start Screening → Read Candidates → Validate & Categorize → Update Result → Categorize Candidate → Send Email

## Technologies Used
- n8n
- Google Sheets
- Gmail

## Nodes Used
- Manual Trigger
- Google Sheets (Read Candidates)
- Validate & Categorize
- Google Sheets (Update Result)
- Rules (Categorize Candidate)
- Gmail (Shortlisted)
- Gmail (On Hold)
- Gmail (Rejected)
- Gmail (Incomplete)

## Setup Instructions
1. Connect your Google Sheets account.
2. Connect your Gmail account.
3. Import the workflow into n8n.
4. Select your Google Sheet.
5. Execute the workflow.

## Credentials Required
- Google Sheets Account
- Gmail Account

## Workflow Explanation
The workflow starts with a manual trigger and reads candidate information from Google Sheets. It checks whether the required information is available, categorizes each candidate based on the screening rules, updates the status in the Google Sheet, and finally sends the appropriate email according to the candidate's category.

## Test Cases
- Eligible candidate → Shortlisted
- Partially eligible → On Hold
- Not eligible → Rejected
- Missing information → Incomplete

## Error Handling
The workflow checks for missing information and handles incomplete records without stopping the execution.

## Known Limitations
- Requires a Google Sheets account.
- Requires a Gmail account.
- Internet connection is required.

## Future Improvements
- Resume upload support
- AI-based resume screening
- Interview scheduling automation
- Candidate scoring system
