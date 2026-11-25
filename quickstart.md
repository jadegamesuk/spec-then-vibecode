# Spec Then Vibecode Quick Start

Follow each step in order. Do not proceed until the current step has been completed.

---

# Project Setup

## Step 1 - Create Specification

Create:

```text
spec.md
```

Populate the following sections:

```text
Goal
In Scope
Out of Scope
User Workflow
Requirements
Frontend
Backend
Database
Storage
Project Constraints
Authentication
Acceptance Criteria
Required External Dependencies
```

- [ ] `spec.md` completed

---

# Scope Validation

## Step 2 - Run Scope Audit

Open a read-only AI agent.

Copy and paste:

```text
Read spec.md.

Use the instructions in skills/scope-audit.md.

Audit the specification.

Do not modify spec.md.
Do not infer requirements.
Do not make product decisions.

Return the output exactly as defined in scope-audit.md.
```

If the result is FAIL:

```text
Update spec.md
Run Step 2 again
```

Repeat until PASS.

- [ ] `scope-audit` passed

---

# Specification Validation

## Step 3 - Run Spec Audit

Open a read-only AI agent.

Copy and paste:

```text
Read spec.md.

Use the instructions in skills/spec-audit.md.

Audit the specification.

Do not modify spec.md.
Do not infer requirements.
Do not make implementation decisions.

Return the output exactly as defined in spec-audit.md.
```

If the result is FAIL:

```text
Update spec.md
Run Step 3 again
```

Repeat until PASS.

- [ ] `spec-audit` passed

---

# Task Generation

## Step 4 - Generate Tasks

Open an AI agent.

Copy and paste:

```text
Read spec.md.

Use the instructions in skills/task-planner.md.

Generate tasks.md.

Write all implementation tasks required to deliver the specification.
```

Expected output:

```text
tasks.md
```

- [ ] `tasks.md` generated

---

# Test Specification Generation

## Step 5 - Generate Test Specifications

Open an AI agent.

Copy and paste:

```text
Read:

- spec.md
- tasks.md

Use the instructions in skills/test-spec-generator.md.

Generate test-spec.md.
```

Expected output:

```text
test-spec.md
```

- [ ] `test-spec.md` generated

---

# Implementation

## Step 6 - Generate Code

Open an AI coding agent.

Copy and paste:

```text
Read:

- spec.md
- tasks.md
- test-spec.md

Use the instructions in agent/coding.md.

Implement all tasks.

Do not infer requirements.
Do not add functionality.
Do not substitute technologies.

If implementation cannot continue, stop immediately and return:

Specification clarification required.
```

Expected output:

```text
Working application
```

- [ ] Application implemented

---

# Testing

## Step 7 - Run Tests

Open an AI testing agent.

Copy and paste:

```text
Read:

- generated source code
- test-spec.md

Use the instructions in agent/tester.md.

Execute all tests and return results.
```

Expected output:

```text
PASS
```

or

```text
FAIL
```

- [ ] Tests passed

---

# Compliance Audit

## Step 8 - Run Compliance Audit

Open a read-only AI agent.

Copy and paste:

```text
Read:

- spec.md
- tasks.md
- test-spec.md
- generated source code
- test results

Use the instructions in skills/compliance-auditor.md.

Verify implementation matches the approved specification.

Return the output exactly as defined in compliance-auditor.md.
```

Expected output:

```text
PASS
```

- [ ] Compliance audit passed

---

# Handling Specification Changes

If requirements change after implementation has started:

## Step 9 - Update Specification

Update:

```text
spec.md
```

- [ ] Specification updated

---

## Step 10 - Re-run Audits

Run:

```text
Read spec.md.

Use skills/scope-audit.md.
```

Then:

```text
Read spec.md.

Use skills/spec-audit.md.
```

Both must PASS.

- [ ] scope-audit passed
- [ ] spec-audit passed

---

## Step 11 - Regenerate Project Artefacts

Generate:

```text
tasks.md
```

using:

```text
Use skills/task-planner.md.
```

Generate:

```text
test-spec.md
```

using:

```text
Use skills/test-spec-generator.md.
```

- [ ] tasks.md regenerated
- [ ] test-spec.md regenerated

---

## Step 12 - Resume Implementation

Open the coding agent.

Copy and paste:

```text
Read:

- spec.md
- tasks.md
- test-spec.md
- existing source code

Review the impact of the specification change.

Update implementation as required.

Continue using agent/coding.md.
```

- [ ] Existing code reviewed
- [ ] Implementation resumed

---

# Definition of Done

The project is complete when all boxes below are checked:

- [ ] spec.md completed
- [ ] scope-audit passed
- [ ] spec-audit passed
- [ ] tasks.md generated
- [ ] test-spec.md generated
- [ ] application implemented
- [ ] tests passed
- [ ] compliance-auditor passed
