# 🏫 School Management System (Zoho CRM & Zoho Creator)

Submission Write-up: Data Structure, Integration & Additional Feature  
Author: Vivek Gupta  
Assignment: Zoho Developer Internship

---

## 🔗 Submission Access Links

| Submission Item | Access URL / Details |
| :--- | :--- |
| **Zoho CRM Implementation** | **URL:** [https://crm.zoho.com](https://crm.zoho.com)<br>**Credentials:** `your-email@example.com` / `TemporaryPassword` |
| **Zoho Creator Parent App** | [Direct Parent Portal Link](https://creatorapp.zoho.com/your-app-link) |
| **Admission Webform** | [Live Admission Webform Link](https://crm.zoho.com/your-webform-link) |

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
