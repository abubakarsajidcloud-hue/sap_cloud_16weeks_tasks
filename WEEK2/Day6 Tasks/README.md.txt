# business-processes.md

# SAP Business Processes: Procure-to-Pay (P2P) and Order-to-Cash (O2C)

## Overview

Enterprise Resource Planning (ERP) systems such as SAP integrate multiple business departments into a single platform. Instead of each department working independently, SAP ensures that purchasing, warehouse, sales, finance, and management all work with the same real-time data.

Two of the most important business processes in SAP are:

* **Procure-to-Pay (P2P)** – How a company purchases goods and pays suppliers.
* **Order-to-Cash (O2C)** – How a company sells goods and collects payment from customers.

Understanding these two processes is essential because almost every manufacturing, retail, logistics, healthcare, banking, and automotive company depends on them every day.

---

# What is Procure-to-Pay (P2P)?

Procure-to-Pay (P2P) is the complete purchasing lifecycle that starts when a company needs materials or services and ends when the supplier receives payment.

### Business Goal

Acquire the correct goods or services:

* From the correct supplier
* At the agreed price
* In the required quantity
* Delivered on time
* Paid accurately

---

# Complete P2P Cycle

## Step 1 – Purchase Requisition (PR)

Business Need:

A department identifies that materials or services are required.

Example:

The production department needs 500 steel sheets.

Purpose:

* Internal request only
* No supplier involvement yet

---

## Step 2 – Purchase Order (PO)

**T-Code:** ME21N

Purchasing reviews the request and sends an official Purchase Order to the supplier.

The PO contains:

* Vendor
* Material
* Quantity
* Price
* Delivery date

Purpose:

Creates the legal agreement to purchase.

---

## Step 3 – Goods Receipt (GR)

**T-Code:** MIGO

The warehouse receives the goods and confirms delivery.

SAP updates:

* Inventory
* Purchase Order history
* Accounting documents

Important:

Inventory increases during Goods Receipt.

---

## Step 4 – Invoice Verification

**T-Code:** MIRO

The supplier sends an invoice.

SAP compares:

* Purchase Order
* Goods Receipt
* Vendor Invoice

Only matching invoices are accepted.

---

## Step 5 – Vendor Payment

**Example T-Code:** F110 (Automatic Payment)

Finance pays the supplier.

The P2P process is complete.

---

# What is Order-to-Cash (O2C)?

Order-to-Cash (O2C) is the complete sales process that begins when a customer places an order and ends when the company receives payment.

Business Goal:

Convert customer demand into company revenue.

---

# Complete O2C Cycle

## Step 1 – Sales Order

**T-Code:** VA01

The customer places an order.

SAP records:

* Customer
* Products
* Quantity
* Price
* Delivery date

No inventory changes occur.

---

## Step 2 – Delivery

**T-Code:** VL01N

Warehouse prepares the shipment.

SAP checks:

* Product availability
* Shipping information

Inventory still does not decrease.

---

## Step 3 – Goods Issue

**T-Code:** VL02N

This is the most important step.

SAP:

* Ships the goods
* Reduces inventory
* Posts Cost of Goods Sold (COGS)
* Creates accounting entries

Important:

Inventory decreases only at Goods Issue.

---

## Step 4 – Billing

**T-Code:** VF01

SAP generates the customer invoice.

Effects:

* Revenue recognized
* Accounts Receivable created

---

## Step 5 – Payment Receipt

**T-Code:** F-28

Customer pays.

SAP:

* Clears Accounts Receivable
* Updates bank balance

The O2C process is complete.

---

# Understanding the 3-Way Match

The 3-Way Match is one of SAP's most important financial control mechanisms.

Before paying a supplier, SAP compares three business documents.

1. Purchase Order (PO)
2. Goods Receipt (GR)
3. Vendor Invoice

If all three agree within configured tolerances, SAP allows the invoice to be posted.

If they do not match, SAP blocks the invoice for investigation.

---

# Why the 3-Way Match Matters

Without the 3-Way Match:

* Fake invoices could be paid.
* Duplicate invoices could be processed.
* Incorrect prices could go unnoticed.
* Companies might pay for goods that never arrived.

The 3-Way Match protects company cash and improves audit compliance.

---

# Fraud Prevention in SAP

