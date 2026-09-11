# Use Case: Enterprise Application Understanding

> **Prerequisites:** Complete Lab Setup before starting this use case
> **Code Set:** Any COBOL workspace — recommended code: `Sample Code`
> **Duration:** 45 minutes
> **Difficulty:** Beginner

---

## Overview

In this use case you will use Bob to build a comprehensive, structured understanding of a large COBOL application portfolio — generating dependency maps, program inventories, call graphs, copybook usage trees, database access summaries, and auto-generated technical documentation. This mirrors the real-world challenge faced when onboarding to an unfamiliar mainframe application with hundreds of programs and decades of undocumented history.

Z Understand, the metadata repository that powers Bob's analysis, enables all of this without requiring Bob to re-read source files on every question — results are deterministic, accurate, and fast even at enterprise scale.

---

## Learning Objectives

By the end of this use case, you will be able to:

- Generate a full program inventory and architecture overview for a COBOL application
- Build complete call graphs and program relationship maps
- Trace copybook usage and identify the most widely shared data structures
- Surface all database interactions across the application (DB2, VSAM, files)
- Produce natural-language business logic explanations for any program
- Auto-generate technical documentation that can be exported and shared

---

## Actions

1. Ensure you have completed workspace scan and Agent.md initialization from Lab Setup
2. Switch to **Z Architect** mode for all exercises in this use case
3. Copy each prompt from the code block and paste it into the Bob chat
4. Approve any tool requests — or enable **Auto Approve** in the Permissions dropdown
5. Review the output before continuing to the next exercise

> **Tip:** Start a fresh chat between unrelated exercises to keep context clean.

---

## Exercises

### Exercise 1: Program Inventory

Generate a complete inventory of every program in the application — names, types, sizes, and roles — as a structured document you can export.

**1. Full application inventory**

```
Generate a complete program inventory for this COBOL application. Include program name, type (batch/online/utility), line count, and a one-line description of each program's purpose.
```

**2. Entry point map**

```
Which programs are never called by any other program in this codebase? List all entry points with their likely roles.
```

**3. Application architecture overview**

```
Generate a high-level architecture overview of this COBOL application. Describe the main functional layers, key program groups, and how data flows between them.
```

---

### Exercise 2: Dependency Maps & Call Graphs

Build visual maps of how programs relate to each other — which programs call which, how deep the call trees go, and where the most interconnected programs are.

**1. Full application call graph**

```
Generate a call graph for the entire application showing which programs call which other programs. Highlight the top 5 most-called programs.
```

**2. Tightly coupled programs**

```
Which programs have the highest number of callers and callees combined? Rank the top 10 most interconnected programs.
```

**3. Isolated programs**

```
Which programs are completely isolated — not called by anyone and not calling anyone? Could any of these be dead code?
```

---

### Exercise 3: Copybook Usage

Identify the most widely shared data structures in the application and understand the risk surface created by each shared copybook.

**1. Most-included copybooks**

```
Which copybooks are included by the most programs? Rank all copybooks by inclusion count and show a dependency graph for the top 5.
```

**2. Copybook usage map**

```
Generate a usage map showing every program that includes each copybook. Group by copybook name.
```

**3. Copybook change risk**

```
If I changed LGPOLICY.cpy, which programs would be directly impacted? Which would be indirectly impacted via other copybooks?
```

---

### Exercise 4: Database Access Summary

Map every database interaction in the application — which programs read and write which tables, and which programs are most database-intensive.

**1. Full DB2 access map**

```
Generate a complete DB2 access map for this application. Show every program and the tables it reads, inserts, updates, and deletes.
```

**2. Most-accessed tables**

```
Which DB2 tables are accessed by the most programs? Rank the top 10 tables by number of programs that reference them.
```

**3. Write-heavy programs**

```
Which programs perform the most INSERT, UPDATE, or DELETE operations? Identify the top 5 write-heavy programs.
```

---

### Exercise 5: Business Logic Explanation

Use Bob to translate complex COBOL logic into plain English — making it accessible to architects, business analysts, and developers who are new to the codebase.

**1. Program explanation in plain English**

```
Explain what LGAPDB01 does in plain English. Describe its purpose, inputs, outputs, and the key business rules it enforces.
```

**2. Paragraph-level explanation**

```
Explain the business logic inside the INSERT-POLICY paragraph of LGAPDB01 step by step.
```

**3. Business rule extraction**

```
Extract all business rules implemented in LGAPDB01 as a numbered list. For each rule, reference the paragraph where it is enforced.
```

---

### Exercise 6: Auto-Generated Technical Documentation

Have Bob produce a complete, exportable technical document for a program or the full application.

**1. Program technical document**

```
Generate a complete technical design document for LGAPDB01. Include: purpose, inputs/outputs, program dependencies, DB2 tables accessed, business rules, and error handling. Format as markdown.
```

**2. Application-wide documentation**

```
Generate a technical documentation index for the entire application — one entry per program with: name, purpose, key dependencies, and DB2 tables used.
```

---

## Key Takeaways

- **Z Architect mode** powers all enterprise-scale analysis — it queries the Z Understand metadata repository rather than re-parsing source files
- **Program inventories and call graphs** provide the foundation for every modernization planning activity
- **Copybook usage maps** reveal the most dangerous shared dependencies — a single widely-used copybook change can ripple across hundreds of programs
- **Business logic explanations** bridge the gap between COBOL source code and business stakeholder understanding
- **Auto-generated documentation** eliminates the manual effort of producing technical specs for legacy applications

---
