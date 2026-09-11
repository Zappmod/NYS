# Use Case: Production Support & Business Logic Debugging

> **Prerequisites:** Complete Lab Setup before starting this use case
> **Code Set:** Any COBOL workspace — recommended code: `Sample Code`
> **Duration:** 45 minutes
> **Difficulty:** Intermediate

---

## Overview

Production incidents on mainframe applications are notoriously difficult to diagnose. Developers are often asked to investigate failures in programs they have never worked in, tracing data through dozens of interconnected COBOL programs under time pressure. This use case demonstrates how Bob accelerates root cause analysis — identifying where incorrect data originated, which business rule failed, and what downstream processes were affected — dramatically reducing investigation time.

---

## Learning Objectives

By the end of this use case, you will be able to:

- Use Bob to identify the root cause of a business logic failure
- Trace unexpected data values back to their origin across programs
- Identify which business rule was violated and where
- Map the downstream impact of a data or logic error
- Reconstruct the code path that caused a production issue
- Document findings in a structured incident report

---

## Actions

1. Ensure you have completed workspace scan and Agent.md initialization from Lab Setup
2. Start in **Z Architect** mode for analysis exercises; switch to **Z Code** when implementing fixes
3. Copy each prompt from the code block and paste it directly into the Bob chat
4. Approve any tool requests — or enable **Auto Approve** in the Permissions dropdown
5. Review outputs carefully — these exercises simulate a real production investigation

> **Tip:** Production support scenarios benefit from starting a fresh chat per investigation so context from one incident does not contaminate another.

---

## Exercises

### Exercise 1: Root Cause Analysis — Incorrect Data

You have received a production incident: a customer policy record contains an incorrect effective date. You need to find where the value was set and why it is wrong.

**1. Trace a field to its origin**

```
In the GENAPP application, where is CA-PAYMENT-AMOUNT set across all programs? Show every paragraph that writes to this field, in the order they would be executed for a typical policy creation request.
```

**2. Identify where unexpected values could enter**

```
Which paragraphs in LGAPDB01 write to the policy effective date field? Are there any code paths where the date could be set to a default or empty value?
```

**3. Find missing validation**

```
Does LGAPDB01 validate the policy start date before inserting a record? If not, which programs in the call chain would be responsible for that validation?
```

---

### Exercise 2: Business Rule Failure Analysis

A calculation is producing wrong results. Use Bob to identify which business rule is responsible and trace the logic back to its source.

**1. Locate the business rule**

```
Which program and paragraph in GENAPP is responsible for calculating the premium amount for a new policy? Walk me through the calculation logic step by step.
```

**2. Find conditional branches**

```
In the premium calculation logic, are there conditional branches that could produce a zero or negative premium? List all conditions that lead to an unexpected value.
```

**3. Trace data from input to output**

```
Trace CA-PREMIUM-AMOUNT from the moment it is first assigned through every program that modifies it, until it is written to the database. Show the full data flow.
```

---

### Exercise 3: Code Path Reconstruction

Reconstruct the exact execution path through the application that led to a production failure, so you can reproduce and fix it.

**1. Reconstruct the call path**

```
A transaction that adds a new customer policy fails at the database insert step. Show me the full call path from the entry point program down to the DB2 INSERT operation, including every program and paragraph involved.
```

**2. Find error handling gaps**

```
Does LGAPDB01 handle a DB2 SQLCODE of -803 (duplicate key)? If not, what happens to the transaction — does it abend, continue silently, or return an error to the caller?
```

**3. Identify defensive code**

```
Which programs in the GENAPP call chain check SQLCODE after every DB2 operation? Which programs skip this check and could silently ignore database errors?
```

---

### Exercise 4: Downstream Impact of a Data Error

Understand what downstream processes and applications were affected by a data corruption event so you can scope the remediation effort.

**1. Find all consumers of a corrupted field**

```
If DB2-LASTNAME was corrupted for a set of policy records, which programs read and use that field in subsequent processing? What reports, interfaces, or downstream jobs would produce incorrect output?
```

**2. Trace downstream job dependencies**

```
Which batch jobs in this application read from the POLICY table? If a policy record is corrupted, which jobs would propagate that bad data further?
```

**3. Identify notification and reporting paths**

```
Does any program in this application send output files or notifications based on policy data? Identify all programs that write output files and the data fields they include.
```

---

### Exercise 5: Incident Documentation

Use Bob to generate a structured incident report based on your investigation findings.

**1. Generate an incident summary**

```
Based on our investigation, generate a structured production incident report for the following scenario: the CA-PAYMENT-AMOUNT field was set to zero for policies created between a given date range due to missing validation in LGAPDB01. Include: root cause, affected programs, downstream impact, recommended fix, and regression test recommendations. Format as markdown.
```

**2. Generate a fix recommendation**

```
Based on the missing validation found in LGAPDB01, generate a code change that adds a check to ensure CA-PAYMENT-AMOUNT is greater than zero before the DB2 INSERT. Include the exact paragraph and placement for the new validation logic.
```

---

## Key Takeaways

- **Z Architect mode** is the fastest way to trace data flows and reconstruct execution paths — it uses the pre-built metadata repository rather than re-reading files from scratch
- **Variable flow tracing** across programs is one of Bob's most powerful capabilities for production support — it surfaces assignment and read points across the entire application instantly
- **Conditional branch analysis** helps identify code paths that silently produce incorrect data without causing an abend
- **Downstream impact mapping** scopes the remediation effort before a single line of code is changed
- Bob can turn investigation findings into a structured incident report and a code fix in a single step

---
