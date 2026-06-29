# SAP Order-to-Cash (O2C) Flow Diagram

## Project Overview

This project demonstrates the complete **Order-to-Cash (O2C)** business process in SAP ERP using a professionally designed **draw.io** flow diagram.

Unlike a basic process flow, this diagram also includes the **Financial Accounting (FI) layer**, illustrating how logistics transactions automatically generate accounting entries. This integration between **Sales & Distribution (SD)** and **Financial Accounting (FI)** is one of the key concepts expected in SAP interviews.

---

# Objectives

* Understand the complete Order-to-Cash lifecycle
* Learn the SAP modules involved in each process
* Understand the responsibilities of different business roles
* Visualize business document flow
* Learn how SD integrates with FI
* Understand automatic financial postings created during sales transactions

---

# Business Process Flow

```text
Customer Inquiry
        ¦
        ?
Sales Order
        ¦
        ?
Outbound Delivery
        ¦
        ?
Goods Issue
        ¦
        ?
Billing
        ¦
        ?
Incoming Payment
```

---

# SAP Process Steps

| Step              | T-Code  | SAP Module | Business Role |
| ----------------- | ------- | ---------- | ------------- |
| Sales Order       | `VA01`  | SD         | Sales         |
| Outbound Delivery | `VL01N` | SD         | Warehouse     |
| Post Goods Issue  | `VL02N` | SD/MM      | Warehouse     |
| Billing           | `VF01`  | SD/FI      | Finance       |
| Incoming Payment  | `F-28`  | FI         | Finance       |

---

# Business Document Flow

```text
Sales Order Number
        ¦
Delivery Number
        ¦
Material Document
        ¦
Billing Document
        ¦
Accounting Document
        ¦
Payment Document
```

---

# Financial Accounting Layer

A major feature of this project is the financial accounting layer, showing how operational activities automatically create accounting entries.

## 1. Post Goods Issue (PGI)

When goods leave the warehouse:

**Debit**

```text
Cost of Goods Sold (COGS)
```

**Credit**

```text
Inventory
```

Business Effect

* Inventory decreases
* Cost of Goods Sold is recognized

---

## 2. Billing (Customer Invoice)

When the customer invoice is created:

**Debit**

```text
Customer (Debtor / Accounts Receivable)
```

**Credit**

```text
Revenue
```

Business Effect

* Revenue is recognized
* Customer receivable is created

---

## 3. Incoming Payment

When the customer pays:

**Debit**

```text
Bank / Cash
```

**Credit**

```text
Customer (Accounts Receivable)
```

Business Effect

* Customer account is cleared
* Cash balance increases

---

# Integration Across SAP Modules

| SAP Module | Responsibility         |
| ---------- | ---------------------- |
| SD         | Sales and Distribution |
| MM         | Inventory Management   |
| FI         | Financial Accounting   |

The project demonstrates how a single sales transaction updates logistics, inventory, customer accounting, revenue recognition, and cash management within one integrated SAP ERP system.

---

# Diagram Features

The draw.io diagram includes:

* Complete O2C lifecycle
* SAP T-Codes
* SAP modules
* Business roles
* Document flow
* Financial accounting layer
* Automatic FI postings
* Professional layout suitable for interviews and portfolio projects

---

# Project Files

```text
SAP-P2P-O2C/
¦
+-- README.md
+-- business-processes.md
+-- O2C-flow.md
+-- diagrams/
¦   +-- O2C-flow.drawio
¦   +-- O2C-flow.png
+-- images/
```

---

# Key Learning Outcomes

After completing this project, you will understand:

* Complete Order-to-Cash business process
* SAP SD process flow
* Inventory movement during sales
* Financial postings generated automatically
* Revenue recognition
* Accounts Receivable lifecycle
* Integration between SD, MM, and FI
* Business document flow
* Enterprise process integration in SAP ERP

---

# Why This Project Matters

Many beginners memorize SAP transaction codes without understanding the underlying business process. This project demonstrates how logistics and finance work together in SAP ERP.

Understanding the financial accounting layer—such as **COGS**, **Inventory**, **Revenue**, and **Accounts Receivable** postings—shows a deeper understanding of SAP as an integrated enterprise system, making this project especially valuable for interviews and technical discussions.
