# Task Execution Plan: [Назва Фічі]

> **Інструкція**: Виконуйте задачі послідовно. Перед кожною задачею переконайтеся, що попередні тести проходять. Після завершення задачі ставте позначку `[x]`.

## Task Breakdown

- [ ] **Task 1: Створення міграції бази даних**
  - **Scope**: Додати поле `google_id` у таблицю `users`.
  - **Files**: `migrations/20261120_add_google_id.sql`, `src/db/schema.ts`
  - **Given/When/Then**: Scenario 1 у `spec.md`.
  - **DoD**: Міграція успішно виконується накатом та відкатом (`up` / `down`).

- [ ] **Task 2: Написання TDD тестів для Auth Service (Test Agent)**
  - **Scope**: Написати unit & інтеграційні тести під валідацію токена.
  - **Files**: `tests/unit/auth.service.test.ts`
  - **DoD**: Тести створені і НЕДІЄЗДАТНІ / ПАДАЮТЬ (RED state).

- [ ] **Task 3: Реалізація логіки обробки Google Auth (Code Agent)**
  - **Scope**: Написати сервіс валідації токена та генерації внутрішнього JWT.
  - **Files**: `src/services/auth.service.ts`
  - **DoD**: Усі тести з Task 2 стають ЗЕЛЕНИМИ (GREEN state).

- [ ] **Task 4: API Endpoint `POST /api/v1/auth/google`**
  - **Scope**: Підключити роут до сервісу та додати обробку помилок.
  - **Files**: `src/controllers/auth.controller.ts`, `src/routes/auth.router.ts`
  - **DoD**: Інтеграційний тест ендпоінту проходить 100%.

- [ ] **Task 5: Final Review & Smoke Test**
  - **Scope**: Перевірка з чистим контекстом, SAST/DAST перевірка, підготовка PR.
  - **DoD**: PR створено, CI зелений, інструкція з відкату додана.
