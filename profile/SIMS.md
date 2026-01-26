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

### 4.1 Cas d'ús: Gestió de vehicles

                      +-------------------------------+
                      | Administrador / Usuari gestor |
                      |          de flota             |
                      +-------------------------------+
                                   |
                                   |
                                   v
                           +-----------------+
                           | Gestió Vehicles |
                           +-----------------+
                           | - Afegir        |
                           | - Editar        |
                           | - Eliminar      |
                           | - Consultar     |
                           +-----------------+
                                   |
                                   |
                                   v
                           +-----------------+
                           | Resultat        |
                           +-----------------+
                           | - Vehicle creat |
                           | - Vehicle       |
                           |   actualitzat   |
                           | - Vehicle       |
                           |   eliminat      |
                           | - Llista de     |
                           |   vehicles      |
                           |   mostrada      |
                           +-----------------+

### 4.2 Cas d'ús: Gestió d’usuaris
                      +----------------------+
                      |   Administrador      |
                      +----------------------+
                               |
                               |
                               v
                       +--------------------+
                       | Gestió Usuaris     |
                       +--------------------+
                       | - Crear usuari     |
                       | - Editar usuari    |
                       | - Eliminar usuari  |
                       | - Consultar llista |
                       +--------------------+
                               |
                               |
                               v
                       +------------------------+
                       | Resultat               |
                       +------------------------+
                       | - Usuari registrat     |
                       | - Usuari modificat     |
                       | - Usuari eliminat      |
                       | - Llista d’usuaris     |
                       |   actualitzada         |
                       +------------------------+

### 4.3 Cas d'ús: Gestió de reserves
                      +-------------------------+
                      |    Usuari / Ciutadà     |
                      +-------------------------+
                               |
                               |
                               v
                       +--------------------+
                       | Gestió Reserves    |
                       +--------------------+
                       | - Consultar        |
                       |   vehicles         |
                       |   disponibles      |
                       | - Reservar vehicle |
                       | - Cancel·lar       |
                       |   reserva          |
                       +--------------------+
                                 |
                                 |
                                 v
                       +---------------------------+
                       | Resultat                  |
                       +---------------------------+
                       | - Reserva confirmada      |
                       | - Reserva cancel·lada     |
                       | - Llista d’events actual. |
                       +---------------------------+

### 4.4 Cas d'ús: Visualització de dades IoT
                      +---------------------------+
                      | Administrador / Analista  |
                      +---------------------------+
                                 |
                                 |
                                 v
                         +-------------------+
                         | Visualització     |
                         | Dades IoT         |
                         +-------------------+
                         | - Veure GPS       |
                         | - Veure bateria   |
                         | - Veure estat     |
                         |   vehicle         |
                         | - Alertes sensors |
                         +-------------------+
                                 |
                                 |
                                 v
                         +---------------------------+
                         | Resultat                  |
                         +---------------------------+
                         | - Dashboard actualitzat   |
                         | - Informació en temps real|
                         | - Tots els vehicles       |
                         |   mostrats correctament   |
                         +---------------------------+


### 4.5 Cas d'ús: Gestió de tiquets
                      +-------------------------------+
                      | Usuari / Ciutadà / Admin      |
                      +-------------------------------+
                                 |
                                 |
                                 v
                         +-------------------+
                         | Gestió Tiquets    |
                         +-------------------+
                         | - Crear tiquet    |
                         | - Consultar       |
                         | - Assignar        |
                         | - Resoldre        |
                         | - Tancar tiquet   |
                         +-------------------+
                                 |
                                 |
                                 v
                         +---------------------------+
                         | Resultat                  |
                         +---------------------------+
                         | - Tiquet creat            |
                         | - Tiquet actualitzat      |
                         | - Tiquet resolt / tancat  |
                         | - Llista de tiquets       |
                         |   actualitzada            |
                         +---------------------------+

---

## 5. Arquitectura del sistema

### 5.1 Tipus d'arquitectura

