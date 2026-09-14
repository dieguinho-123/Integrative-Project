# Integrative Project Portfolio

## Team Members
* Diego Dael González Acuña
* Paul Daniel Ortiz Contreras
* José Fernando González Quiñonez

---

## 1. Use Case Model

![Use Case Diagram](casos-uso.png)

### Justification
This Use Case Diagram outlines the functional scope, external actors, and key interactions within the system boundaries. It defines the separation between public browsing capabilities and authenticated operations, establishing a structured interaction framework prior to backend implementation.

### Value to the Project
* **Actor & Role Demarcation:**
  * **Primary Users:** Divided into *Unregistered User* (browsing and basic searches) and *Registered User* (inheriting general Web User capabilities to book reservations and manage personal profiles).
  * **Business Owner:** Manages venue-specific operations, including business profile creation and promotional media management.
  * **External Services:** Incorporates secondary actors such as *Authentication Service* (identity management) and *Payment Service* (transaction processing).
* **Clear Functional Workflows:** 
  * *Exploration Flow:* Searching places automatically includes viewing place details (`<<include>>`), with the conditional capability to open the interactive map view (`<<extend>>`).
  * *Transactional Flow:* The `Make Reservation` use case is optionally extended by `Pay for reservation`, directly coupling the platform to the external payment gateway.

---

## 2. Class Model

![Class Diagram](clases.png)

### Justification
This UML Class Diagram models the core architecture of the platform, organizing user roles, venue listings, and reviews. It establishes an object-oriented foundation that decouples responsibilities, optimizes code maintainability, and provides an unambiguous structural blueprint for both data persistence and business logic.

### Value to the Project
* **Inheritance Hierarchy:** Centralizes identity and session management within the base `User` class (`login()`, `logout()`), which is inherited by `Diner` (search execution, review creation) and `Owner` (venue registration and updates), minimizing code redundancy.
* **Core Entities & Structural Associations:**
  * An `Owner` manages one or more `Establishment` instances.
  * An `Establishment` belongs to a `Category` and contains exactly one `Location` instance for mapping and distance calculations.
  * A `Diner` writes multiple `Review` records, each linked directly to a target `Establishment`.
* **Encapsulation & Implementation Readiness:** Defines clear visibility modifiers (+, -), explicit data types, and method signatures, enabling direct translation into clean, modular backend code.
