# 02. CRM – Creator Integration

The parent-facing application is built in Zoho Creator and reads data live from Zoho CRM rather than storing a separate copy of student data, so there is no duplication and the parent always sees up-to-date information.

---

## Parent Identification
The Creator app has a dedicated Parent Login page with a single 'Parent Email' field. On submission, this email is matched against the Parent Email field on the Students module in CRM. Because each Student record stores its own Parent Email, a parent is always linked to, and can only ever view, their own child's data.

---

## Data Retrieval
Once the parent's email is matched to a Student, the Student Dashboard page fetches that student's data directly from CRM through a configured CRM connection (crm_connection), using:
- zoho.crm.searchRecords (to find the matching Student by Parent Email)
- zoho.crm.getRecordById (to pull related Attendance, Exam Results and Fee records for that specific student)

No student, attendance, exam or fee data is copied into Creator — it is fetched on demand, so CRM remains the single source of truth and any update made in CRM is immediately reflected in the parent app.

---

## Pages in the Creator App
- Parent Login — captures and validates the Parent Email against the Students module.
- Student Dashboard — displays the matched student's Name, Class, Attendance %, Exam Results and Fee Status, fetched live from CRM.