L'aplicació seguirà una arquitectura client‑servidor amb comunicació via API REST. Per facilitar escalabilitat i mantenibilitat s'adoptarà un enfoc modular tant al frontend com al backend.

- Frontend: aplicació SPA amb components reutilitzables i mòduls per domini (Vue 3 + TypeScript).
- Backend: arquitectura modular basada en MVC adaptada a mòduls (MMVC), on cada mòdul encapsula models, controllers, serveis, rutes i migrations.

Exemple d'estructura modular per al frontend (Vue 3 + Vite):

```
src/
├─ assets/
├─ modules/           # mòduls de domini (fleet/, rentals/, tickets/)
│  ├─ exemple/
│  │  ├─ components/
│  │  ├─ composable/    
│  │  ├─ views/
│  │  ├─ routes/
│  │  ├─ interfaces/
│  │  └─ store/
│  └─ tickets/
├─ router/
├─ store/             # pinia / vuex global
├─ services/          # serveis HTTP i integracions (api.ts, payments.ts)
├─ plugins/
└─ main.ts
```

Exemple d'estructura modular MMVC per a Laravel:

```
app/
├─ Modules/
│  ├─ Fleet/
│  │  ├─ Controllers/
│  │  ├─ Models/
│  │  ├─ Services/
│  │  ├─ Migrations/
│  │  └─ Routes/
│  └─ Tickets/
├─ Http/
│  └─ Controllers/      # controllers genèrics
├─ Providers/           # registrar mòduls i serveis
└─ Console/

routes/
└─ api.php
```

Notes per al backend:
- Cada mòdul registra les seves rutes i migration, utilitzarem Service i Providers per inicialitzar mòduls.

---

### 5.2 Comunicació entre components

La comunicació entre frontend i backend es farà principalment via API REST amb JSON. Principals consideracions:

- Autenticació: Tokens CSRF.
- Versionat d'API: usar `/api/v1/...` per compatibilitat.
- Errors: respostes amb codi HTTP, codi intern i missatge amigable.
- Temps real: WebSockets o serveis pub/sub per telemetria i notificacions en temps real si cal.


## 6. Tecnologies utilitzades

- Frontend: Vite + Vue3 + TypeScript
- Backend: Laravel 
- Base de dades: Postgres 
- Control de versions: Git
- Altres eines: Projects Github, PgAdmin

---

## 7. Model de dades


### 7.1 Entitats de la base de dades "Main"

A continuació es mostren les taules principals amb els camps, tipus i restriccions.

#### Taula `users`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, autoincrement, not null |
| email | varchar(70) | not null, unique |
| pwd | text | not null |
| name | varchar(50) | not null |
| created_at | timestamp | not null |
| updated_at | timestamp |  |
| deleted_at | timestamp |  |

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
| created_at | timestamp | not null |
| updated_at | timestamp |  |
| deleted_at | timestamp |  |

**Notes:**
- Els camps marcats com a "xifrats" (db_conexion, db_user, db_pwd) han d'emmagatzemar-se en forma segura (p. ex. xifrat a la base de dades o gestionats per un sistema de secrets).
- `created_by` és una clau forana referenciant `users.id` i s'ha de validar la seva integritat.
- Afegir índexs a `email` i `cif` per millorar la consulta i garantir unicitat.


---

### 7.2 Entitats de la base de dades "Tenant"

A continuació es documenten les taules específiques del tenant (esquema multi-tenant) amb camps, tipus i restriccions.

#### Taula `users`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, not null, autoincrement |
| email | varchar(70) | unique, not null |
| password | text | not null |
| role_id | int | not null |
| name | varchar(50) | not null |
| surname | varchar(50) |  |
| created_at | timestamp | not null |
| updated_at | timestamp | not null |
| deleted_at | timestamp |  |

#### Taula `roles`

#### Taula `roles`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, not null, autoincrement |
| name | varchar(50) | not null, unique |
| created_at | timestamp | not null |
| updated_at | timestamp | not null |
| deleted_at | timestamp |  |

