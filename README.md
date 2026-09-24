# SWYNEX Technologies — Data Analyst Internship
## Task 1: Data Cleaning & Preparation

**Intern Name:** JARIPITI MADHUSUDHAN  
**Intern ID:** SWX-2026-000964  
**Domain:** Data & AI | Data Analyst Internship  
**Mentor:** Swapnil Gaikwad / Program Mentor  

---

### 1. Project & Dataset Overview
- **Dataset:** Online Retail Transactional Dataset (UCI Machine Learning Repository)
- **Domain:** Global E-Commerce & Retail Sales
- **Tool Used:** Microsoft Excel & Power Query Editor
- **Scope:** 540,000+ transactional line items spanning transactions between 01/12/2010 and 09/12/2011.

---

### 2. Data Quality Issues Identified
1. **Duplicate Records:** Identified and removed exact duplicate line-item transactions.
2. **Cancelled Orders & Negative Quantities:** Invoices starting with "C" and records with `Quantity <= 0` representing order reversals/cancellations rather than genuine sales.
3. **Price Anomalies & Noise:** Records containing `UnitPrice <= 0` representing inventory adjustments, damaged items, samples, or administrative write-offs.
4. **Text Inconsistencies:** Inconsistent casing and trailing whitespace across product descriptions.
5. **Missing Customer Identifiers:** Over 130,000 transaction records lacked `CustomerID` values due to guest/unregistered checkouts.
6. **Data Types & Revenue Metrics:** `InvoiceDate` needed temporal verification, and individual transaction line items lacked a calculated gross sales metric.

---

### 3. Cleaning & Transformation Steps (Power Query)
- **Removed Duplicates:** Executed table deduplication to preserve unique sales line items.
- **Quantity Filter:** Applied a numeric filter `Quantity > 0` to exclude cancellations and stock corrections.
- **UnitPrice Filter:** Filtered `UnitPrice > 0` to remove write-offs, free items, and zero-dollar adjustments.
- **Text Standardisation:** Applied `Trim` to remove leading/trailing whitespace and `Capitalize Each Word` to clean the `Description` column.
- **Handling Missing Customer IDs:** Replaced `null` values in `CustomerID` with `0` to denote guest/unregistered customer transactions without losing valid sales revenue.
- **Feature Engineering:** Added a calculated column `TotalAmount` using the formula:
  ```text
  [Quantity] * [UnitPrice]
