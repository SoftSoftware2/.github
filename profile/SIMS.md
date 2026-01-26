# Documentació Tècnica – Prèvia al Desenvolupament

## 1. Introducció

### 1.1 Propòsit del document
Aquest document defineix l'anàlisi i el disseny tècnic de l'aplicació abans d'iniciar el desenvolupament. Serveix com a guia, però no és del tot rígida.

---

### 1.2 Abast del projecte
Aquest projecte està enfocat a desenvolupar una aplicació web multi-tenant, on les empreses contractants podran tenir la gestió de la seva flota de vehicles.

---

## 2. Descripció general de l'aplicació

### 2.1 Objectiu de l'aplicació
L'aplicació té un objectiu clar per al client: permetre gestionar la seva flota de vehicles, millorar-ne el control i obtenir beneficis mitjançant serveis d'ús compartit de vehicles (car sharing). A més, ofereix un sistema de ticketing B2C (business-to-consumer) per a la comunicació amb els clients.

---

### 2.2 Rols d'usuari
Rols principals de l'aplicació:

- **Superusuari** (`super_user`): gestiona les estadístiques globals de totes les empreses i administra recursos i serveis globals, p. ex. bases de dades, comptes d'administrador, integracions d'API (mapes) i subdominis.
- **Administrador d'empresa** (`company_admin`): gestiona l'empresa a la qual està assignat; té accés només a les estadístiques de la seva empresa. A la secció de vehicles pot consultar, crear, actualitzar i eliminar vehicles. Gestiona el sistema de ticketing amb els clients i l'administració d'usuaris de la seva empresa.
- **Treballador** (`worker`): gestiona els tickets amb els clients i pot consultar i actualitzar la informació dels vehicles.
- **Client** (`customer`): pot llogar un vehicle i crear tickets per sol·licitar ajuda o suport.

---

## 3. Requisits del sistema

### 3.1 Requisits funcionals
Funcionalitats que el sistema ha de complir.

- RF01: Gestió d'usuaris: registrar, autenticar (iniciar sessió) i restablir contrasenya.
- RF02: Control d'identitat i permisos: assignació de rols i permisos (superusuari, administrador, treballador, client).
- RF03: Gestió d'usuaris administratius: crear, consultar, actualitzar i eliminar usuaris i assignar rols.
- RF04: Gestió de vehicles: crear, consultar, actualitzar i eliminar vehicles (inclou dades tècniques i estat operatiu).
- RF05: Gestió d'empreses (multi-tenant): crear, consultar, actualitzar i eliminar empreses/clientes.
- RF06: Provisionament d'empresa: automatitzar la creació de l'estructura necessària per a cada empresa (base de dades/espai, subdomini/pàgina dedicada, endpoints, configuracions inicials).
- RF07: Lloguer/reservés de vehicles: reservar, confirmar, modificar i cancel·lar lloguers; gestionar disponibilitat.
- RF08: Pagaments i facturació: integrar pagaments (passarel·la), generar factures i gestionar estats de pagament.
- RF09: Sistema de ticketing: crear, assignar, comentar, tancar i eliminar tickets; historial de comunicació client–soporte.
- RF10: Notificacions: enviar notificacions per correu electrònic/push/SMS per esdeveniments rellevants (reserves, tickets, alertes).
- RF11: Informes i estadístiques: generar dashboards i informes per empresa i globals (ús de la flota, ingressos, incidents).
- RF12: Registre d'auditoria: logging d'operacions crítiques i activitats d'usuaris per a traçabilitat.
- RF13: Configuració per empresa: paràmetres personalitzables per empresa (polítiques, preus, plans, recursos disponibles).
- RF14: Cerca i filtres: cercar i filtrar vehicles, empreses i reserves per diversos criteris.
- RF15: Gestió de permisos sobre recursos: controlar l'accés a recursos (p. ex. visibilitat de vehicles per empresa).
- RF16: Recuperació i gestió d'errors: mostrar errors clars i permetre la reintenció d'operacions crítiques/sensibles (p. ex. pagaments fallits).

---

## 4. Casos d'ús

### 4.1 Cas d'ús: [Nom del cas d'ús]

| Camp | Descripció |
|------|-------|
| Actor | Usuari |
| Flux principal | |
| Resultat | |

---

## 5. Arquitectura del sistema

### 5.1 Tipus d'arquitectura
Descriu l'arquitectura utilitzada.

> Exemple:  
> Arquitectura client-servidor basada en API REST.

---

### 5.2 Comunicació entre components
Explica com es comuniquen el frontend i el backend.

---

## 6. Tecnologies utilitzades

- Frontend: Vite + Vue3 + TypeScript
- Backend: Laravel 
- Base de dades: Postgres 
- Control de versions: Git
- Altres eines: Projects Github, PgAdmin

---

## 7. Model de dades


### 7.1 Entitats de la base de dades

A continuació es mostren les taules principals amb els camps, tipus i restriccions.

#### Taula `users`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, autoincrement, not null |
| email | varchar(70) | not null, unique |
| pwd | text | not null |
| name | varchar(50) | not null |
| created_at | datetime | not null |
| updated_at | datetime |  |
| deleted_at | datetime |  |

#### Taula `companies`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, autoincrement, not null |
| created_by | int | not null |
| name | varchar(50) | not null |
| description | varchar(255) |  |
| cif | varchar(25) | not null, unique |
| db_conexion | varchar(255) | not null |
| db_user | varchar(255) | not null |
| db_pwd | text | not null |
| created_at | datetime | not null |
| updated_at | datetime |  |
| deleted_at | datetime |  |

**Notes:**
- Els camps marcats com a "xifrats" (db_conexion, db_user, db_pwd) han d'emmagatzemar-se en forma segura (p. ex. xifrat a la base de dades o gestionats per un sistema de secrets).
- `created_by` és una clau forana referenciant `users.id` i s'ha de validar la seva integritat.
- Afegir índexs a `email` i `cif` per millorar la consulta i garantir unicitat.


---

## 8. Seguretat

Descriu les mesures bàsiques de seguretat implementades.

- Autenticació d'usuaris
- Validació de dades
- Control d'accés per rols
- Implemntació de test, per a front/back.


---

## 9. Planificació del desenvolupament

| Fase | Descripció |
|-----|------------|
| Anàlisi | |
| Desenvolupament frontend | |
| Desenvolupament backend | |
| Proves | |

---

## 10. Conclusió

Resum final del document i la seva utilitat durant el desenvolupament del projecte.

```
