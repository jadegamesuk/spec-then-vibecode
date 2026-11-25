# Spec Then Vibecode

A specification-driven workflow for AI-assisted software development.

Instead of asking an LLM to build software from a vague idea, define exactly what should be built first. The workflow uses auditing, planning, implementation and compliance stages to ensure generated code matches the specification and nothing more.

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

## Goals

- Reduce AI hallucinations
- Prevent undocumented features
- Avoid unwanted architectural decisions
- Catch specification gaps before implementation
- Ensure generated code matches requirements

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

## Process

### 1. Scope Audit

Validates that the proposed solution is appropriately scoped and capable of achieving the stated goal.

### 2. Specification Audit

Validates that the specification can be implemented exactly as written without assumptions.

### 3. Task Planning

Converts the approved specification into implementation tasks.

### 4. Test Specification Generation

Creates tests derived from requirements and acceptance criteria rather than generated code.

### 5. Coding

Implements the specification.

Rules:

- Do not infer requirements
- Do not add features
- Do not substitute technologies
- Stop and request clarification if information is missing

### 6. Testing

Validates implementation against the generated test specification.

### 7. Compliance Audit

Verifies:

- All requirements implemented
- All acceptance criteria implemented
- All tests exist and pass
- No undocumented functionality exists
- No specified functionality is missing

## Design Principles

- Specification before implementation
- Requirements before code
- Tests before validation
- No AI product decisions
- No undocumented functionality

## Limitations

This workflow can only evaluate information explicitly written in the specification. Missing or incorrect requirements in `spec.md` will lead to missing or incorrect behaviour in the final application.

## Detailed Documentation

See the individual files under `skills/` and `agents/` for the complete prompts and behaviour definitions.
