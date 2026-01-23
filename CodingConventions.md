# Coding Conventions – Fleetly

> **Objective**: To define clear and agreed-upon rules for the entire team to develop **readable, maintainable, scalable, and secure** code.
>
---

## 1. General Project Information
- **Project Name**: Fleetly
- **Main Technologies** (frontend, backend, DB, etc.): 
    - **Frontend**: VUE
    - **Backend**: Laravel
    - **DBMS**: PostgreSQL, Pgadmin.
    
- **Language Version**:
- **Convention Managers**: Jordi Arnau, Francesc Quintó and Iker Vericat.
- **Last Revision Date**: 20/01/2026

---

## 2. General Principles
- **Priority**: readability and optimization
- **Focus** (clean code, domain-driven, component-based, etc.)
- **General rules applicable to the entire project**:
    - Language: English
    - Few comments
    - Brief comments
    - Work using the SCRUM methodology.

---

## 3. Project Structure
- Structure:
  - Frontend: 
    - Must have its own repository
    - We will use a modular architecture. 
    - Main function: Display formatted views and capture user data
  - Backend: 
    - Must have its own repository
    - We will use a modular architecture.
    - Function: Manage communication, process data, and validate users.
- Mandatory files (README, .env.example, etc.)

---

## 4. Naming Conventions
### 4.1 Files and folders
- Style:
    - File names: PascalCase
    - Variable names: camelCase
    - Function names: camelCase
    - Constant names: SCREAMING_SNAKE_CASE
    - Routes: kebab-case
    - Folders: snake_case
    - Tables and DB Names: snake_case
- Allowed prefixes/suffixes:
    - FrontEnd:    
        - Composables: use -> useAuth.ts
        - Views: Page -> LoginPage.vue
        - Interfaces: .interfaces. -> users.interfaces.ts 
    - BackEnd:
        - Controllers: Controller -> AuthController.php

### 4.2 Variables
- Language: English
- Semantics: descriptive names (avoid x, y) except for iterators.
- Booleans: Must have a prefix (is, has, can..)
### 4.3 Functions and methods
- Verb + action. Example (getVehicleLocation(), storeCoordinate(), calculateDistance())
- Recommended maximum length: 20-30 lines

### 4.4 Classes and components
- Name pattern: PascalCase
- Singular

### 4.5 Constants
- Format: SCREAMING_SNAKE_CASE
- Location
    - Laravel: (Model or /config)
    - VUE: dedicated file @/constants/index.js / "const" object

---

## 5. Code Style
- Indentation (spaces or tabs): 
- Indentation size: 4 spaces for PHP (Laravel), 2 spaces for VUE and configuration files.
- Use of blank lines: 
    - One mandatory blank line between each method or function within a class.
    - End of file: One blank line

---

## 6. Comments and Documentation
- Brief comments only to understand complex code snippets
- Comment format
    - PHP and Typescript:
        /**
        * Calculates the total distance traveled by a vehicle.
        */
- Documentation in .md files in a separate repository.

---

## 7. Version Control (Git)
### 7.1 Main Branch
- Name of the main branch: Main

### 7.2 Branching Strategy
- Feature branches
    - feature/FT-1
- Hotfix
    - hotfix/issue_to_fix


### 7.3 Commits
- Commit message format: "Add/fix/bug: anything"
- Commit language: English
- Examples of good commits: Brief

### 7.4 Pull Requests / Merge Requests
- Minimum requirements
    - Descriptive title
    - Clear description
    - Code free of warnings
- Mandatory reviews
    - Compliance with coding conventions
- Rules before merging
    - Pass CI tests
    - Conflict resolution

---

## 10. Security
- Management of secrets and environment variables
- Protection against common attacks (XSS, CSRF, SQL Injection, etc.)
- Authentication and authorization
- Security best practices

---

## 11. Performance and Optimization
- Performance best practices
- Lazy loading
- Image and asset optimization
- Caching

---

> **Final Note**: This is a living document and should be updated according to the evolution of the project and the team.
