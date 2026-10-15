# Business Analytics & Automation

**Case Study Portfolio | SQL Analytics · Business Insights · Workflow Automation · Solution Design**

This portfolio presents two independent case studies focused on analytical problem-solving and operational automation. The first applies SQL and statistical analysis to payment transaction data, while the second proposes a browser-based agent for automating multi-item e-commerce returns.

Each case study includes its original requirements, solution approach, key findings or design decisions, and supporting documentation.

---

## Portfolio Overview

| # | Case Study | Focus | Primary Deliverable |
|---|---|---|---|
| 01 | Transaction Data Analysis | SQL, statistics, user cohorts | Analytical report with queries, results, and visualisations |
| 02 | Returns Automation Agent | Browser automation, workflow design | Technical design covering architecture and exception handling |

---

## 01. Transaction Data Analysis

**Objective:** Analyse payment transactions to answer five business questions involving transaction rankings, payment-channel volumes, amount distributions, monthly user cohorts, and user-level net amounts.

**Dataset:** 501 transactions across 10 users, covering January–July 2020.

### Analytical Scope

- Identify the seventh-highest IMPS debit amount.
- Calculate transaction volumes across UPI, IMPS, RTGS, and NEFT.
- Examine transaction amount distributions using a bell curve, box plot, and statistical summary.
- Build monthly cohorts of users performing debit transactions.
- Identify the top 10 percentile of users by net amount, calculated as total debit minus total credit.

### Approach

The solution describes extracting transaction records from PDF documents, preparing the data in SQLite, and applying SQL filtering, sorting, and aggregation. User-month activity supports cohort analysis, while statistical summaries and visualisations help interpret transaction distributions.

### Key Findings

| Metric | Reported Result |
|---|---:|
| Seventh-highest IMPS debit | ₹9,525 |
| IMPS transactions | 272 |
| UPI transactions | 86 |
| NEFT transactions | 33 |
| RTGS transactions | 21 |
| IFT transactions | 89 |

IFT transactions are excluded from the four-channel count requested in the assignment.

**Data assumption:** The source dataset does not contain a field explicitly named `load amount`. Its intended interpretation should be verified against the assignment requirements. The figures above are reported from the supplied case study and have not been independently recomputed for this README.

### Deliverables

| File | Description |
|---|---|
| [Assignment Questions](01_Transaction_Data_Analysis/source-material/Transaction-Analysis-Questions.pdf) | Original analytical requirements |
| [Transactions Dataset](01_Transaction_Data_Analysis/source-material/Transactions-Dataset.pdf) | Source transaction records |
| [Analysis Report — PDF](01_Transaction_Data_Analysis/documentation/Transaction_Data_Analysis.pdf) | SQL queries, result tables, charts, and analysis |
| [Analysis Report — HTML](01_Transaction_Data_Analysis/documentation/Transaction_Analysis_Report.html) | Styled, browser-viewable analytical report |

### Key Takeaway

Applying SQL and statistical analysis to financial transaction data to answer business questions, evaluate user activity, and document data assumptions.

---

## 02. Returns Automation Agent

**Objective:** Design a browser-based agent that reads pending return tasks from Excel, initiates returns on Amazon and Flipkart, and records the outcome for each product or SKU.

The central challenge is handling item-level differences in return eligibility, return IDs, and platform workflows, including batch and sequential processing.

### Proposed Architecture

| Component | Responsibility |
|---|---|
| Excel / Task Store | Maintains pending tasks and processing outcomes |
| Orchestrator | Coordinates workflows and item-level execution |
| Platform Adapters | Handle platform-specific return interactions |
| Browser Engine | Supports browser automation using Playwright |
| Secrets Manager | Handles runtime credentials and OTP workflows |
| Logging / Audit | Records actions, timestamps, outcomes, and failures |

### Workflow and Reliability

The proposed workflow reads pending tasks, checks return eligibility, selects the relevant platform workflow, captures return details, and updates the corresponding Excel row.

Key design considerations:

- **Item-level processing:** Process each SKU independently.
- **Fault isolation:** Continue processing eligible items when another item fails.
- **Exception handling:** Flag ineligible items and unresolved failures for human review.
- **Traceability:** Record return IDs, statuses, refund amounts, and execution outcomes.
- **Controlled retries:** Handle transient failures without blindly repeating actions.
- **Credential security:** Keep credentials separate from spreadsheets and source code.
- **Responsible automation:** Respect platform access controls and do not bypass CAPTCHA or anti-bot protections.

### Deliverables

| File | Description |
|---|---|
| [Assignment Brief](02_Returns_Automation_Agent/source-material/Returns-Automation-Assignment-Brief.pdf) | Original objectives and functional requirements |
| [Technical Design — PDF](02_Returns_Automation_Agent/documentation/Returns-Automation-Agent-Technical-Design.pdf) | Proposed architecture, workflow, Excel schema, and failure handling |

### Implementation Status

This is a **technical design proposal**, not a verified working automation system. The supplied materials contain the assignment brief and design document, but no runnable agent source code, dependency manifest, or execution and testing report.

### Key Takeaway

Designing reliable operational workflows through modular architecture, item-level state tracking, exception handling, and auditability.

---

## Methodology at a Glance

| Dimension | Transaction Data Analysis | Returns Automation Agent |
|---|---|---|
| Problem Type | Analytical | Operational and technical |
| Primary Method | SQL, aggregation, cohort analysis, statistical visualisation | Workflow orchestration, platform adapters, state tracking |
| Main Output | Analytical case study | Technical design document |
| Validation Focus | Query logic, data interpretation, reported results | Item-level outcomes, failure handling, traceability |

Both assignments follow a structured problem-solving approach: define requirements, develop a solution, document key decisions, and identify limitations.

---

## Tools & Technologies

| Assignment | Technologies |
|---|---|
| Transaction Data Analysis | SQL, SQLite, Python, PyMuPDF |
| Returns Automation Agent | Excel, `openpyxl`, Playwright |

The technologies listed for returns automation describe the proposed architecture and do not imply that a runnable implementation is included.

---

## Reviewing the Deliverables

**Transaction Data Analysis**

1. Review the original assignment questions and source dataset.
2. Open the PDF report for the analytical narrative or the HTML report for browser-based viewing.
3. Reproducing the analysis requires preparing the source data and implementing the SQL workflow. A standalone SQL script is not included in the supplied package.

**Returns Automation Agent**

1. Review the assignment brief to understand the functional requirements.
2. Open the technical design to examine the architecture, processing workflow, and proposed Excel schema.
3. Implementation, platform-specific validation, and testing are required before using the proposed design for actual returns.

---

## Conclusion

These case studies demonstrate two complementary approaches to business problem-solving: extracting insights from historical transaction data and designing a reliable workflow for operational automation.

Together, they showcase analytical thinking, structured solution design, data interpretation, exception handling, and technical documentation while distinguishing reported findings from proposed functionality.

---
