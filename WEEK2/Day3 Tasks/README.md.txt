# SAP Fraud Prevention using the 3-Way Match (PO–GR–Invoice)

A comprehensive guide to one of SAP's most important financial control mechanisms: the **3-Way Match**.

This repository explains how SAP prevents fraudulent or incorrect vendor payments by comparing the **Purchase Order (PO)**, **Goods Receipt (GR)**, and **Vendor Invoice** before payment is approved.

---

# Project Overview

The **3-Way Match** is a financial control process within the Procure-to-Pay (P2P) cycle that protects organizations from fraud, duplicate payments, incorrect pricing, and invoices for goods that were never received.

This project covers:

* Business concepts
* SAP MM & FI integration
* Important T-Codes
* Architecture diagrams
* SAP Basis perspective
* SAP Cloud relevance
* Real-world fraud scenarios
* Interview preparation

---

# Learning Objectives

* Understand the SAP 3-Way Match process.
* Learn how Purchase Orders, Goods Receipts, and Invoices are validated.
* Understand invoice blocking mechanisms.
* Explore fraud prevention techniques in SAP.
* Learn the role of SAP Basis and SAP Cloud engineers.
* Prepare for SAP MM, SAP Basis, and ERP interviews.

---

# Business Flow

Business Requirement

?

Purchase Order (ME21N)

?

Goods Receipt (MIGO)

?

Invoice Verification (MIRO)

?

3-Way Match

?

Invoice Posted / Blocked

?

Vendor Payment

---

# Core Documents

| Document       | Purpose                     | SAP Module | T-Code |
| -------------- | --------------------------- | ---------- | ------ |
| Purchase Order | Agreement to purchase goods | MM         | ME21N  |
| Goods Receipt  | Confirms goods received     | MM         | MIGO   |
| Vendor Invoice | Supplier payment request    | MM/FI      | MIRO   |

---

# Important SAP T-Codes

| T-Code | Purpose                    |
| ------ | -------------------------- |
| ME21N  | Create Purchase Order      |
| MIGO   | Post Goods Receipt         |
| MIRO   | Invoice Verification       |
| MRBR   | Release Blocked Invoices   |
| OMR6   | Configure Tolerance Limits |

---

# Fraud Prevention Examples

## Missing Goods Receipt

Purchase Order ??

Goods Receipt ?

Invoice ??

Result:

Invoice Blocked

---

## Price Difference

PO Price: $1,000

Invoice Price: $1,500

Tolerance: 2%

Result:

Invoice Blocked

---

## Quantity Difference

PO

100 Units

?

GR

100 Units

?

Invoice

150 Units

Result:

Invoice Blocked

---

## Duplicate Invoice

Invoice Number:

INV-1001

Submitted Twice

Result:

SAP detects duplicate invoice and prevents duplicate payment.

---

# SAP Basis Perspective

SAP Basis engineers support the technical platform by:

* Monitoring application servers
* Monitoring work processes
* Troubleshooting MIRO failures
* Checking background jobs
* Managing authorizations
* Ensuring SAP availability

---

# SAP Cloud Perspective

Cloud engineers help maintain:

* SAP Application Servers
* AWS EC2
* EBS Storage
* CloudWatch Monitoring
* IAM Security
* Disaster Recovery
* High Availability

---

# Architecture

Users

?

SAP GUI / SAP Fiori

?

Application Server

?

SAP MM + SAP FI

?

SAP HANA Database

?

Invoice Validation

?

Payment

---

# Interview Questions

* What is the SAP 3-Way Match?
* Which three documents are compared?
* What happens if Goods Receipt is missing?
* What does MIRO do?
* What is MRBR used for?
* What is OMR6?
* How does SAP prevent duplicate payments?
* Why is the 3-Way Match important?

---

# Skills Demonstrated

* SAP MM
* SAP FI
* Invoice Verification
* Fraud Prevention
* Internal Controls
* ERP Business Processes
* SAP Basis Fundamentals
* SAP Cloud Basics
* Technical Documentation

---

# Repository Structure

```text
SAP-P2P-3-Way-Match/
¦
+-- README.md
+-- docs/
¦   +-- 3-Way_Match_Notes.pdf
¦   +-- Fraud_Prevention.pdf
¦   +-- Interview_Questions.md
¦   +-- Architecture_Notes.md
¦
+-- diagrams/
¦   +-- 3-Way_Match.drawio
¦   +-- P2P_Process.drawio
¦   +-- SAP_MM_FI.drawio
¦
+-- images/
¦   +-- Business_Flow.png
¦   +-- SAP_Architecture.png
¦   +-- Fraud_Prevention.png
¦   +-- PO_GR_Invoice.png
¦
+-- LICENSE
```

---

# Future Improvements

* SAP Fiori Invoice Verification
* Automatic Payment (F110)
* Invoice Blocking Configuration
* SAP S/4HANA Changes
* End-to-End P2P Process
* Real Production Case Studies

---

# Author

**Muhammad Abubakar Sajid Kamboh**

Aspiring SAP Basis | SAP Cloud | DevOps Engineer

Learning enterprise technologies by documenting SAP concepts, cloud infrastructure, Linux, and business processes through hands-on portfolio projects.

---

## License

This repository is intended for educational and portfolio purposes.
