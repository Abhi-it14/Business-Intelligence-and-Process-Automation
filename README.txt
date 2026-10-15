# Business Analytics & Automation | Case Study Portfolio

**SQL Analytics · Business Insights · Workflow Automation · Solution Design**

This repository brings together two independent assignment case studies focused on solving practical analytical and operational problems. The first explores payment transaction data using SQL and statistical analysis, while the second proposes a browser-based agent for automating multi-item e-commerce returns.

Each assignment includes its original problem statement and corresponding solution documents, organised for easy review.

---

## Portfolio Overview

| Assignment | Focus | Primary Deliverable |
|---|---|---|
| **01. Transaction Data Analysis** | SQL queries, statistical analysis, and user cohort analysis | Analytical case study with queries, results, and visualisations |
| **02. Returns Automation Agent** | Browser automation, workflow design, and exception handling | Technical design covering architecture and processing workflows |

---

## 01. Transaction Data Analysis

### Objective

Analyse payment transactions to answer five questions involving transaction ranking, payment-channel volumes, amount distributions, monthly user cohorts, and user-level net amounts.

The supplied case study describes **501 transactions across 10 users**, covering January–July 2020.

### Problem Statement

The assignment requires:

1. Finding the seventh-highest IMPS debit amount.
2. Calculating transaction counts for UPI, IMPS, RTGS, and NEFT.
3. Creating a bell curve and box plot with a statistical summary.
4. Building monthly cohorts of users performing debit transactions.
5. Identifying the top 10 percentile of users by net amount, defined as total debit minus total credit.

### Approach and Key Findings

The solution describes extracting transaction records from PDF, preparing the data in SQLite, and applying SQL filtering, sorting, and aggregation. User-month activity is analysed for cohorts, while statistical summaries and visualisations support the amount-distribution analysis.

| Analysis | Reported Result |
|---|---|
| Seventh-highest IMPS debit | ₹9,525 |
| IMPS transactions | 272 |
| UPI transactions | 86 |
| NEFT transactions | 33 |
| RTGS transactions | 21 |

The dataset also contains 89 IFT transactions, which are excluded from the four-channel count requested in the brief.

**Important assumption:** The dataset does not contain a field explicitly named `load amount`. The interpretation used for this analysis should be checked against the assignment's intended definition. The results above are reported from the supplied case study and have not been independently recomputed for this README.

### Deliverables

| File | Description |
|---|---|
| [Assignment Questions](01_Transaction_Data_Analysis/source-material/Transaction-Analysis-Questions.pdf) | Original analytical requirements |
| [Transactions Dataset](01_Transaction_Data_Analysis/source-material/Transactions-Dataset.pdf) | Source transaction records |
| [Analysis Report — PDF](01_Transaction_Data_Analysis/documentation/Transaction_Data_Analysis.pdf) | Case study with SQL queries, result tables, charts, and analysis |
| [Analysis Report — HTML](01_Transaction_Data_Analysis/documentation/Transaction_Analysis_Report.html) | Styled, browser-viewable analytical report |

### Key Takeaway

This assignment demonstrates the application of SQL and statistical analysis to transaction data, with a focus on answering defined business questions, understanding user activity, and documenting data assumptions.

---

## 02. Returns Automation Agent

### Objective

Design a browser-based agent that reads pending return tasks from Excel, initiates returns on Amazon and Flipkart, and records the outcome for every product or SKU.

The key challenge is that products within the same order may have different return windows and return IDs, while platforms may follow batch or sequential return workflows.

### Proposed Solution and Architecture

The technical design outlines six components:

| Component | Responsibility |
|---|---|
| **Excel / Task Store** | Maintains pending tasks and final outcomes |
| **Orchestrator** | Coordinates workflows and item-level processing |
| **Platform Adapters** | Handle platform-specific return interactions |
| **Browser Engine** | Uses Playwright for browser automation |
| **Secrets Manager** | Manages runtime credentials and OTP handling |
| **Logging / Audit** | Records actions, timestamps, results, and failures |

### Workflow and Reliability

The proposed workflow reads pending tasks, checks return eligibility, selects the appropriate platform workflow, captures the return ID/status/refund amount, and writes the outcome back to the corresponding Excel row.

Key design considerations include:

- Processing each SKU independently.
- Continuing with eligible items when another item fails.
- Recording ineligible items and unresolved failures for human review.
- Writing results back at the line-item level.
- Using appropriate retries and maintaining an audit trail.
- Keeping credentials separate from spreadsheets and source code.
- Respecting platform access controls rather than attempting to bypass CAPTCHA or anti-bot protections.

### Deliverables

| File | Description |
|---|---|
| [Assignment Brief](02_Returns_Automation_Agent/source-material/Returns-Automation-Assignment-Brief.pdf) | Original objectives and functional requirements |
| [Technical Design — PDF](02_Returns_Automation_Agent/documentation/Returns-Automation-Agent-Technical-Design.pdf) | Proposed architecture, workflow, Excel schema, and failure handling |

### Implementation Status

This is a **technical design proposal**, not a verified working automation system. The supplied materials contain the assignment brief and design document, but no runnable agent source code, dependency manifest, or execution/test report.

### Key Takeaway

The assignment focuses on designing a reliable operational workflow through component-based architecture, item-level tracking, exception handling, and auditability.

---

## Methodology and Problem-Solving Approach

| Dimension | Transaction Data Analysis | Returns Automation Agent |
|---|---|---|
| Problem type | Analytical | Operational and technical |
| Primary method | SQL queries, aggregation, cohort analysis, and statistical visualisation | Workflow orchestration, platform adapters, state tracking, and exception handling |
| Main output | Analytical case study | Technical design document |
| Validation focus | Query logic, data interpretation, and reported results | Item-level outcomes, failure handling, and traceability |

The assignments remain distinct: one focuses on extracting insights from historical transaction data, while the other specifies a proposed system for managing operational tasks.

---

## Tools and Technologies

Only tools explicitly referenced in the supplied materials are listed.

| Assignment | Technologies |
|---|---|
| Transaction Data Analysis | SQL, SQLite, Python, PyMuPDF |
| Returns Automation Agent | Excel, `openpyxl`, Playwright |

The returns automation technologies describe the proposed architecture and do not imply that a runnable implementation is included.

---

## Accessing the Deliverables

**Transaction Data Analysis**
- Open the PDF case study in a PDF reader or the HTML report in a modern browser.
- Refer to the original questions and dataset for the source requirements.
- Reproducing the analysis requires preparing the source data and implementing the SQL workflow; a standalone SQL script is not included in the supplied package.

**Returns Automation Agent**
- Open the technical design PDF to review the architecture, workflow, and proposed Excel schema.
- Refer to the assignment brief for the original requirements.
- Implementation and testing are required before using the proposed design for actual returns.

---

## Conclusion

This portfolio presents two complementary case studies in **data analysis and operational solution design**. The transaction analysis assignment applies SQL and statistical techniques to payment data, while the returns automation assignment proposes a structured approach to multi-item return processing.

Together, they document the original requirements, solution approaches, key deliverables, and implementation limitations in a format suitable for professional review.
