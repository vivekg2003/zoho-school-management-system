# 03. Additional Feature: Low Attendance Warning

## 1. Problem Identified
Attendance is tracked as individual daily records, but neither staff nor parents had a direct, at-a-glance way to know when a specific student's overall attendance had dropped to a concerning level[cite: 3]. Without automation, identifying this would require someone to manually pull and calculate attendance percentages from raw Attendance Records — a slow, error-prone, and easily overlooked process, especially as the number of students grows[cite: 3].

---

## 2. Why This Feature Was Selected
Low attendance is one of the most common and earliest indicators of a student needing academic follow-up, so surfacing it automatically has clear, immediate value for the school[cite: 3]. It also builds naturally on data the system already captures (Attendance Records), requires no new data entry from staff, and directly benefits the parent-facing Creator app, which already displays attendance to parents — making it a high-value, low-friction addition[cite: 3].

---

## 3. How It Was Implemented
- Two new fields were added to the Students module: Attendance_Percentage (Number) and Attendance_Status (Pick List: Good / Low Attendance Warning)[cite: 3].
- A Deluge function, checkLowAttendance, takes the triggering Attendance Records entry as input, recalculates that student's overall attendance percentage from all of their Attendance Records, and writes the result to Attendance_Percentage on the corresponding Student record[cite: 3].
- The same function evaluates the recalculated percentage: if it falls below 75%, Attendance_Status is set to 'Low Attendance Warning'; otherwise it is set to 'Good'[cite: 3].
- A Workflow Rule on the Attendance Records module (Trigger: On Create) invokes checkLowAttendance automatically every time a new attendance entry is added, so both fields stay current with zero manual effort[cite: 3].
- The Student Dashboard in the Creator app surfaces Attendance_Status alongside Attendance %, so parents see the warning the moment it is triggered — not just staff inside CRM[cite: 3].

---

## 4. Optimisation and Scalability
- Constant Execution Cost: The recalculation runs only for the specific student tied to the triggering Attendance Record, not the entire Students module, so cost stays constant per attendance entry regardless of total student count[cite: 3].
- Event-Driven Accuracy: Using a Workflow Rule (event-driven, On Create) instead of a scheduled batch job means the status is always accurate immediately, with no periodic full-module recalculation needed[cite: 3].
- Precomputed Performance: Storing Attendance_Percentage and Attendance_Status directly on the Student record (rather than computing them on every read) keeps both CRM reports and the Creator dashboard fast, since they read a precomputed field instead of aggregating Attendance Records on demand[cite: 3].
