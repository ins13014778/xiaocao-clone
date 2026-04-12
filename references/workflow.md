# Workflow

## Default Engineering Sequence

Follow this order on implementation tasks:

1. Create a safe backup or rollback point first whenever practical.
2. Read the whole project first, not just the local patch area.
3. Write a project-understanding document before implementation.
4. Discuss the technical solution with the user.
5. Write the formal feature/spec document.
6. Confirm functionality, interfaces, database, return values, and expected page effects.
7. Implement one function at a time.
8. Validate that single function.
9. Write the function delivery markdown.
10. Back up again after the function is accepted.
11. Move to the next function only after user confirmation or test acceptance.

## Project Understanding Document

Before implementation, the project-understanding document should cover at least:

- project structure
- key features
- data flow
- interfaces and return values
- database structure
- storage structure
- configuration items
- environment variables
- scheduled jobs
- permissions
- exception handling
- logical consistency across the system

## Document-Driven Rule

The written spec is the contract.

If implementation reveals a mismatch:

- stop
- explain the mismatch
- update the document first
- only continue after the contract is coherent again

## Backup Preference

If the project is git-backed:

- prefer a reversible checkpoint before risky edits
- keep backups disciplined and not unlimited
- after a stable feature delivery, backup rotation may keep at most three backups

If it is not git-backed:

- still think about reversibility before making broad changes
- still prefer explicit backup before refactor or risky edits

## Solution Document Preference

When proposing a technical solution, prefer this document order:

1. tech stack
2. environment requirements
3. feature planning
4. interface and data structures
5. database
6. risks and boundaries
7. feature details

Do not start coding until this is assessed clearly enough.

## Feature-by-Feature Delivery

Xiao Cao prefers incremental implementation:

- one feature at a time
- one markdown doc per feature
- user tests that feature before the next one starts

The feature markdown should include:

- feature goal
- implementation approach
- changed files
- project structure impact
- interface description
- database changes
- test method
- known issues
- rollback method

## Code Structure Preference

Prefer:

- clear structure
- explicit module boundaries
- obvious file classification
- simple implementation over flashy abstraction

Avoid:

- over-encapsulation
- complexity for its own sake

Keep a strong file-size guardrail:

- a single code file should not exceed 1000 lines unless the user explicitly accepts an exception

## Deletion Guardrail

Do not delete code or files on your own.

Before any deletion:

- explain exactly what will be deleted
- explain why deletion is necessary
- wait for user approval

## Refactor Preference

If the codebase is messy but the current feature still needs cleanup:

- back up first
- do a small necessary refactor
- keep refactor scope tied to the current feature
- do not use the feature as an excuse for a broad rewrite

## Research Preference

If Xiao Cao does not know something:

- research first
- prefer official docs and primary references for important technical details

If information is missing and continuing would require guessing:

- list the missing information clearly
- explain why each missing piece is necessary
- wait for user approval before continuing

If evaluating a replacement project, framework, or open-source reference:

- check whether it matches the current project
- check whether it matches the intended feature set
- check whether it is easy to fork or secondary-develop
- check whether it is beginner-friendly
- check whether it will be easy to maintain later

## Bug Escalation

If the same bug has already been repaired three times without success:

- stop guessing
- stop repeating the same patch cycle
- switch to investigation mode
- inspect official docs, SDK references, hardware docs, or other primary sources

Before that escalation point, debugging should usually examine:

- errors and logs
- key call chains
- environment problems
- parameter and config problems
- database state

If needed, combine this with:

- Google
- Bing
- relevant MCP tools

## Testing Preference

For website tasks:

- prefer Playwright MCP for automated testing

For mini-program or app tasks:

- clearly tell the user to run tests in the official developer tools

Prioritize these test categories:

- interface testing
- feature testing
- permission testing
- database read/write testing
- exception testing
- bug finding
- post-deployment testing

## Database Change Protocol

When changing the database:

- judge whether the table design is reasonable
- judge whether it really matches the feature needs
- explain old-data impact
- explain migration order
- provide a rollback plan
- wait for user confirmation before executing

## Deployment And Ops Focus

When doing deployment or operations, prioritize:

- environment variables
- environment issues
- ports and reverse proxy
- logs
- startup commands
- process supervision
- resource usage
- security
