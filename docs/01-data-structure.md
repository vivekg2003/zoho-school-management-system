# 01. Data Structure and Relationships

The system is built entirely in Zoho CRM using interconnected modules connected through lookup fields so that data is captured once and referenced everywhere it is needed, avoiding duplication.

---

## Module Breakdown & Relationships

| Module | Purpose | Key Relationships |
| :--- | :--- | :--- |
| **Leads** | Captures admission enquiries submitted via the public Webform. | Converted into a Students record on admission confirmation. |
| **Students** | Master record for each enrolled student. Student ID is generated automatically using Zoho CRM's built-in Auto-Number field (`STU-0001`), ensuring every student has a guaranteed-unique identifier with no manual entry or duplication risk. Also holds Name, Class, Section, Parent Email, etc. | Central hub — linked to from Attendance Records, Exam Results, Fee Structures and Fee Payments. |
| **Academic Years** | Defines each academic session (e.g. 2025-26). | Referenced by Classes and Fee Structures to scope records to a session. |
| **Classes** | Defines each class/grade. | Linked to Academic Year; parent to Sections. |
| **Sections** | Defines sections within a class (e.g. Class 8 - A). | Linked to Classes; Students belong to a Section. |
| **Subjects** | Master list of subjects taught. | Linked to Exam Results and to Teachers. |
| **Teachers** | Teacher master data. | Linked to Subjects and Classes taught. |
| **Attendance Records** | Daily attendance entry per student (Present/Absent). | Lookup to Students; a Deluge workflow prevents duplicate entries for the same student/date and recalculates Attendance %. |
| **Exam Results** | Marks obtained per student per subject per exam. | Lookups to Students and Subjects; Percentage is a formula field; a validation rule blocks Marks Obtained > Total Marks. |
| **Fee Structures** | Total fees and payment status per student per academic year. | Lookups to Students and Academic Years; Outstanding Amount and Payment Status are formula fields, kept in sync by Fee Payments. |
| **Fee Payments** | Individual payment transactions. | Lookups to Student and Fee Structure; a workflow (`update_fee_structure_amount`) sums payments into the Fee Structure's Amount Paid on every Create/Edit. |

---

## Student Identification
Every Student record is assigned a unique Student ID automatically at creation, using Zoho CRM's built-in Auto-Number field (format `STU-0001`, incrementing with each new admission). This removes any dependency on manual entry, guarantees uniqueness across the system, and gives every downstream module (Attendance, Exam Results, Fee Structures, Fee Payments, and the Creator parent app) a single, reliable key to reference the student by.

---

## Relationship Flow
1. A public Webform submission creates a record in **Leads**; once admission is confirmed, the Lead is converted into a **Students** record, which receives its Auto-Number Student ID at that point.
2. **Students** is the central module. `Academic Years` -> `Classes` -> `Sections` form the academic hierarchy that a Student belongs to.
3. **Attendance Records**, **Exam Results**, **Fee Structures**, and **Fee Payments** all hold a lookup back to **Students**, so a single student's complete academic, attendance and fee history can be retrieved from one place.
4. **Fee Payments** additionally looks up to **Fee Structures**, and a Deluge workflow keeps the Fee Structure's `Amount Paid`, `Outstanding Amount`, and `Payment Status` automatically in sync whenever a payment is created or edited.
5. This lookup-based design means no data is duplicated across modules — every module stores only what is unique to it and references shared data through relationships.
