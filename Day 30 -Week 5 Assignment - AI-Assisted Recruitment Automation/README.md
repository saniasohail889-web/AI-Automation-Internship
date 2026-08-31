# AI-Assisted Recruitment Automation

## Day 30 — Week 5 Assignment

### Project Overview

This project is an **AI-Assisted Recruitment Automation** workflow built using n8n.

The system automates the initial recruitment process by collecting candidate applications, extracting resume information, using AI to analyze candidate skills and experience, applying rule-based assessment, and sending the assessment to an authorized human reviewer.

The AI only provides assistance and recommendations. **The final recruitment decision is always made by a human reviewer.**

---

## Objective

The objective of this project is to build a secure, reliable, error-handled, and human-approved recruitment automation.

The workflow helps reduce manual work during the initial candidate screening process while keeping humans in control of the final decision.

---

## Workflow

The workflow follows these main steps:

**Application → Resume Extraction → AI Analysis → Rule-Based Assessment → Store Candidate Data → Human Review → Shortlist/Reject → Candidate Email → Database Update**

---

## 1. Candidate Application

The workflow starts with an n8n **Job Application** form.

The candidate provides:

* Full Name
* Email
* Phone
* Position Applied For
* Resume in PDF format

The form explains that AI assists with the review but a human makes the final decision.

---

## 2. Resume Text Extraction

The uploaded PDF resume is processed using the **Extract Resume Text** node.

The resume text is extracted so that it can be analyzed by the AI system.

---

## 3. AI Analysis

The **AI Analysis** node uses an OpenAI model to analyze the candidate's resume and position applied for.

The AI extracts:

* Skills
* Relevant experience
* Candidate score
* AI recommendation
* Reason
* Candidate summary

The AI recommendation can be:

* Shortlist
* Maybe
* Reject

The AI does not make the final hiring decision.

---

## 4. Rule-Based Assessment

After AI analysis, the **Rule-Based Assessment** Code node applies deterministic business rules.

The workflow checks information such as:

* Whether skills were detected
* Relevant experience
* AI score
* Email validity
* High or low score indicators

The system combines the AI assessment with these rule-based checks to create a system recommendation.

For example:

* Score ≥ 80 → high AI score
* Score < 40 → low AI score
* Experience < 2 years → junior experience flag
* Invalid email → invalid email flag

The rules are used to support the assessment and do not replace human review.

---

## 5. Candidate Data Storage

Candidate information and assessment results are stored in the recruitment data table.

Stored information includes:

* Candidate name
* Email
* Phone
* Position
* Resume text
* Skills
* Experience
* AI score
* AI recommendation
* AI reason
* Rule flags
* Status
* Execution ID
* Submission time

---

## 6. Human Review

The assessment is sent to an authorized human reviewer through Gmail.

The reviewer receives:

* Candidate name
* Email
* Phone
* Position
* Experience
* Skills
* AI score
* AI recommendation
* System recommendation
* AI reason
* Rule flags

The reviewer has two choices:

**Shortlist** or **Reject**

This is the human-in-the-loop part of the system.

The AI does not make the final hiring decision.

---

## 7. Shortlist

If the authorized human reviewer selects **Shortlist**:

1. The candidate receives a shortlist email.
2. The candidate database record is updated.
3. The final decision is stored as `shortlist`.
4. The status is changed to `shortlisted`.
5. The reviewer response is recorded.

---

## 8. Reject

If the authorized human reviewer selects **Reject**:

1. The candidate receives a rejection email.
2. The candidate database record is updated.
3. The final decision is stored as `reject`.
4. The status is changed to `rejected`.
5. The reviewer response is recorded.

---

## 9. Error Handling

The workflow includes error handling for important processing stages.

If resume extraction or AI analysis fails:

**Error → Log Error → Notify Admin**

The error is logged with information such as:

* Error message
* Execution ID
* Execution URL
* Failed node
* Workflow ID
* Workflow name
* Timestamp

An administrator is notified by email so that the candidate is not silently lost.

---

## 10. Security and Responsible AI

The workflow follows these principles:

* AI does not make the final hiring decision.
* Human approval is required before shortlisting or rejecting a candidate.
* API credentials are stored using n8n credentials.
* Candidate information is processed only for recruitment assessment.
* The AI prompt instructs the model to avoid bias based on age, gender, ethnicity, and personal attributes.
* The assessment focuses on job-related skills and experience.

---

## 11. Example AI Output

Example:

```json
{
  "skills": [
    "Python",
    "SQL",
    "n8n",
    "REST APIs",
    "Supabase"
  ],
  "experience_years": 1,
  "score": 85,
  "recommendation": "shortlist",
  "reason": "The candidate has strong technical skills relevant to AI automation.",
  "summary": "The candidate has practical experience with automation, databases, APIs, and AI-related tools."
}
```

This output is an AI recommendation only. The authorized human reviewer makes the final decision.

---

## 12. Testing

The workflow can be tested by submitting a sample candidate application through the n8n Job Application form.

Example test candidate:

**Name:** Noor
**Position:** AI Automation Intern
**Email:** [noor@example.com](mailto:noor@example.com)
**Resume:** Noor's AI Automation resume in PDF format

After submission:

1. Resume text is extracted.
2. AI analyzes the resume.
3. Rules are applied.
4. Candidate data is stored.
5. Human reviewer receives the review email.
6. Reviewer selects Shortlist or Reject.
7. Candidate receives the appropriate email.
8. Database status is updated.

---

## Conclusion

The AI-Assisted Recruitment Automation workflow demonstrates how AI can assist with candidate screening while keeping the final recruitment decision under authorized human control.

The project combines AI analysis, structured information extraction, rule-based assessment, human approval, automated communication, database updates, and error handling in one n8n workflow.

