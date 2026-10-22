# Консолідована Матриця Трасування M:N (Вимоги ↔ Use Cases)

## 1. Реєстр Прецедентів (Use Cases)

| UC ID | Назва Use Case | Актор |
|---|---|---|
| **UC-01** | Пошук та перегляд каталогу | Guest (успадковує User, Librarian) |
| **UC-02** | Фільтрація за автором/роком (`<<extend>>` UC-01) | Guest |
| **UC-03** | Авторизація (Log In) | Guest |
| **UC-04** | Перегляд історії Loan | User |
| **UC-05** | Створення запиту на Loan | User |
| **UC-06** | Скасування бронювання (`<<extend>>` UC-05) | User |
| **UC-07** | Додавання Book та Author | Librarian |
| **UC-08** | Перевірка унікальності ISBN (`<<include>>` UC-07) | Librarian |
| **UC-09** | Підтвердження повернення книги | Librarian |
| **UC-10** | Формування сповіщень про борги (`<<delegate>>`) | Notification Service (`<<System>>`) |

> **Примітка:** `UC-03 (Log In)` виступає **передумовою (Precondition)** для авторизованих дій і НЕ зв'язується через `<<include>>`.

---

## 2. Зведена Матриця M:N

| EARS Вимога | Тип | UC-01 | UC-02 | UC-03 | UC-04 | UC-05 | UC-06 | UC-07 | UC-08 | UC-09 | UC-10 | Статус |
|---|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **REQ-UBI-01** | Ubiquitous | ✔ | | | ✔ | ✔ | | ✔ | | ✔ | | **COVERED** |
| **REQ-UBI-02** | Ubiquitous | | | | ✔ | ✔ | ✔ | | | ✔ | | **COVERED** |
| **REQ-EVT-01** | Event-driven | | | | | ✔ | | | | | | **COVERED** |
| **REQ-EVT-02** | Event-driven | | | | | | | | | ✔ | | **COVERED** |
| **REQ-EVT-03** | Event-driven | | | | | | | ✔ | ✔ | | | **COVERED** |
| **REQ-STA-01** | State-driven | | | ✔ | ✔ | | | | | | | **COVERED** |
| **REQ-STA-02** | State-driven | | | | | ✔ | | | | | | **COVERED** |
| **REQ-EXC-01** | Exception | | | | | ✔ | | | | | | **COVERED** |
| **REQ-EXC-02** | Exception | | | | | | | ✔ | ✔ | | | **COVERED** |
| **REQ-OPT-01** | Optional | | | | | | | | | | ✔ | **COVERED** |
| **REQ-NFR-PERF-01** | NFR (Perf) | ✔ | ✔ | | | | | | | | | **COVERED** |
| **REQ-NFR-SEC-01** | NFR (Sec) | | | ✔ | | | | | | | | **COVERED** |
| **REQ-OUT-01** | Out of Scope | | | | | | | | | | | **UNCOVERED** |

---

## 3. Непокрита вимога (Uncovered Requirement)

| ID Вимоги | Назва вимоги | Причина відсутності покриття | Заплановано |
|---|---|---|---|
| **REQ-OUT-01** | Онлайн-оплата штрафів | Виходить за межі поточного функціоналу системи і не реалізується у базовому релізі. | Майбутні релізи |
