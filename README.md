# AI Resume Screening Automation

A Make.com (Integromat) scenario that automatically screens and scores incoming job applicant resumes using AI — built by [Sohag Gain](https://bd.linkedin.com/in/sohaggain), Founder & CEO of [AI Smart Galaxy](https://www.aismartgalaxy.com), an AI automation agency helping businesses adopt AI-driven workflows.

This project was built to solve real hiring bottlenecks at AI Smart Galaxy and demonstrates a rubric-based AI scoring system — a pattern directly reusable for recruiters, agencies, and any business that needs objective, consistent, high-volume candidate evaluation.

## What It Does

1. **Google Sheets (Watch New Rows)** — monitors a connected Google Form's response sheet for new job applicants.
2. **HTTP (Get a file)** — retrieves the applicant's uploaded resume file (Google Drive link) from the form submission.
3. **PDF.co (Convert from PDF)** — converts the resume PDF into plain text for AI processing.
4. **OpenAI (Generate a Completion)** — evaluates the resume text against a structured, weighted scoring rubric:
   - **Experience in Role** — up to 20 points for 3+ years in the target position
   - **Degree in Relevant Field** — 10 points for a matching or related degree
   - **Spelling & Grammar** — up to 15-point deduction for 5+ language issues
   - **Reputable University** — 5 points
   - **Sales Experience** — up to 20 points for cold-calling/prospecting background
   - **Unemployment Gap** — up to 30-point deduction for 1+ year gaps
   - **Job Longevity** — up to 30-point deduction if average tenure is under 1.5 years
   - **Keyword Frequency** — 5 points for role-relevant keyword density

   The model returns a structured JSON score breakdown and an overall percentage (0–100%).
5. **Google Sheets (Update a Row)** — writes the score, comments, and evaluation back into the tracking sheet.
6. **Router** — branches candidates into two paths based on outcome:
   - **Rejected** → automated rejection email
   - **Interview** → automated interview-invitation email

## Tracking Sheet Structure

The connected Google Sheet records each applicant with:

`Timestamp | First Name | Last Name | Email | Resume (link) | Position | Score | Comments | Rejected | Interview`

## Tech Stack

| Component | Tool |
|---|---|
| Orchestration | [Make.com](https://make.com) |
| Form intake | Google Forms + Google Sheets |
| Resume file retrieval | HTTP module |
| PDF-to-text conversion | [PDF.co](https://pdf.co) |
| AI scoring | OpenAI (GPT) |
| Candidate tracking | Google Sheets |
| Outcome routing | Make.com Router |
| Candidate communication | Email module |

## Setup

1. Import the Make.com blueprint (`.json`) into a new scenario.
2. Reconnect your own accounts for:
   - Google Sheets / Google Drive
   - PDF.co API
   - OpenAI API
   - Email (SMTP or connected mailbox)
3. Point the Google Sheets "Watch New Rows" module at your own applicant intake sheet.
4. Update the scoring rubric's role/keyword placeholders (currently templated per open position) to match your hiring needs.
5. Customize the Rejected and Interview email templates in the Email modules.
6. Turn on scheduling (e.g. every 15 minutes) or set to run on trigger.

## Why This Matters

Manual resume screening doesn't scale — a recruiter reviewing 50+ applicants per role spends hours on work an AI rubric can do consistently in seconds. This scenario removes reviewer bias and inconsistency by scoring every resume against the same fixed criteria, while still keeping a human in the loop for the final decision.

## About AI Smart Galaxy

AI Smart Galaxy is an AI automation agency founded by Sohag Gain, specializing in AI Agents, workflow automation (n8n, Make.com, Zapier, GoHighLevel), and business process automation for agencies, SaaS companies, e-commerce, real estate, coaches, and service businesses.

🌐 [aismartgalaxy.com](https://www.aismartgalaxy.com) | [Services](https://aismartgalaxy.com/services-ai-automation) | [LinkedIn](https://bd.linkedin.com/in/sohaggain)

## Author

**Sohag Gain**
Founder & CEO, AI Smart Galaxy — AI Automation, AI Agents & Business Workflow Consulting
