# Procure-to-Pay (P2P) Flow Diagram

## Objective

Create a professional SAP Procure-to-Pay (P2P) process flow diagram using draw.io that demonstrates the complete purchasing lifecycle from Purchase Requisition to Vendor Payment.

---

# Diagram Requirements

The flow diagram must include:

* Process flow from Purchase Requisition to Vendor Payment
* SAP Transaction Code (T-Code) for every step
* SAP module involved
* Business role responsible
* Document flow between processes
* 3-Way Match validation at Invoice Verification (MIRO)

---

# Overall Process Flow

```text
Purchase Requisition
        ¦
        ¦ PR Number
        ?
Purchase Order
        ¦
        ¦ PO Number
        ?
Goods Receipt
        ¦
        ¦ Material Document
        ?
Invoice Verification
        ¦
        ¦ FI Document
        ?
Vendor Payment
```

---

# Step 1 — Purchase Requisition

### Purpose

A department identifies the need for materials or services and submits a purchase request.

| Property        | Value                     |
| --------------- | ------------------------- |
| Step            | Purchase Requisition      |
| SAP Module      | MM                        |
| T-Code          | `ME51N`                   |
| Business Role   | Purchaser                 |
| Output Document | Purchase Requisition (PR) |

Outgoing Document

```
PR Number
```

---

# Step 2 — Purchase Order

### Purpose

The purchasing department reviews the PR and creates an official Purchase Order for the vendor.

| Property        | Value               |
| --------------- | ------------------- |
| Step            | Purchase Order      |
| SAP Module      | MM                  |
| T-Code          | `ME21N`             |
| Business Role   | Purchaser           |
| Output Document | Purchase Order (PO) |

Incoming Document

```
PR Number
```

Outgoing Document

```
PO Number
```

---

# Step 3 — Goods Receipt

### Purpose

Warehouse personnel receive the ordered materials and record the receipt in SAP.

| Property        | Value             |
| --------------- | ----------------- |
| Step            | Goods Receipt     |
| SAP Module      | MM                |
| T-Code          | `MIGO`            |
| Business Role   | Warehouse         |
| Output Document | Material Document |

Incoming Document

```
PO Number
```

Outgoing Document

```
Material Document
```

Business Effect

* Inventory increases
* Stock becomes available

Financial Effect

* Goods Receipt/Invoice Receipt (GR/IR) account updated
* Inventory value increases

---

# Step 4 — Invoice Verification

### Purpose

Finance verifies the vendor invoice before payment.

| Property        | Value                  |
| --------------- | ---------------------- |
| Step            | Invoice Verification   |
| SAP Module      | MM + FI                |
| T-Code          | `MIRO`                 |
| Business Role   | Finance                |
| Output Document | FI Accounting Document |

Incoming Documents

* Purchase Order
* Goods Receipt
* Vendor Invoice

Outgoing Document

```
FI Document
```

---

# 3-Way Match Logic

At the MIRO step, SAP performs a mandatory validation called the **3-Way Match**.

The following three documents are compared:

```
Purchase Order
        ¦
        +-----------+
Goods Receipt       ¦
        ¦           ¦
        +------+    ¦
               ?    ?
          Vendor Invoice
               ¦
               ?
           SAP MIRO Check
```

SAP validates:

* Material
* Quantity
* Price
* Vendor
* Purchase Order Number

If all three documents match:

* Invoice is accepted.
* FI accounting document is generated.

If any mismatch exists:

* Invoice is blocked.
* Payment cannot proceed until the discrepancy is resolved.

---

# Step 5 — Vendor Payment

### Purpose

Finance posts payment to the vendor after successful invoice verification.

| Property      | Value          |
| ------------- | -------------- |
| Step          | Vendor Payment |
| SAP Module    | FI             |
| T-Code        | `F110`         |
| Business Role | Finance        |

Incoming Document

```
FI Document
```

Business Effect

* Vendor liability cleared
* Payment completed

Financial Effect

* Cash/Bank account decreases
* Vendor account is settled

---

# Complete Document Flow

```text
Purchase Requisition
        ¦
        ¦ PR Number
        ?
Purchase Order
        ¦
        ¦ PO Number
        ?
Goods Receipt
        ¦
        ¦ Material Document
        ?
Invoice Verification
        ¦
        ¦ FI Document
        ?
Vendor Payment
```

---

# Business Roles

| Process              | Responsible Role |
| -------------------- | ---------------- |
| Purchase Requisition | Purchaser        |
| Purchase Order       | Purchaser        |
| Goods Receipt        | Warehouse        |
| Invoice Verification | Finance          |
| Vendor Payment       | Finance          |

---

# SAP Modules

| Step                 | Module  |
| -------------------- | ------- |
| Purchase Requisition | MM      |
| Purchase Order       | MM      |
| Goods Receipt        | MM      |
| Invoice Verification | MM + FI |
| Vendor Payment       | FI      |

---

# SAP Transaction Codes

| Step                 | T-Code  |
| -------------------- | ------- |
| Purchase Requisition | `ME51N` |
| Purchase Order       | `ME21N` |
| Goods Receipt        | `MIGO`  |
| Invoice Verification | `MIRO`  |
| Vendor Payment       | `F110`  |

---

# Diagram Design Guidelines

Use the following layout when creating the draw.io diagram:

* Five large process boxes arranged from left to right.
* Each process box contains:

  * Step Name
  * SAP T-Code (displayed in a code-style font)
  * SAP Module
  * Business Role
* Connect the boxes with labeled arrows:

  * **PR Number**
  * **PO Number**
  * **Material Document**
  * **FI Document**
* Add a second layer below the **MIRO** process to illustrate the **3-Way Match** using three incoming arrows from:

  * Purchase Order
  * Goods Receipt
  * Vendor Invoice
* Clearly label the validation as **3-Way Match**.
* Use professional colors (blue for MM activities, green for warehouse, orange for finance) and align all elements consistently.

---

# Expected Output

**Diagram File**

```
P2P-flow.png
```

**Source File**

```
P2P-flow.drawio
```

---

# GitHub Repository Structure

```text
SAP-P2P-O2C
¦
+-- README.md
+-- business-processes.md
+-- P2P-flow.md
+-- diagrams/
¦   +-- P2P-flow.drawio
¦   +-- P2P-flow.png
+-- images/
```

---

# Learning Outcomes

After completing this diagram, you will understand:

* Complete SAP Procure-to-Pay lifecycle
* Responsibilities of Purchaser, Warehouse, and Finance
* Flow of business documents through the purchasing process
* Purpose of SAP MM and FI modules
* Usage of key SAP T-Codes (`ME51N`, `ME21N`, `MIGO`, `MIRO`, `F110`)
* How SAP performs the 3-Way Match before releasing vendor payments
* Integration between logistics and finance within the SAP ERP system
