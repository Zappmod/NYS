# Use Case: Application Consolidation & Modernization Planning

> **Prerequisites:** Complete Lab Setup before starting this use case
> **Code Set:** Any COBOL workspace — recommended code: `Sample Code`
> **Duration:** 60 minutes
> **Difficulty:** Intermediate

---

## Overview

Modernization without planning is one of the leading causes of failed mainframe transformation programmes. This use case demonstrates how Bob serves as the technical planning engine for consolidation and modernization — identifying application boundaries, detecting tightly coupled systems, mapping shared functionality, highlighting duplicate logic, and producing prioritized modernization roadmaps. Bob provides the analysis; your architects make the decisions.

---

## Learning Objectives

By the end of this use case, you will be able to:

- Identify natural application boundaries within a large COBOL portfolio
- Detect tightly coupled programs that are difficult to modernize independently
- Surface duplicate and redundant business logic across the codebase
- Map shared functionality that could be extracted as common services
- Generate a prioritized modernization roadmap with risk and effort estimates
- Support human-in-the-loop decision making with structured technical evidence

---

## Actions

1. Ensure you have completed workspace scan and Agent.md initialization from Lab Setup
2. Use **Z Architect** mode for all exercises in this use case
3. Copy each prompt from the code block and paste it into the Bob chat
4. Approve any tool requests — or enable **Auto Approve** in the Permissions dropdown
5. Review the output and discuss findings with your team before making planning decisions

> **Tip:** Modernization planning exercises produce the most value when you ask follow-up questions. Use Bob's output as a starting point for a deeper investigation.

---

## Exercises

### Exercise 1: Application Boundary Identification

Identify the natural service boundaries within a large COBOL application — the logical groups of programs that could be modernized independently.

**1. Identify functional domains**

```
Analyze the GENAPP codebase and identify the natural functional domains within the application. Group programs by their business domain and describe each group's responsibilities.
```

**2. Find domain entry points**

```
For each functional domain you identified, which programs serve as the entry points? What is the interface contract for each entry point — inputs, outputs, and side effects?
```

**3. Map cross-domain dependencies**

```
Are there programs that are shared between multiple functional domains? List all cross-domain dependencies and rate each one as: Low risk (can be copied), Medium risk (shared interface), or High risk (tightly coupled).
```

---

### Exercise 2: Tightly Coupled System Detection

Identify programs so tightly coupled that modernizing one requires modernizing all of them together — so the team can plan realistic workstreams.

**1. Find high-coupling clusters**

```
Identify the most tightly coupled clusters of programs in this application. A cluster is a group of programs that call each other frequently and share data structures. Rank clusters by coupling strength.
```

**2. Shared COMMAREA analysis**

```
Which programs share COMMAREA data structures? Draw a dependency graph of all programs connected by a common COMMAREA layout, and identify the highest-risk shared structures.
```

**3. Modernization unit sizing**

```
Based on the coupling analysis, suggest how the application should be decomposed into modernization units — groups of programs that should be migrated together. Estimate the relative size of each unit.
```

---

### Exercise 3: Duplicate & Redundant Logic Detection

Surface business logic that has been implemented multiple times across different programs — a major source of maintenance burden and modernization risk.

**1. Find duplicate business logic**

```
Are there paragraphs or sections across multiple GENAPP programs that implement similar or identical logic? Identify the top 5 candidates for consolidation.
```

**2. Redundant validation routines**

```
Which programs implement their own input validation? Are any validation routines duplicated? Could these be extracted into a shared validation module?
```

**3. Repeated SQL patterns**

```
Are there repeated SQL query patterns across multiple programs that read from the same tables with the same WHERE clauses? Identify candidates for shared stored procedures.
```

---

### Exercise 4: Shared Functionality Mapping

Identify common services that exist implicitly across the codebase — utilities, error handlers, and data access routines that are candidates for extraction into shared libraries.

**1. Common utilities inventory**

```
List all utility programs in GENAPP that are called from three or more other programs. For each utility, describe its function and suggest whether it should become a shared service in a modernized architecture.
```

**2. Error handling consolidation**

```
How is error handling implemented across GENAPP? Are there multiple different patterns? Identify which programs have no error handling and which implement it consistently.
```

**3. Data access layer mapping**

```
Which programs access DB2 directly versus which programs go through a shared data access program? Map the data access patterns and recommend whether a common data access layer should be introduced.
```

---

### Exercise 5: Modernization Roadmap Generation

Use Bob's analysis to produce a prioritized, actionable modernization roadmap.

**1. Complexity-based prioritization**

```
Rank all programs in GENAPP by modernization complexity — considering cyclomatic complexity, coupling, lines of code, and number of DB2 operations. Produce a prioritized list: start with low-complexity, low-risk programs.
```

**2. Quick win identification**

```
Which programs are good candidates for early modernization — low complexity, few dependencies, no shared copybooks, and limited DB2 operations? List the top 5 quick wins with justification.
```

**3. Full modernization roadmap**

```
Generate a modernization roadmap for GENAPP organized into three phases: 
Phase 1 — Quick wins (low complexity, low risk)
Phase 2 — Core business logic (medium complexity, high business value)
Phase 3 — Complex tightly coupled programs (high complexity, high risk)
For each phase, list the programs, estimated effort, dependencies, and key risks.
Format the output as a structured markdown document.
```

---

## Key Takeaways

- **Application boundary detection** is the foundation of any modernization plan — Bob uses the Z Understand metadata to identify functional domains without requiring manual analysis
- **Coupling analysis** prevents the most common modernization mistake: treating tightly coupled programs as independent migration units
- **Duplicate logic detection** surfaces consolidation opportunities that reduce long-term maintenance burden before a line of modernized code is written
- **Roadmap generation** gives architects and project managers a structured, evidence-based starting point for modernization planning conversations
- Bob accelerates the discovery phase but does not replace human judgment — use its output to inform decisions, not to make them automatically

---
