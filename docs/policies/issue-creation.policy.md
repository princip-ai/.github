

# 📘 Jira Issue Creation Policy

This document defines how issues must be created, structured, and linked in Jira.
All contributors are expected to follow this policy when creating or updating issues.

---

## 1. Issue Hierarchy (Mandatory)

Jira issues must follow this hierarchy:

```
Epic
 └── Story
      └── Sub-task
 └── Task
 └── Bug
```

Each level has a **clear responsibility and scope**.

---

## 2. Issue Types & Usage Rules

### 🎯 Epic

**Purpose**
Epics represent **high-level product or domain areas**.
They answer: *“What major capability are we building?”*

**Owner**
Product Owner / Tech Lead

**Rules**

* Epics are long-lived
* Epics define *what*, not *how*
* Stories must always belong to exactly one Epic

**Real Example:** 
- [EPIC - Core Linguistics Engine](https://principai.atlassian.net/browse/VOC-16)

This Epic represents the core language intelligence layer of the product.

---

### 📘 Story

**Purpose**
Stories represent **deliverable product or platform capabilities**.

They answer: *“What will exist in the system when this is done?”*

**Owner**
Assigned Engineer

**Rules**

* Stories must be independently deliverable
* Stories must belong to an Epic
* Stories may include multiple sub-tasks
* Default case: no labels

---

#### ✅ Correct Story Example

- [Story - Create Vocabulary Module](https://principai.atlassian.net/browse/VOC-7)
  ```
  Epic: Core Linguistics Engine
  Components: backend
  FixVersion: 1.0.0-mvp
  ```

Meaning:

> When this story is done, the Vocabulary domain exists in the system.

---

#### ❌ Anti-pattern (to avoid)

```text
Story: Create CRUD operations
```

This is *how*, not *what* → should be a **sub-task**, not a story.

---

### 🔧 Sub-task

**Purpose**
Sub-tasks represent **implementation steps** required to complete a Story.

They answer: *“How do we implement the story?”*

**Rules**

* Sub-tasks must always have a parent Story
* Sub-tasks are technical and granular
* Sub-tasks are not independently valuable

---

#### ✅ Correct Sub-task Examples

(under *Create Vocabulary Module*)
 - [Sub-task - Create CRUD operation for Vocabulary](https://principai.atlassian.net/browse/VOC-15)
 - [Sub-task - Create UserVocabulary Service](https://principai.atlassian.net/browse/VOC-17)
 - [Sub-task - Improvements vocabulary data model](https://principai.atlassian.net/browse/VOC-18)

✔️ These are implementation steps
✔️ Correctly scoped as sub-tasks

---

### 🛠 Task

**Purpose**
Tasks represent **technical, operational, or documentation work** that does not map directly to a product story.

**Rules**

* Tasks may exist without an Epic
* Tasks may have empty Components
* Common use cases:

  * Architecture & UML
  * Dev environment setup
  * CI/CD
  * Documentation
  * Research / spikes

---

#### ❌ Misplaced Example (Important)
  - [Task - Create a development environment](https://principai.atlassian.net/browse/VOC-6)

  This **should NOT be a Task** under *Core Linguistics Engine*.

---

#### ✅ Corrected Form

```text
Task: Set up development environment
Epic: Platform & Developer Experience (or none)
Components:
- backend
- infra
Labels:
- spike (only if exploratory)
```

---

## 3. Components Policy

**Purpose**
Components represent the **execution layer** affected by the issue.

### Allowed Components

```text
backend
web
mobile
desktop
chrome
infra
```

### Rules

* Components answer: *“Where does this work happen?”*
* Components are optional
* Leave Components empty if the work is:

  * Architecture-level
  * UML / design
  * Research
  * Cross-cutting

---

### Example

```text
Task: Create UML diagrams for Core Linguistics Engine
Components: (empty)
Labels:
- doc
- architecture
Epic:
- Core Linguistics Engine
```

---

## 4. Labels Policy

**Purpose**
Labels describe the **nature or risk profile** of the work.

> A label means: *“This is not a standard task.”*

### Approved Labels

```text
doc
architecture
tech-debt
performance
security
ux
experiment
spike
blocked
```

### Rules

* Default case: no labels
* Do NOT use labels for:

  * Modules
  * Platforms
  * MVP / release scope
* Labels must be intentional and minimal

---

### Correct Label Usage Examples

```text
Architecture documentation → doc, architecture
Performance optimization → performance
Research / POC → spike
UX improvement → ux
```

---

## 5. Fix Versions Policy

**Purpose**
Fix Versions define **release scope**.

### Example

```text
1.0.0-mvp
```

### Rules

* FixVersion is the single source of truth for releases
* Do NOT duplicate release information using labels
* Issues without FixVersion are considered out of scope

---

## 6. Decision Guide (Quick Reference)

| Question                         | Use        |
| -------------------------------- | ---------- |
| What domain is this?             | Epic       |
| What capability is delivered?    | Story      |
| How is it implemented?           | Sub-task   |
| Is it operational / doc / infra? | Task       |
| Where does it run?               | Component  |
| Is it non-standard or risky?     | Label      |
| Is it part of a release?         | FixVersion |

---

## 7. Final Principle

> If an issue is hard to classify, it is usually **too big** or **poorly scoped**.

Clean structure = clear thinking = faster delivery.
