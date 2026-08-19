# 🏫 School Management System (Zoho CRM & Zoho Creator)

Submission Write-up: Data Structure, Integration & Additional Feature  
Author: Vivek Gupta  
Assignment: Zoho Developer Internship

---

## 🔗 Submission Access Links

| Resource | Access URL / Identifier | Credentials / Mode |
| :--- | :--- | :--- |
| **Zoho CRM & Creator Login** | [https://crm.zoho.com](https://crm.zoho.com) | **Use Credentials:**<br>&nbsp;&nbsp;&nbsp;&nbsp;• **Email:** `gauriii.sharma929@gmail.com`<br>&nbsp;&nbsp;&nbsp;&nbsp;• **Password:** `Recruiter_2026`

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
