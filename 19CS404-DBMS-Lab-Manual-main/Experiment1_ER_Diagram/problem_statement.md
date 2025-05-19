# 🧪 Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose
Gain hands-on experience in designing ER diagrams that visually represent the structure of a database, including entities, relationships, attributes, and constraints.

---

## 🏥 Scenario Chosen: Hospital Database

---

## 🖼️ ER Diagram

![438538708-4b5c26be-d9da-4cea-b369-df4e7b85d88c](https://github.com/user-attachments/assets/21a064be-ccfc-4f67-9f3c-a459aca128c3)


---

## 📦 Entities and Attributes

### 1. `PATIENT`
- `P-ID` (Primary Key)
- `PH-NO`
- `AGE`
- `GENDER`
- `INSURANCE DETAILS` *(optional)*

### 2. `DOCTOR`
- `D-ID` (Primary Key)
- `NAME`
- `DEPT`
- `QUALIFICATION`
- `SPECIALIZATION`
- `CONTACT INFO`

### 3. `NURSE`
- `N-ID` (Primary Key)
- `E-ID` (Employee ID)

### 4. `RECEPTIONIST`
- `R-ID` (Primary Key)
- `NAME`
- `E-ID` (Employee ID)

### 5. `ROOM`
- `R-ID` (Primary Key)
- `TYPE` (e.g., ICU, General)
- `CAPACITY`

### 6. `BILL`
- `B-ID` (Primary Key)
- `P-ID` (Foreign Key)
- `AMOUNT`
- `DATE`

### 7. `TEST REPORT`
- `T-ID` (Primary Key)
- `TEST-TYPE`
- `P-ID` (Foreign Key)
- `RESULT`
- `DATE`

### 8. `RECORD`
- `R-NO` (Primary Key)
- `APP-NO` (Appointment Number)
- `P-ID` (Foreign Key)
- `DOCTOR ID`
- `DIAGNOSIS`
- `TREATMENT DETAILS`

---

## 🔗 Relationships and Constraints

### 1. `CONSULTS`
- **Between**: `PATIENT` ↔️ `DOCTOR`
- **Cardinality**: Many-to-Many (M:N)
- **Participation**: Total on `PATIENT`, Partial on `DOCTOR`

### 2. `PAYS`
- **Between**: `PATIENT` → `BILL`
- **Cardinality**: One-to-Many (1:N)
- **Participation**: Total on `BILL`, Partial on `PATIENT`

### 3. `HAS`
- **Between**: `PATIENT` → `TEST REPORT`
- **Cardinality**: One-to-Many (1:N)

### 4. `GOVERNS`
- **Between**: `NURSE` ↔️ `ROOM`
- **Cardinality**: Many-to-Many (M:N)

### 5. `MAINTAINS`
- **Between**: `RECEPTIONIST` → `RECORD`
- **Cardinality**: One-to-Many (1:N)

---

## 💳 Billing Extension

### Entities Involved
- `PATIENT`
- `BILL`

### Relationship: `PAYS`
- **Type**: One-to-Many (1:N)

### Explanation:
Each `PATIENT` may be associated with multiple `BILL` entries using the `PAYS` relationship. Each `BILL` includes:
- `B-ID`: Unique ID
- `P-ID`: Foreign key from `PATIENT`
- `AMOUNT`: Bill amount
- `DATE`: Payment date

### Benefits:
- Enables historical tracking of bills per patient
- Simplifies financial data management
- Links billing data accurately to patient identity

---

## ⚙️ Design Choices

### Entity Selection
- `PATIENT`, `DOCTOR`, `NURSE`, `RECEPTIONIST`: Core human actors
- `ROOM`, `BILL`, `TEST REPORT`, `RECORD`: Operational and data-driven entities

### Relationship Modeling
- **M:N** for `CONSULTS` and `GOVERNS` to reflect real-world flexibility
- **1:N** for `PAYS`, `HAS`, `MAINTAINS` for natural ownership and record tracking

### Assumptions
- Test reports are patient-specific
- Bills are per appointment or group of services
- Nurses and doctors work within departments (not deeply modeled here)

---

## ✅ Result
This ER model captures the essential components of a hospital management system, including:
- Clear **entities** and **attributes**
- Well-defined **relationships** with appropriate cardinality
- Realistic **constraints** mirroring hospital operations

The design supports implementation of a robust relational database or hospital software system.