#### Taula `permissions`

#### Taula `permissions`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, not null, autoincrement |
| name | varchar(50) | not null, unique |
| created_at | timestamp | not null |
| updated_at | timestamp | not null |
| deleted_at | timestamp |  |


#### Taula `roles_permissions`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| role_id | int | not null |
| permission_id | int | not null |
| created_at | timestamp | not null |
| updated_at | timestamp | not null |
| deleted_at | timestamp |  |

Nota: es recomana una PK composta `(role_id, permission_id)` per garantir unicitat.

#### Taula `vehicle_types`

#### Taula `vehicle_types`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, not null, autoincrement |
| name | varchar(50) | not null, unique |
| created_at | timestamp | not null |
| updated_at | timestamp | not null |
| deleted_at | timestamp |  |


#### Taula `vehicles`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, not null, autoincrement |
| license | varchar(15) | not null, unique |
| status | enum | values: `available`, `using`, `stopped` |
| vehicle_type | int | not null |
| created_at | timestamp | not null |
| updated_at | timestamp | not null |
| deleted_at | timestamp |  |

#### Taula `payment_forms`

#### Taula `payment_forms`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, not null, autoincrement |
| name | varchar(50) | not null |
| created_at | timestamp | not null |
| updated_at | timestamp | not null |
| deleted_at | timestamp |  |


#### Taula `rentals`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, not null, autoincrement |
| user_id | int | not null |
| vehicle_id | int | not null |
| payment_form_id | int | not null |
| exit_point | varchar(255) | not null |
| drop_off_point | varchar(255) | not null |
| created_at | timestamp | not null |
| updated_at | timestamp | not null |
| deleted_at | timestamp |  |


#### Taula `tickets`

| Camp | Tipus | Restriccions |
|------|-------|--------------|
| id | int | PK, not null, autoincrement |
| created_by | int | not null |
| assigned_id | int |  |
| vehicle_id | int | not null |
| status | enum | values: `solved`, `open`, `in_progress` |
| created_at | timestamp | not null |
| updated_at | timestamp | not null |
| deleted_at | timestamp |  |

---

**Observacions:**
- Es recomana declarar índexs per `email`, `license` i `cif` en les taules corresponents.
- Per enums (`status`), assegurar la definició en la migració/BD i gestionament d'estats en backend.
- Afegir mecanismes d'auditoria (created_by/updated_by) si es requereix traçabilitat detallada.

## 8. Seguretat

La seguretat és una prioritat en totes les capes de l'aplicació: autenticació, autorització, dades, infraestructura i processos. A continuació es recullen les mesures i bones pràctiques recomanades.

- **Autenticació**
        - Emmagatzemar contrasenyes amb un algorisme fort (bcrypt, Argon2) i salts únics.
        - Gestionar sessions amb tokens.

- **Autorització i control d'accés**
        - Implementar RBAC (roles) i verificacions a nivell de servei i de dades.
        - Aplicar principi de mínims privilegis.

- **Validació i sanejament**
        - Validar totes les dades d'entrada (servidor i client) i utilitzar consultes parametritzades/ORM per evitar injeccions SQL.
        - Codificar la sortida (output encoding) per evitar XSS.

- **Proteccions HTTP i headers segurs**
        - Implementar CSRF tokens per operacions que modifiquin estat.


- **Proves i revisió contínua**
        - Integrar test d'integracó en la pipeline CI.


---

## 9. Conclusió
Aquest document serveix com a guia inicial per poder desenvolupar a cap l'applicació. Aqui es recullen els requisits minims inicials (poden variar durant el temps). També aquest document, permeteix que noves persones es sumen a treballar amb el projectes, sense anar a ulls cecs. 

Per a mantenir el projecte, s'han de seguir els següents pasos:
- **Priotizar els requisists**
- **Mantenir el model de dades** (sempre que es pugue).
- **Coordinar el desplegament**
- **Mantindre coherencia amb les codeconventions** [CodingCoventions](CodingConventions.md)
```