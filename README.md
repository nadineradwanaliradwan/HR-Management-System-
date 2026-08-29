# HR Management System

A desktop HR management application built in Java with JavaFX. It covers the core day-to-day
workflows of an HR department — employee records, leave requests, payroll, and performance
evaluation — through a role-based dashboard for HR staff and employees.

This project also served as a hands-on exercise in software testing: every core model is covered
by both **white-box** and **black-box/unit** test suites, run through JUnit 5's Suite API.

## Features

- **Authentication** — login flow backed by a file-based login manager
- **Employee management** — add, edit, and view employee records (ID, department, role, salary,
  leave balance, performance score)
- **HR dashboard** — central view for HR staff to manage employees and department data
- **Employee dashboard** — a scoped view for individual employees
- **Leave management** — submit and process leave requests
- **Payroll** — payroll records and processing per employee
- **Performance evaluation** — track and record employee performance

## Tech stack

- **Java** with **JavaFX 22** (`javafx-controls`, `javafx-fxml`) for the UI
- **Maven** for build and dependency management
- **JUnit 5** (Jupiter + Platform Suite API) for testing
- File-based persistence for login/session data

## Architecture

The app follows an MVC-style structure:

```
src/main/java/
├── Controller/     # JavaFX controllers (Login, Dashboards, Add/Edit Employee, Payroll, Leave, Performance)
├── Models/         # Domain models + services (Employee, Payroll, LeaveManagement, PerformanceEvaluation)
├── data/           # File-based data access (LoginManager, FileHandler)
└── HelloApplication.java   # JavaFX entry point
```

## Testing

Each core model (`Employee`, `LeaveRequest`, `Payroll`, `PerformanceEvaluation`) has two parallel
test classes:

- **Standard tests** (e.g. `EmployeeTest`) — general unit/black-box coverage of expected behavior
- **White-box tests** (e.g. `EmployeeTestW`) — targeted at full code-path coverage: every
  constructor, getter/setter, and edge case (like invalid/negative values), explicitly written to
  expose gaps such as missing validation

Tests are aggregated into runnable suites (`AllTestsSuite`, `TestsSuite`) using JUnit Platform
Suite, so the full white-box or full regression suite can be run in one pass.

To run all tests:

```bash
mvn test
```

## Running the app

```bash
mvn clean javafx:run
```

(Requires a JavaFX-compatible JDK; JavaFX 22 controls/fxml are pulled in automatically via Maven.)
