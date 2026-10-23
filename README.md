# 🚀 Smart Lead Management & Routing System

### A No-Code Lead Automation Workflow Built with Make.com

![Make.com](https://img.shields.io/badge/Automation-Make.com-purple)
![Google Sheets](https://img.shields.io/badge/Data-Google%20Sheets-green)
![Gmail](https://img.shields.io/badge/Notifications-Gmail-red)
![Google Calendar](https://img.shields.io/badge/Scheduling-Google%20Calendar-blue)
![HTTP API](https://img.shields.io/badge/Integration-HTTP%20API-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## 📌 Project Overview

The **Smart Lead Management & Routing System** is a no-code automation workflow built with **Make.com** to automate the journey of a lead from initial submission to follow-up.

The system captures leads submitted through a Google Form, validates the information, enriches the lead's email domain using an external DNS API, calculates a rule-based lead score, routes the lead to either the Sales or Nurture team, stores the result, sends an email notification, schedules a follow-up, and logs the activity.

The project was developed as part of an **Advanced Make.com Automation Assessment** and was designed as a practical business automation workflow rather than a simple demonstration of individual Make.com modules.


---

# 🎯 Project Goal

The goal was to design an automated lead-processing system that reduces repetitive manual work and ensures that incoming leads are consistently:

- Captured
- Validated
- Enriched
- Processed
- Scored
- Routed
- Stored
- Communicated to staff
- Scheduled for follow-up
- Logged for traceability


---

# 🏢 Business Problem

When leads are processed manually, teams may need to:

1. Review new submissions
2. Check whether information is complete
3. Evaluate lead quality
4. Decide which team should handle the lead
5. Send internal notifications
6. Schedule follow-ups
7. Record what happened

This creates repetitive administrative work and can result in inconsistent processing.

This automation addresses that workflow by connecting these activities into a single automated pipeline.

---

# 🔄 Workflow Architecture

```text
                    GOOGLE FORM
                         │
                         ▼
                  GOOGLE SHEETS
                         │
                         ▼
             ┌──────────────────────┐
             │   WATCH NEW ROWS     │
             │     Lead Capture     │
             └──────────┬───────────┘
                        │
                        ▼
                LEAD VALIDATION
                        │
                        ▼
              INITIALIZE VARIABLES
                        │
                        ▼
              EMAIL DOMAIN / MX
                  ENRICHMENT
                        │
                        ▼
                LEAD PROCESSING
                        │
                        ▼
             LEAD SCORE COMPONENTS
                        │
                        ▼
              CALCULATE LEAD SCORE
                        │
                        ▼
                   ┌─────────┐
                   │ ROUTER  │
                   └────┬────┘
                        │
              ┌─────────┴─────────┐
              ▼                   ▼
       SALES QUALIFIED          NURTURE
              │                   │
              ▼                   ▼
        LEAD RESULTS         LEAD RESULTS
              │                   │
              ▼                   ▼
          GMAIL ALERT         GMAIL ALERT
              │                   │
              ▼                   ▼
       CALENDAR FOLLOW-UP   CALENDAR FOLLOW-UP
              │                   │
              ▼                   ▼
         ACTIVITY LOG        ACTIVITY LOG
 

```
---  

# 🧩 Key Features

1. Automated Lead Capture

New Google Form submissions are automatically detected through Google Sheets.

2. Lead Validation

Required lead fields are checked before processing continues.

3. Email Domain Enrichment

The system extracts the email domain and queries Google's DNS-over-HTTPS API for MX records.

4. Rule-Based Lead Scoring

Leads receive scores based on:

- Estimated budget
- Company size
- Area of interest

5. Intelligent Routing

The router sends leads to:

- Sales — score ≥ 60
- Nurture — score < 60

6. Automated Notifications

Gmail sends an internal notification based on the lead route.

7. Automated Follow-Up

Google Calendar creates a follow-up event.

8. Activity Logging

Every processed lead is recorded in an Activity Log.

9. Error Handling

The external API enrichment step includes a Resume error handler.

---

# 📊 Lead Scoring Model

The scoring model uses three components.

**Budget Score**

| Estimated Budget | Score |
| ---------------- | ----: |
| $5,000–$9,999    |    30 |
| $1,000–$4,999    |    20 |
| Other            |    10 |

**Company Size Score**

| Company Size | Score |
| ------------ | ----: |
| 100–249      |    25 |
| 50–99        |    20 |
| Other        |    15 |

**Interest Score**

| Area of Interest      | Score |
| --------------------- | ----: |
| AI / Machine Learning |    30 |
| Data Analytics        |    25 |
| Software Development  |    20 |
| Other                 |    10 |

**Routing Logic**

IF Lead Score >= 60
        ↓
      SALES

IF Lead Score < 60
        ↓
     NURTURE

Example

Budget Score       = 30
Company Size Score = 25
Interest Score     = 30
-------------------------
Total Score        = 85

A score of 85 is therefore routed to the Sales branch.

---

# 🛠️ Technology Stack

| Technology      | Role                                  |
| --------------- | ------------------------------------- |
| Make.com        | Automation and workflow orchestration |
| Google Forms    | Lead intake                           |
| Google Sheets   | Lead storage and logging              |
| Gmail           | Staff notifications                   |
| Google Calendar | Follow-up scheduling                  |
| HTTP API        | External enrichment                   |
| Google DNS API  | MX record lookup                      |
| Make Tools      | Variables and data transformation     |


---


# 🧱 Make.com Scenario Modules

The scenario contains the following major components:

**Lead Capture**
- Google Sheets — Watch New Rows

**Validation**
- Filter — Lead Validation


**Data Processing**
- Tools — Set Variables
- HTTP — Make a Request
- Tools — Set Variables
- Tools — Set Variables
- Tools — Set Variables

**Routing**
- Router
- Sales Qualified filter
- Nurture filter

**Sales Branch**
- Google Sheets — Add a Row
- Gmail — Send an Email
- Google Calendar — Create an Event
- Google Sheets — Add a Row

**Nurture Branch**
- Google Sheets — Add a Row
- Gmail — Send an Email
- Google Calendar — Create an Event
- Google Sheets — Add a Row

**Error Handling**
- HTTP Resume Error Handler

---

# 🗂️ Repository Structure
```
smart-lead-management-routing/
│
├── README.md
│
├── docs/
│   └── technical-documentation.pdf
│
├── screenshots/
│   ├── Google Form.png
│   ├── Form Responses sheet.png
│   ├── Lead Results sheet.png
│   ├── Activity Log sheet.png
│   └── Complete Make.com scenario.png
│
├── demo/
│   └── drive.google.com
│
└── LICENSE

```

---
# 📸 Project Screenshots

### 1. Complete Make.com Workflow

The complete end-to-end automation built in Make.com.

![Complete Make.com Workflow](./complete%20Make.com%20scenario.png)

---

### 2. Smart Lead Intake Form

The Google Form used to capture incoming lead information.

![Google Form](./Google%20Form.png)

---

### 3. Form Responses

The Google Sheets worksheet containing the submitted lead information.

![Form Responses](./Form%20Responses%20sheet.png)

---

### 4. Lead Results

Processed leads are stored with their calculated score, route, and status.

![Lead Results](./Lead%20Results%20sheet.png)

---

### 5. Activity Log

Automated routing outcomes and follow-up actions are recorded in the Activity Log.

![Activity Log](./Activity%20Log%20sheet.png)


---

# 🎥 Project Demo

**4-Minute Demonstration**

The demonstration shows the complete workflow from lead capture through routing, notification, scheduling, and logging.

## Demo Video:
[https://drive.google.com/file/d/19HOx3IT-N76256s9SL4ssVv7nLc9idMR/view?usp=sharing]

**What the demo covers**
- Lead submission
- Google Sheets trigger
- Validation
- API enrichment
- Lead scoring
- Sales/Nurture routing
- Email notification
- Calendar scheduling
- Activity logging
- Successful execution

## 📚 Technical Documentation

Detailed implementation documentation is available here:

👉 Technical Documentation

The technical documentation covers:

- System architecture
- Module configuration
- Data flow
- Validation logic
- API integration
- Scoring logic
- Router configuration
- Google Sheets structure
- Gmail notifications
- Calendar scheduling
- Error handling
- Testing
- Limitations
- Future improvements

---

# 🧪 Testing & Validation

The workflow was tested using both routing paths.

**Nurture Test**

A test lead generated a score of:
35

Result:

Nurture

The Nurture branch successfully executed the required downstream actions.

**Sales Test**

A test lead generated a score of:

85

Result:

Sales

The Sales branch successfully executed:

Lead Results storage
Gmail notification
Calendar follow-up
Activity Log entry

---

# ⚠️ Challenges Encountered

Several implementation challenges were encountered during development.

1. **Webhook vs Google Forms**

The initial approach considered using a Make Custom Webhook.

However, Google Forms does not directly send arbitrary POST requests to a Make webhook.

Solution

The workflow was redesigned around:

```
Google Form
↓
Google Sheets
↓
Watch New Rows

```
This also satisfied the assessment requirement for an app-based trigger.

2. **Email Domain Extraction** 

The initial email-domain extraction formula produced an error.

The formula was revised to extract the last portion of the email address after @.

Result

user@gmail.com
       ↓
gmail.com

3. **HTTP API Request Error**

The DNS enrichment module initially returned an HTTP 400 error because the email-domain expression was not being passed correctly.

After correcting the expression, the API returned:

Status Code: 200
Status: 0

and returned valid MX records.

4. **Lead Scoring Logic**

The initial scoring formulas returned default scores instead of the expected values.

The issue was traced to the way the comparison expressions were entered.

After correcting the formulas, the scoring worked as intended.

Example:

Budget       = 30
Company Size = 25
Interest     = 30

Total        = 85

5. **Sales Routing**

During testing, the Sales route initially did not execute because the calculated score was below the Sales threshold.

After correcting the scoring logic, a score of 85 successfully passed:

Lead Score >= 60

and entered the Sales branch.

6. **Google Calendar Authorization**

The Google Calendar module initially returned an authentication/permission error.

The Google connection permissions were updated, after which the Calendar module was able to create follow-up events successfully.

---

# 💡 Lessons Learned

This project reinforced several practical automation concepts:

- A workflow should be designed around the actual capabilities of the connected applications.
- Data validation should happen before downstream processing.
- External API calls should have error handling.
- Complex workflows are easier to maintain when data is transformed into reusable variables.
- Conditional routing allows one automation to handle multiple business outcomes.
- Testing both successful and alternative branches is essential.
- Logging provides visibility into what happened after an automation runs.
- Authentication and permission scopes are an important part of integrating external services.

---


# 🔐 Data & Security Considerations

The project uses test lead data for demonstration purposes.

Sensitive credentials, API keys, private webhook URLs, and personal authentication information should not be committed to the repository.

The repository should contain configuration examples or documentation rather than private credentials.


---

# 🚀 Future Improvements

The current system provides the core lead-processing workflow. Future versions could include:

**CRM Integration**

Connect the workflow to a CRM such as HubSpot or Salesforce.

**Advanced Lead Enrichment**

Add external company-data services to obtain:
- Industry
- Company revenue
- Employee count
- Company location
- Website information


**Duplicate Detection**

Prevent the same lead from being processed multiple times.


**Advanced Scoring**

Introduce additional factors such as:

- Lead engagement
- Previous interactions
- Company industry
- Geographic location
- Website activity


**Slack / Microsoft Teams Alerts**

Add real-time team notifications in addition to email.


**Analytics Dashboard**

Build a dashboard showing:

- Total leads
- Sales-qualified leads
- Nurture leads
- Average lead score
- Conversion trends
- Lead sources


**Improved Error Logging**

Create a dedicated error log containing:

- Module
- Timestamp
- Error message
- Lead identifier
- Recovery action


**CRM Follow-Up**

Automatically create tasks or deals in a CRM based on the lead route.

---

# 📈 Possible Future Architecture

```
Lead Source
     ↓
Validation
     ↓
Deduplication
     ↓
Company Enrichment
     ↓
Lead Scoring
     ↓
AI-Assisted Classification
     ↓
Router
 ┌───┴────┐
Sales   Nurture
  ↓        ↓
 CRM      CRM
  ↓        ↓
Notification
  ↓
Follow-up
  ↓
Analytics Dashboard`

```
---

# 🎓 Assessment Requirements Demonstrated

| Requirement           | Implementation                 |
| --------------------- | ------------------------------ |
| Trigger               | Google Sheets — Watch New Rows |
| Router                | Sales / Nurture Router         |
| At least two branches | Sales + Nurture                |
| Data transformation   | Make Tools — Set Variables     |
| External integration  | Google DNS API                 |
| Logging system        | Activity Log                   |
| Error handling        | HTTP Resume handler            |
| Tool modules          | Make Tools                     |
| Automated scoring     | Rule-based scoring system      |
| Notifications         | Gmail                          |
| Scheduling            | Google Calendar                |
| Data storage          | Google Sheets                  |

---

# 👩🏽‍💻 About the Author

**Sylvia O. Onwuanabile**

**Medical Laboratory Scientist | Data Analyst/Data Scientist | Computational Biology & Drug Discovery**

I am a Medical Laboratory Scientist with professional experience across clinical laboratory practice and a growing focus on data science, computational biology, bioinformatics, and technology-driven healthcare solutions.

My interests sit at the intersection of:

🧪 Medical Laboratory Science
💻 Data Analytics & Data Science
🧬 Computational Biology & Bioinformatics
🔬 Research
🤖 Automation & AI-enabled workflows
💊 Computational Drug Discovery

I am particularly interested in using technology, data, and computational approaches to improve healthcare and scientific workflows.

**Connect with me**

LinkedIn:
[https://www.linkedin.com/in/sylvia-onwuanabile-153b39261]

GitHub:
[https://github.com/Onwuanabile-Sylvia]

---

# 🙏🏽 Acknowledgements

This project was developed as part of an Advanced Make.com Automation Assessment.

Special appreciation to the program, mentors, and learning community that provided the framework and requirements for developing this automation project.

---

# ⭐ Project Status

Status: Completed

The core automation workflow has been implemented and tested across both Sales and Nurture routing paths.

---

# 📄 License

This project is intended primarily as a portfolio and educational project.

Add your preferred license here if you decide to license the repository.

---

# ⭐ If you found this project useful

Feel free to explore the workflow, documentation, and implementation details.