SAP includes several controls to reduce fraud.

## 1. Three-Way Match

Ensures payment is made only after:

* Goods were ordered
* Goods were received
* Invoice matches

---

## 2. Duplicate Invoice Check

SAP checks:

* Vendor
* Invoice number
* Amount

Duplicate invoices can be blocked automatically.

---

## 3. Tolerance Limits

SAP allows only small differences in:

* Quantity
* Price

Large differences trigger an invoice block.

---

## 4. Invoice Blocking

Invoices with mismatches are blocked until reviewed.

---

# Segregation of Duties (SoD)

Segregation of Duties is an important internal control.

The same employee should **not** control the entire purchasing and payment process.

Example:

| Activity                    | Responsible Team      |
| --------------------------- | --------------------- |
| Create Purchase Requisition | Requesting Department |
| Create Purchase Order       | Purchasing            |
| Receive Goods               | Warehouse             |
| Verify Invoice              | Finance               |
| Approve Payment             | Accounts Payable      |

### Why is this important?

If one person could:

* Create the Purchase Order
* Receive the Goods
* Approve the Invoice
* Post the Payment

they could create fake suppliers and steal company money without detection.

SAP authorization roles are designed to separate these responsibilities.

---

# Real Failure Story – Procure-to-Pay (P2P)

A manufacturing company issued a Purchase Order worth **€2.3 million** for industrial machinery.

Before any machines were delivered, the supplier submitted an invoice requesting full payment.

During invoice verification:

* Purchase Order existed ?
* Goods Receipt did not exist ?
* Invoice existed ?

The 3-Way Match failed.

SAP blocked the invoice automatically.

The purchasing team investigated and confirmed that no equipment had been delivered.

The company avoided a €2.3 million fraudulent payment because the control worked as intended.

---

# Real Failure Story – Order-to-Cash (O2C)

A customer ordered 1,000 automotive parts.

The warehouse shipped the goods successfully.

However, the billing process failed due to a pricing configuration issue.

Result:

* Customer received the goods.
* No invoice was generated.
* Accounts Receivable was never created.
* Finance could not collect payment.

The issue was discovered during month-end reconciliation.

After correcting the pricing configuration, SAP generated the missing invoice and the customer completed payment.

This demonstrates why monitoring the billing process is critical for protecting company revenue.

---

# Key Differences Between P2P and O2C

| Procure-to-Pay (P2P)                 | Order-to-Cash (O2C)                |
| ------------------------------------ | ---------------------------------- |
| Company buys goods                   | Company sells goods                |
| Starts with Purchase Requisition     | Starts with Sales Order            |
| Ends with Vendor Payment             | Ends with Customer Payment         |
| Inventory increases at Goods Receipt | Inventory decreases at Goods Issue |
| Focuses on suppliers                 | Focuses on customers               |

---

# 10+ Key Points

1. SAP integrates purchasing, warehouse, sales, and finance into one system.
2. P2P manages the purchasing lifecycle from requisition to supplier payment.
3. O2C manages the sales lifecycle from customer order to payment receipt.
4. Inventory increases during **Goods Receipt (MIGO)** in P2P.
5. Inventory decreases during **Goods Issue (VL02N)** in O2C.
6. The 3-Way Match compares the Purchase Order, Goods Receipt, and Vendor Invoice.
7. Invoice verification prevents fraudulent or incorrect supplier payments.
8. Duplicate invoice checks help prevent paying the same invoice twice.
9. Segregation of Duties ensures no single employee controls the complete purchasing and payment process.
10. SAP authorization roles support strong internal controls and audit compliance.
11. SAP Basis engineers maintain the systems that keep these business processes available.
12. SAP Cloud engineers ensure the infrastructure, databases, backups, and monitoring support uninterrupted business operations.

---

# Conclusion

Procure-to-Pay and Order-to-Cash are the foundation of enterprise business operations in SAP. Together they manage how organizations purchase materials, produce goods, sell products, recognize revenue, and pay suppliers.

Understanding these processes is valuable not only for functional consultants but also for SAP Basis, SAP Cloud, and DevOps engineers, because technical issues directly affect business operations. A strong understanding of P2P, O2C, fraud prevention, and internal controls enables engineers to troubleshoot production problems more effectively and appreciate the business impact of maintaining a reliable SAP environment.
