# Application Changes 🚀

> **Release Version:** `v2.1.1`  
> **Release Date:** `2024-09-30`

---

## 📄 Overview

Minor logical changes while overall processing improvements. Multi-Thread support was added to allow solution to process multiple policy records simultaneously allowing for quick cycle time.

---

## 🆕 New Features

1. **Feature Name**  
   _Description_: Multi-Thread Support
   _Impact_: Time and Speed to process improved by 75%

---

## 🔄 Improvements

- **Feature Name**  
  _Changes_: Loan payment history improvement
  _Benefits_: Improved methodology for retrieving and evaluating loan payment history

- **Feature Name**  
  _Changes_:  GetLoanPayments
  _Benefits_: Added functionality to remove payments that have had a processing issue in the past 3 business days

- **Feature Name**  
  _Changes_:  GetPremiumPayments
  _Benefits_: Added functionality to remove payments that have had a processing issue in the past 3 business days


---

## 🐞 Bug Fixes

- **Issue #XYZ**  
  _Fix_: Fixed an issue where a payment processed as part of conversion history was incorrectly relaying to the GetLoanPaymentDates stored procedure causing a rare posting-in-advance issue.
  _Affected Areas_: Loan Paymnet Processing


---

## ⚠️ Breaking Changes

> **Important**: LIPAS-Client Integration

- **Change Description**  
  _Impact_: Removes web-service calls from application in adoption of new client library

  _Rollback Path_: Backup current application version and rollback if issue occurs.

---

> **[⬅️ Back to ARCHER Release Notes](../ARCHER-2.1.1/2.1.1.md)**