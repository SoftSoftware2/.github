# Coding Conventions – Fleetly

> **Objective**: Define clear and agreed rules for the whole team to develop **readable, maintainable, scalable, and secure** code.
>
---

## 1. General project information
- **Project name**: Fleetly
- **Main technologies** (frontend, backend, DB, etc.):
    - **Frontend**: VUE
    - **Backend**: Laravel
    - **DBMS**: PostgreSQL, Pgadmin.

- **Language version**:
- **Conventions responsible**: Jordi Arnau, Francesc Quintó, and Iker Vericat.
- **Last review**: 20/01/2026

---

## 2. General principles
- **Priority**: readability and optimization
- **Focus** (clean code, domain-driven, component-based, etc.)
- **General rules applicable to the whole project**:
    - Language: Catalan (public messages and main documentation)
    - Few comments; only when needed to clarify complex logic
    - Short comments
    - Work following the SCRUM methodology

---

## 3. Project structure
- Structure:
  - Frontend:
    - Must have its own repository
    - Modular architecture will be used
    - Main function: display formatted views and capture user data
  - Backend:
    - Must have its own repository
    - Modular architecture will be used
    - Function: manage communication, process data, and validate users
- Mandatory files (README, `.env.example`, etc.)

---

## 4. Naming conventions
### 4.1 Files and folders
- Style:
    - File names: PascalCase
    - Variable names: camelCase
    - Function names: camelCase
    - Constants: SCREAMING_SNAKE_CASE
    - Routes: kebab-case
    - Folders: snake_case
    - Tables and DB names: snake_case
- Allowed prefixes/suffixes:
    - Frontend:
        - Composables: `use` → `useAuth.ts`
        - Views: `Page` → `LoginPage.vue`
        - Interfaces: `.interfaces.` → `users.interfaces.ts`
    - Backend:
        - Controllers: `Controller` → `AuthController.php`

### 4.2 Variables
- Language: English (code and identifiers)
- Semantics: descriptive names (avoid `x`, `y` except for iterators)
- Booleans: prefix with `is`, `has`, `can`, etc.

### 4.3 Functions and methods
- Pattern: verb + action. Examples: `getVehicleLocation()`, `storeCoordinate()`, `calculateDistance()`
- Recommended length: max 20–30 lines

### 4.4 Classes and components
- Naming pattern: PascalCase
- Singular

### 4.5 Constants
- Format: SCREAMING_SNAKE_CASE
- Recommended location:
    - Laravel: inside the Model or in `/config`
    - VUE: dedicated file `@/constants/index.js` or `const` object

---

## 5. Code style
- Indentation (spaces or tabs):
- Indentation size: 4 spaces for PHP (Laravel), 2 spaces for VUE and config files
- Use of blank lines:
    - One mandatory blank line between each method or function inside a class
    - End of file: one blank line

---

## 6. Comments and documentation
- Short comments only to understand complex code fragments
- Comment format:
    - PHP and Typescript:
        /**
         * Calculates the total distance traveled by a vehicle.
         */
- Documentation: `.md` files in a separate repository

---

## 7. Version control (Git)
### 7.1 Main branch
- Main branch name: `main`

### 7.2 Branching strategy
- Feature branches:
    - `feature/FT-1`
- Hotfix:
    - `hotfix/issue_to_fix`

### 7.3 Commits
- Message format: `Add/fix/bug: short description`
- Commit language: English (code and technical commits in English for consistency)

### 7.4 Pull Requests / Merge Requests
- Minimum requirements:
    - Descriptive title
    - Clear description
    - Warning-free code
- Mandatory review:
    - Compliance with code conventions
- Rules before merging:
    - Pass CI tests
    - Conflict resolution

---

## 10. Security
- Management of secrets and environment variables
- Protection against common attacks (XSS, CSRF, SQL Injection, etc.)
- Authentication and authorization
- Security best practices

---

## 11. Performance and optimization
- Performance best practices
- Lazy loading
- Image and asset optimization
- Caching

---

> **Final note**: This is a living document and must be updated as the project and team evolve.
