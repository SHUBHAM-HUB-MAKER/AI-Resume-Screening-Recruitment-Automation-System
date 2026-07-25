An AI-powered recruitment automation system that processes candidate applications, evaluates resumes using AI, validates candidate data, tracks approval decisions, stores generated documents, and automates company notifications and daily reporting.

The system connects a React frontend, Express.js backend, n8n workflow automation, AI-based resume evaluation, JavaScript data processing, Google Sheets, Google Drive, Gmail, and Slack.

---

## Overview

Candidates submit their application details and resume through a React frontend.

The application is sent to an Express.js backend, which forwards the data to an n8n webhook.

The automation workflow then processes the resume, evaluates the candidate using an AI Agent, structures the AI output using JavaScript, validates the application, stores the candidate record according to the result, and handles approval notifications and reporting.

---

## React Frontend

The React frontend provides the candidate-facing application interface.

Candidates can:

- View the recruitment application page
- Enter their application details
- Upload their resume
- Submit their application

### Application Flow

**Hiring Page → Application Form → Application Submission**

<div align="center">

<img src="./Front" alt="System Workflow" width="100%">


<h1>↓</h1>
<img src="./Form" alt="System Workflow" width="100%">


<h1>↓</h1>
<img src="./Submission" alt="System Workflow" width="100%">

</div>

<!-- Add the real frontend screenshots here -->

---

## System Architecture

```text
React Frontend
      ↓
Express.js Backend
      ↓
n8n Webhook
      ↓
Resume Processing
      ↓
AI Agent
      ↓
JavaScript Data Processing
      ↓
Resume Validation
      │
      ├── Invalid → Invalid Google Sheets Tab → Workflow Stops
      │
      └── Valid
             ↓
        PDF Generation
             ↓
        Google Drive
             ↓
      Approval Decision
          │
          ├── Approved
          │      ↓
          │  Approved Sheet
          │      ↓
          │  Gmail + Slack
          │
          └── Not Approved
                 ↓
             Not Approved Sheet
```

---

## Workflow

### 1. Candidate Application

Candidates submit their application details and resume through the React frontend.

The application data is sent to the Express.js backend.

```text
Candidate
    ↓
React Frontend
    ↓
Application Details + Resume
```

---

### 2. Express.js Backend

The Express.js backend receives the application data from the React frontend and forwards it to the n8n webhook.

```text
React Frontend
      ↓
Express.js Backend
      ↓
n8n Webhook
```

---

### 3. Resume Processing

The n8n workflow receives the candidate application and processes the submitted resume.

The resume content is extracted and prepared for AI-based evaluation.

---

### 4. AI Resume Evaluation

The AI Agent evaluates the candidate information and resume according to the screening criteria configured for the workflow.

The AI output may include:

- Candidate information
- Qualification
- Subject knowledge
- Relevant experience
- Teaching or training experience
- Communication
- Resume quality
- Form and resume consistency
- Skills
- Candidate score
- Final decision
- Reason for decision

---

### 5. JavaScript Data Processing

The AI Agent response is processed using JavaScript.

The JavaScript processing step:

- Processes the AI response
- Structures candidate information
- Normalizes the output
- Prepares consistent data for later workflow steps
- Determines the next processing path

---

## Resume Validation

After the AI output is processed, the workflow determines whether the submitted resume is valid.

### Invalid Resume

If the resume is invalid:

- Candidate data is stored in the `Invalid` tab of Google Sheets.
- The workflow stops for that candidate.

```text
Invalid Resume
      ↓
Google Sheets
      ↓
Invalid Tab
      ↓
Workflow Stops
```

### Valid Resume

If the resume is valid:

- The candidate continues through the workflow.
- A PDF document is generated.
- The PDF is stored in Google Drive.
- The Google Drive link is stored with the candidate record.
- The candidate continues to the approval decision stage.

```text
Valid Resume
      ↓
PDF Generation
      ↓
Google Drive
      ↓
Resume Drive Link
      ↓
Approval Decision
```

---

## Candidate Approval Processing

After a valid candidate's resume PDF is stored, the candidate is processed according to the approval decision.

### Approved Candidate

For approved candidates:

- Candidate information is stored in the `Approved` tab of Google Sheets.
- The Google Drive resume link is stored with the candidate record.
- An email is sent to the client/company.
- A Slack notification is sent to the company.

```text
Approved Candidate
        ↓
Approved Google Sheets Tab
        ↓
Google Drive Resume Link
        ↓
Email Notification
        ↓
Slack Notification
```

### Not Approved Candidate

For candidates who are not approved:

- Candidate information is stored in the `Not Approved` tab of Google Sheets.
- The Google Drive resume link is stored with the candidate record.

```text
Not Approved Candidate
        ↓
Not Approved Google Sheets Tab
        ↓
Google Drive Resume Link
```

---

## Email Notification

When a candidate is approved, the workflow sends the candidate application information to the client/company by email.

This removes the need for the information to be manually forwarded after the approval decision.

---

## Slack Notification

After an approved application is processed, the company receives a Slack notification about the new candidate application.

This provides an additional internal notification channel for the recruitment workflow.

---

## Daily Approved Candidate Summary

A separate scheduled workflow runs daily to process approved candidates from the previous day.

The workflow:

1. Checks the current time.
2. Identifies approved candidates from the previous day.
3. Generates a summary.
4. Sends the summary to the company by email.

```text
Scheduled Workflow
        ↓
Time Check
        ↓
Previous Day's Approved Candidates
        ↓
Summary Generation
        ↓
Email Sent to Company
```

---

## Technology Stack

### Frontend

- React.js
- JavaScript
- HTML
- CSS

### Backend

- Node.js
- Express.js
- REST APIs

### Automation

- n8n
- Webhooks
- JavaScript Code Nodes
- Workflow Automation

### AI

- AI Agents
- Gemini AI
- LLM Integration
- Prompt Engineering

### Google Services

- Google Sheets
- Google Drive
- Gmail
- Google Cloud Console

### Communication

- Slack

### Tools

- PDF Automation
- Postman
- Git
- GitHub

---

## Key Features

- React-based candidate application interface
- Resume upload and application data collection
- Express.js backend integration
- n8n webhook integration
- Automated resume processing
- AI-based resume evaluation
- JavaScript-based AI output processing
- Resume validation
- Invalid resume handling
- Automated PDF generation
- Google Drive document storage
- Google Sheets candidate tracking
- Approved candidate tracking
- Not Approved candidate tracking
- Resume Drive link storage
- Automated email notifications
- Slack notifications
- Daily approved-candidate summary emails

---

## Project Objective

The objective of this project is to automate repetitive recruitment workflow tasks using AI and workflow automation.

The system connects candidate application submission with AI-based resume evaluation, validation, document storage, candidate tracking, approval processing, company notifications, and daily reporting.

---

## Author

**Shubham Gupta**

**AI Automation Engineer | AI Agents | n8n | Full-Stack Development**
