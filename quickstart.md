# Spec Then Vibecode Quick Start

Follow each step in order. Do not proceed until the current step has been completed.

---

## Project Setup

### Step 1 - Create a specification

Create a file called:

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

Checkbox:

- [ ] `spec.md` created and completed

---

## Scope Validation

### Step 2 - Run Scope Audit

Using a read-only AI agent, run:

```text
Validate spec.md using skills/scope-audit.md
```

Review the output.

If the result is:

```text
FAIL
```

Update `spec.md` and rerun the audit.

Repeat until:

```text
PASS
```

Checkbox:

- [ ] `scope-audit` passed

---

## Specification Validation

### Step 3 - Run Specification Audit

Using a read-only AI agent, run:

```text
Validate spec.md using skills/spec-audit.md
```

Review the output.

If the result is:

```text
FAIL
```

Update `spec.md` and rerun the audit.

Repeat until:

```text
PASS
```

Checkbox:

- [ ] `spec-audit` passed

---

## Task Generation

### Step 4 - Generate Tasks

Using an AI agent, run:

```text
Read spec.md and generate tasks.md using skills/task-planner.md
```

Expected output:

```text
tasks.md
```

Checkbox:

- [ ] `tasks.md` generated

---

## Test Generation

### Step 5 - Generate Test Specification

Using an AI agent, run:

```text
Read spec.md and tasks.md and generate test-spec.md using skills/test-spec-generator.md
```

Expected output:

```text
test-spec.md
```

Checkbox:

- [ ] `test-spec.md` generated

---

## Implementation

### Step 6 - Generate Code

Using an AI coding agent, run:

```text
Read:

- spec.md
- tasks.md
- test-spec.md

Use agent/coding.md to implement the project.
```

If the coding agent responds:

```text
Specification clarification required.
```

Update `spec.md` and return to:

```text
Step 2
```

Expected output:

```text
Completed application
```

Checkbox:

- [ ] Application implemented

---

## Testing

### Step 7 - Test Implementation

Using an AI testing agent, run:

```text
Read:

- test-spec.md
- generated source code

Use agent/tester.md to execute tests.
```

Expected output:

```text
PASS
```

Checkbox:

- [ ] Tests passed

---

## Compliance Validation

### Step 8 - Run Compliance Audit

Using a read-only AI agent, run:

```text
Compare:

- spec.md
- tasks.md
- test-spec.md
- generated source code
- test results

Use skills/compliance-auditor.md
```

Expected output:

```text
PASS
```

Checkbox:

- [ ] Compliance audit passed

---

## Handling Specification Changes

If requirements change after coding has started:

### Step 9 - Update Specification

Update:

```text
spec.md
```

Checkbox:

- [ ] Specification updated

### Step 10 - Re-run Validation

Run:

```text
scope-audit
spec-audit
```

Checkbox:

- [ ] Validation rerun

### Step 11 - Regenerate Project Artifacts

Generate:

```text
tasks.md
test-spec.md
```

Checkbox:

- [ ] tasks.md regenerated
- [ ] test-spec.md regenerated

### Step 12 - Resume Implementation

Using the coding agent:

```text
Review all existing code for impact.

Continue implementation using:
- spec.md
- tasks.md
- test-spec.md
```

Checkbox:

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
