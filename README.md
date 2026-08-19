# 🏫 School Management System (Zoho CRM & Zoho Creator)

Submission Write-up: Data Structure, Integration & Additional Feature  
Author: Vivek Gupta  
Assignment: Zoho Developer Internship

---

## 🔗 Submission Access Links

| Resource | Access URL | Credentials / Mode |
| :--- | :--- | :--- |
| **Zoho CRM & Creator** | [https://crm.zoho.com](https://crm.zoho.com) | Click on **Sign In** and use:<br>&nbsp;&nbsp;&nbsp;&nbsp;• **Email:** `gauriii.sharma929@gmail.com`<br>&nbsp;&nbsp;&nbsp;&nbsp;• **Password:** `Recruiter_2026` |
| **Admission Webform** | https://fanciful-melomakarona-f54de3.netlify.app/ | Public Webform (Direct Submission) |

> **Note for Evaluator:**
> 1. Open `https://crm.zoho.com` in an Incognito/Private window and sign in with the credentials above.
> 2. To access the **Zoho Creator School Parent Application**, Simply navigate to Creator inside the same signed-in browser session.
---

## 📌 Architecture Overview

* **Zoho CRM (Core Operations):** Central administrative hub managing Leads (Webform), Students, Academic Hierarchy, Attendance Records, Exam Results, Fee Structures, and Fee Payments.
* **Zoho Creator (Parent Portal):** Parent-facing app with Parent Login and Student Dashboard, fetching live records from Zoho CRM via Deluge connection (`crm_connection`) with zero data duplication.
* **Deluge Automations:** Event-driven workflows for attendance health monitoring (`checkLowAttendance`) and fee collection balance rollups (`update_fee_structure_amount`).

---

## 📂 Project Documentation

* [01. Data Structure & Relationships (docs/01-data-structure.md)](./docs/01-data-structure.md)
* [02. CRM – Creator Integration (docs/02-crm-creator-integration.md)](./docs/02-crm-creator-integration.md)
* [03. Additional Feature: Low Attendance Warning (docs/03-additional-feature.md)](./docs/03-additional-feature.md)
* **Deluge Scripts:**
  * [checkLowAttendance.dg](./scripts/checkLowAttendance.dg)
  * [update_fee_structure_amount.dg](./scripts/update_fee_structure_amount.dg)
