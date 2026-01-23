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

- RF01: El sistema ha de permetre registrar usuaris.
- RF02: El sistema ha de permetre iniciar sessió.
- RF03: El sistema ha de permetre crear registres.
- RF04: El sistema ha de permetre modificar registres.
- RF05: El sistema ha de permetre eliminar registres.

---

### 3.2 Requisits no funcionals
Condicions de qualitat i comportament del sistema.

- RNF01: L'aplicació ha de ser accessible des de navegadors moderns.
- RNF02: Les contrasenyes han d'emmagatzemar-se de forma xifrada.
- RNF03: El temps de resposta no ha de superar els 2 segons.

---

## 4. Casos d'ús

### 4.1 Cas d'ús: [Nom del cas d'ús]

| Camp | Descripció |
|------|------------|
| Actor | Usuari |
| Descripció | |
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

- Frontend:
- Backend:
- Base de dades:
- Control de versions:
- Altres eines:

---

## 7. Model de dades

### 7.1 Entitats principals

**Entitat 1**
- atribut1
- atribut2
- atribut3

**Entitat 2**
- atribut1
- atribut2
- atribut3

---

## 8. Seguretat

Descriu les mesures bàsiques de seguretat implementades.

- Autenticació d'usuaris
- Validació de dades
- Control d'accés per rols

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
