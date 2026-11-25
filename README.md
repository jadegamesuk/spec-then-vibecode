# Spec Then Vibecode

![License](https://img.shields.io/github/license/jadegamesuk/spec-then-vibecode)
![Status](https://img.shields.io/badge/status-active-success)
![Methodology](https://img.shields.io/badge/development-spec--driven-blue)
![AI](https://img.shields.io/badge/AI-agentic%20workflow-purple)

Build software by writing the specification first and generating code second.

Spec Then Vibecode is a specification-driven workflow that treats AI as an implementation tool rather than a product designer. The goal is to reduce hallucinations, prevent scope creep, and ensure generated code matches documented requirements.

## Workflow

```text
spec.md
    ↓
scope-audit
    ↓
spec-audit
    ↓
task-planner
    ↓
test-spec-generator
    ↓
coding-agent
    ↓
tester
    ↓
compliance-auditor
```

## Core Principles

- Specification before implementation
- Requirements before code
- Tests before validation
- No undocumented functionality
- No AI product decisions
- No inferred requirements

## Specification Format

Create a `spec.md` containing:

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

## Repository Structure

```text
skills/
├── scope-audit.md
├── spec-audit.md
├── task-planner.md
├── test-spec-generator.md
└── compliance-auditor.md

agents/
├── coding.md
└── tester.md
```

## Process

### Scope Audit

Validates that the proposed solution is appropriately scoped and capable of achieving the stated goal.

### Specification Audit

Validates that the specification can be implemented exactly as written and identifies ambiguities, contradictions, missing requirements, and undefined behaviour.

### Task Planning

Converts the approved specification into implementation tasks.

### Test Specification Generation

Creates tests derived from requirements and acceptance criteria.

### Coding

Implements the approved specification.

If a requirement is unclear:

```text
Specification clarification required.
```

### Testing

Executes tests generated from the approved test specification.

### Compliance Audit

Verifies:

- Every requirement implemented
- Every acceptance criterion implemented
- Every test exists and passes
- No undocumented functionality exists
- No specified functionality is missing

## Limitations

This workflow can only validate information explicitly written in the specification. Missing or incorrect requirements in `spec.md` will result in missing or incorrect behaviour in the final application.

## Detailed Documentation

See the individual files under `skills/` and `agents/` for complete prompts and behaviour definitions.
