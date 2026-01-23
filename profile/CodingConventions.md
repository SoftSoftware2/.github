# Convencions de Codi – Fleetly

> **Objectiu**: Definir regles clares i acordades per tot l'equip per desenvolupar codi **llegible, mantenible, escalable i segur**.
>
---

## 1. Informació general del projecte
- **Nom del projecte**: Fleetly
- **Tecnologies principals** (frontend, backend, BD, etc.):
    - **Frontend**: VUE
    - **Backend**: Laravel
    - **SGBD**: PostgreSQL, Pgadmin.

- **Versió de llenguatge**:
- **Responsables de les convencions**: Jordi Arnau, Francesc Quintó i Iker Vericat.
- **Última revisió**: 20/01/2026

---

## 2. Principis generals
- **Prioritat**: llegibilitat i optimització
- **Focus** (clean code, domain-driven, component-based, etc.)
- **Regles generals aplicables a tot el projecte**:
    - Llenguatge: català (els missatges públics i la documentació principal)
    - Pocs comentaris; només quan calgui per aclarir lògica complexa
    - Comentaris breus
    - Treballar seguint la metodologia SCRUM

---

## 3. Estructura del projecte
- Estructura:
  - Frontend:
    - Ha de tenir el seu propi repositori
    - S'utilitzarà una arquitectura modular
    - Funció principal: mostrar vistes formatades i capturar dades d'usuari
  - Backend:
    - Ha de tenir el seu propi repositori
    - S'utilitzarà una arquitectura modular
    - Funció: gestionar la comunicació, processar dades i validar usuaris
- Fitxers obligatoris (README, `.env.example`, etc.)

---

## 4. Convencions de nom
### 4.1 Fitxers i carpetes
- Estil:
    - Noms de fitxers: PascalCase
    - Noms de variables: camelCase
    - Noms de funcions: camelCase
    - Constants: SCREAMING_SNAKE_CASE
    - Rutes: kebab-case
    - Carpetes: snake_case
    - Taules i noms de BD: snake_case
- Prefixos/sufixos permesos:
    - Frontend:
        - Composables: `use` → `useAuth.ts`
        - Vistes: `Page` → `LoginPage.vue`
        - Interfaces: `.interfaces.` → `users.interfaces.ts`
    - Backend:
        - Controllers: `Controller` → `AuthController.php`

### 4.2 Variables
- Llenguatge: anglès (codi i identificadors)
- Semàntica: noms descriptius (evitar `x`, `y`) excepte iteradors
- Booleans: prefixar amb `is`, `has`, `can`, etc.

### 4.3 Funcions i mètodes
- Patró: verb + acció. Exemples: `getVehicleLocation()`, `storeCoordinate()`, `calculateDistance()`
- Longitud recomanada: màxim 20–30 línies

### 4.4 Classes i components
- Patró de nom: PascalCase
- Singular

### 4.5 Constants
- Format: SCREAMING_SNAKE_CASE
- Ubicació recomanada:
    - Laravel: dins del Model o a `/config`
    - VUE: fitxer dedicat `@/constants/index.js` o objecte `const`

---

## 5. Estil de codi
- Indentació (espais o tabs):
- Mida d'indentació: 4 espais per PHP (Laravel), 2 espais per VUE i fitxers de configuració
- Ús de línies en blanc:
    - Una línia en blanc obligatòria entre cada mètode o funció dins d'una classe
    - Final de fitxer: una línia en blanc

---

## 6. Comentaris i documentació
- Comentaris breus només per entendre fragments de codi complexos
- Format de comentaris:
    - PHP i Typescript:
        /**
         * Calcula la distància total recorreguda per un vehicle.
         */
- Documentació: arxius `.md` en un repositori separat

---

## 7. Control de versions (Git)
### 7.1 Branca principal
- Nom de la branca principal: `main`

### 7.2 Estratègia de branching
- Branches de feature:
    - `feature/FT-1`
- Hotfix:
    - `hotfix/issue_to_fix`

### 7.3 Commits
- Format del missatge: `Add/fix/bug: descripció breu`
- Idioma dels commits: anglès (codis i commits tècnics en anglès per coherència)

### 7.4 Pull Requests / Merge Requests
- Requisits mínims:
    - Títol descriptiu
    - Descripció clara
    - Codi lliure d'advertiments
- Revisió obligatòria:
    - Compliment de les convencions de codi
- Regles abans de fer merge:
    - Passar les proves del CI
    - Resolució de conflictes

---

## 10. Seguretat
- Gestió de secrets i variables d'entorn
- Protecció contra atacs comuns (XSS, CSRF, SQL Injection, etc.)
- Autenticació i autorització
- Bones pràctiques de seguretat

---

## 11. Rendiment i optimització
- Bones pràctiques de rendiment
- Lazy loading
- Optimització d'imatges i actius
- Caché

---

> **Nota final**: Aquest és un document viu i s'ha d'actualitzar segons l'evolució del projecte i de l'equip.
