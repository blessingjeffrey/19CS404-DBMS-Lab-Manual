# Experiment 1: Entity-Relationship (ER) Diagram

## Scenario Chosen:
Hospital

## ER Diagram:
![Screenshot 2025-04-29 083123](https://github.com/user-attachments/assets/4b5c26be-d9da-4cea-b369-df4e7b85d88c)


## Entities and Attributes:
- PATIENT

P-ID

PH-NO

AGE

GENDER

- DOCTOR

DEPT

QUALIFICATION

- NURSE

N-ID

E-ID

- RECEPTIONIST (No specific attributes shown)

- ROOMS

R-ID

TYPE

CAPACITY

- BILLS

B-ID

P-ID

AMOUNT

- TEST REPORT

TEST-TYPE

P-ID

RESULT

- RECORDS

R-NO

APP-NO



## Relationships and Constraints:
- CONSULTS

Between: PATIENT and DOCTOR

Constraint: Many-to-Many (M:N)

A patient can consult multiple doctors, and a doctor can be consulted by multiple patients.

- PAYS

Between: PATIENT and BILLS

Constraint: One-to-Many (1:N)

A patient can pay many bills, but each bill is linked to one patient.

- HAS

Between: PATIENT and TEST REPORT

Constraint: One-to-Many (1:N)

A patient can have multiple test reports, but each test report is linked to one patient.

- GOVERNS

Between: NURSE and ROOMS

Constraint: Many-to-Many (M:N)

A nurse can govern multiple rooms, and a room can be governed by multiple nurses.

- MAINTAINS

Between: RECEPTIONIST and RECORDS

Constraint: One-to-Many (1:M)

A receptionist maintains multiple records.



## Extension (Prerequisite / Billing):
-Entities Involved:
PATIENT,BILLS

Relationship:
PAYS (between PATIENT and BILLS)

Attributes Used:
In PATIENT: P-ID

In BILLS: B-ID, P-ID, AMOUNT

- Modeling Explanation:
Each PATIENT can pay multiple BILLS — this is shown via a 1:N relationship from PATIENT to BILLS.

The PAYS relationship logically ties each bill to a patient using P-ID as a foreign key in the BILLS entity.

Each BILL has a unique B-ID, an AMOUNT, and references a single PATIENT (P-ID).

This approach simplifies billing by:

Allowing historical tracking of multiple bills per patient.

Associating each billing record with the corresponding patient.

## Design Choices:
PATIENT, DOCTOR, NURSE, RECEPTIONIST

Chosen as entities because they represent key actors in the hospital system, each with their own attributes and responsibilities.

ROOMS

Modeled as a separate entity to manage space allocation, with attributes like TYPE and CAPACITY.

BILLS, TEST REPORT, RECORDS

Represent important operational and administrative data, each requiring independent storage and relationships to patients or staff.

-  Relationship Choices:
CONSULTS (PATIENT—DOCTOR)

Many-to-many to reflect real-life scenarios where multiple patients consult multiple doctors.

PAYS (PATIENT—BILLS)

One-to-many, as one patient can pay multiple bills.

HAS (PATIENT—TEST REPORT)

One-to-many, since a patient may have several test reports.

GOVERNS (NURSE—ROOMS)

Many-to-many because nurses may be assigned to multiple rooms and rooms may be overseen by multiple nurses during shifts.

MAINTAINS (RECEPTIONIST—RECORDS)

One-to-many, as one receptionist maintains several patient records.

## RESULT
The ER model successfully captures the core components of a hospital management system, including patients, doctors, nurses, rooms, billing, test reports, and administrative functions. It clearly defines:

Entities such as PATIENT, DOCTOR, NURSE, RECEPTIONIST, ROOMS, BILLS, TEST REPORT, and RECORDS.

Relationships like CONSULTS, PAYS, HAS, GOVERNS, and MAINTAINS to show interactions between the entities.

Attributes that support effective tracking of patient details, test outcomes, billing amounts, and room allocations.

Constraints (1:N, M:N) that mirror real-world hospital operations, allowing many-to-many or one-to-many interactions where appropriate.

This model lays the groundwork for designing a relational database or hospital software system that ensures accurate data flow, traceability of patient care, and efficient administrative management.
