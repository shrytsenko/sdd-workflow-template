# Task Execution Plan: [Feature Name]

> **Instructions**: Execute tasks sequentially. Before each task, make sure previous tests pass. Mark `[x]` once a task is done.

## Task Breakdown

- [ ] **Task 1: Create database migration**
  - **Scope**: Add a `google_id` column to the `users` table.
  - **Files**: `migrations/20261120_add_google_id.sql`, `src/db/schema.ts`
  - **Given/When/Then**: Scenario 1 in `spec.md`.
  - **DoD**: Migration runs successfully both up and down (`up` / `down`).

- [ ] **Task 2: Write TDD tests for Auth Service (Test Agent)**
  - **Scope**: Write unit & integration tests for token validation.
  - **Files**: `tests/unit/auth.service.test.ts`
  - **DoD**: Tests are written and FAILING (RED state).

- [ ] **Task 3: Implement Google Auth handling logic (Code Agent)**
  - **Scope**: Write the service that validates the token and generates an internal JWT.
  - **Files**: `src/services/auth.service.ts`
  - **DoD**: All tests from Task 2 turn GREEN.

- [ ] **Task 4: API Endpoint `POST /api/v1/auth/google`**
  - **Scope**: Wire the route to the service and add error handling.
  - **Files**: `src/controllers/auth.controller.ts`, `src/routes/auth.router.ts`
  - **DoD**: Endpoint integration test passes 100%.

- [ ] **Task 5: Final Review & Smoke Test**
  - **Scope**: Clean-context review, SAST/DAST check, prepare the PR.
  - **DoD**: PR created, CI green, rollback instructions added.
