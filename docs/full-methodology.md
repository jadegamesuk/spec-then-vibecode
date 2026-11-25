### Spec driven vibe coding Steps

Given my goals to complete some projects using AI, I have been thinking that it would be best to document what I want rigously and have the LLM implement it exactly. It seems that for effective code generation, rather than vibe coding a solution, it should be fully speced out so I fully know what the out is that I am getting. I've been thinking about the best way to do this and have come up with the following structure:

- Write `spec.md` 

   Headers:
	- Goal: overarching target that explains what the code should do (e.g. translate video uploaded by user)
	- In Scope: specific things the code should contain to reach goal (e.g. HTML5, web interface )
	- Out of Scope: specific things the code should NOT contain to reach goal (e.g. API, authentication, 1GB file limit, billing, admin dashboard)
	- User Workflow: steps the end user will click through to use the product (e.g. upload file, download translated file)
	- Requirements: Things the code ought to have (e.g. minimal options, HTML5, CSS, error capturing, max 1 video upload at a time)
	- Frontend: frontend solution (e.g. React, Electron)
	- Backend: backend solution (e.g. NodeJS)
	- Database: database backend solution (e.g. Postress, SQLlite)
	- Storage: storage solution: (e.g. S3, disk)
  - Project Constraints (e.g. Ubuntu 24.04 only, offline, GPU-required, max RAM usage 8GB, Docker Compose)
  - Authentication: defines how users will authenticate to use product (e.g. None, Google login, OAuth2, cookies)
  - Acceptance Criteria (e.g. user upload file, user informed upload successful, specific file formats only, updating progress bar 
  - Required External Dependencies (e.g. none)

- `spec.md` is handed to a read-only agent via a skill, `scope-audit`, that reads `spec.md` to check if the goal and scope is met and nothing more. The agent will check if `spec.md` contains enough information to answer this question accurately (is this overengineered? Identify business, usage, scale or operational assumptions
required to validate scope. Do the decisions made allow the goal to be reached and nothing else? Are there any missing business assumptions, etc.) Anything else relevant and not explicitly stated in `spec.md` should be flagged to allow the user to fill in the missing information to accurately pass this test. The LLM should NOT 'fill in' any blanks or make any product decisions, although it can suggest them. Do not infer requirements, only report issues. Every issue found must reference section. It should suggest changes to fix those issues and they should be suggested based on high/medium/low severity. The severity definitions are shown below:

      - High severity: 
        Goal cannot be achieved
        Requirements cannot be implemented
        Contradictory requirements exist
        Critical information missing

      - Medium severity:
        Behavour ambigious
        Edge case undefined
        Acceptance criteria incomplete

      - Low severity:
        Clarity issue
        Style issue
        Improvement suggestion

The format for `scope-audit` should look like:

          Output:

          PASS | FAIL

          High Severity:
          ...

          Medium Severity:
          ...

          Low Severity:
          ...

- I implement the suggested changes in `spec.md` and the above step is rerun until the `spec.md` passes successfully. A pass is defined as no remaining high or medium severity issues.

- `spec.md` is read by a read-only agent via a skill, `spec-audit`, that reads `spec.md` to check if the steps are clear enough to be implemented as written. It should inform the user if things are unspecified, or there are edge cases not considered. The LLM should NOT 'fill in' any blanks in my description or make any product decisions. Do not infer requirements, only report issues, every issue must reference section. Check for missing, ambiguous or contradictory requirements. Check for undefined behaviour or missing edge cases. It should suggest changes to make to fix those issues and they should suggested changes based on high/medium/low severity

The format for `spec-audit` should look like:

          Output:

          PASS | FAIL

          High Severity:
          ...

          Medium Severity:
          ...

          Low Severity:
          ...

 - I implement the suggested changes in `spec.md` and the above step is rerun until the `spec.md` passes successfully. A pass is defined as no remaining high or medium severity issues.

- `spec.md` is read by an agent via a skill, `task-planner`, that reads and splits all the work from `spec.md` into achieveable bulletpoints and writes this information into a new file, `tasks.md` 

The format for `spec-audit` should look like:

          Output:

          tasks.md


- An agent reads both `spec.md` and `tasks.md` via a new skill, `test-spec-generator`, and writes to a new file, `test-spec.md`. This skill lists tests to be created that are tied to the specifications written rather than code not yet produced. For example Test1: "upload valid video file" Expected: "Success" Test2: "upload invalid video file" Expected: "failure"

The format for `test-spec-generator` should look like:
          Output:

          test-spec.md

- A coding agent opens `spec.md`, `tasks.md` and `test-spec.md` and implements each bulletpoint in `tasks.md`. The coding agent should only read those 3 files. It should not add features not present in `spec.md`, it should not substitute technologies listed in `spec.md`. Do not remove requirements listed in `spec.md`. Do not implement optional behaviour unless it is explicitly specified. If it isn't possible to implement something, it should not infer information, it should pause the implmentation and say "Specification clarification required.", and provide detail on what it specifically needs to continue. Once it has this information, it should ask look at all previously written code to see if the new information will cause any issues to the code already generated. 

If the specification changes after implementation has begun then:

    - Update spec.md
    - Re-run scope-audit
    - Re-run spec-audit
    - Re-generate tasks.md
    - Re-generate test-spec.md
    - Coding agent reviews existing implementation for impact
    - Implementation resumes          

- Once completed, a tester agent creates tests based on `test-spec.md` to verify the code itself is working correctly

- A skill `compliance-auditor` compares, `spec.md`, `tasks.md`, `test-spec.md` and the generated code itself. It's goal is to ask if there was anything implemented that wasn't specified or anything specified but not implemented. This passes if the following steps are met:

    - Every acceptance criterion implemented
    - Every task implemented
    - Every test in `test-spec.md` exists and passes
    - No undocumented functionality exists
    - No contradictory implementation exists
    - No missing implementation exists

The format for `compliance-auditor` should look like:

        Output:

        PASS | FAIL

        Implemented but not specified:
        ...

        Specified but not implemented:
        ...

        Acceptance criteria status:
        ...
