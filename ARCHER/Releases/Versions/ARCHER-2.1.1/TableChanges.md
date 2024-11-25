# Database Table Changes 🔧

> **Release Version:** `v2.1.1`  
> **Release Date:** `2024-09-30`

---

---

## 📝 Modified Tables

### **1. Table Name: `Archer`**

- **Changes**:

  - **Added Column**: `BATCHID` (VARCHAR(255), NOT NULL, Default: `'pre-release 2.0'`)
  - **Added Column**: `TransactionID` (VARCHAR(150), NOT NULL, Default: `'pre-release 2.0'`) 
  - **Added Column**: `CorrespondenceGenerated` (CHAR(1), NULL, Default: `'default_value'`)
  - **Modified Column**: `existing_column` changed data type from INT to BIGINT
  - **Dropped Column**: `obsolete_column`

- **Reason for Changes**:

  > _Quote_: "Changes required to improve cross-application logging. Added support for [CommonLogs] and [WebServiceLogs] "

---

## 🔄 Migration Scripts

```sql
BEGIN TRANSACTION;

USE INSENTRY;

/*
ARCHER 2.1.1 Release:

https://jira.devops.va.gov/browse/VILN-17850
https://jira.devops.va.gov/browse/VILN-18306
*/

--Step 1:
--Alter schema of existing Archer table
ALTER SCHEMA [InsuranceBusinessService] TRANSFER dbo.[Archer];

        /*
            --Rollback Option
            ALTER SCHEMA dbo TRANSFER [InsuranceBusinessService].[Archer];

        */

--Step 2:
--Alter Table to Version 2.0 Schema
ALTER TABLE [InsuranceBusinessService].[Archer]
ADD BATCHID VARCHAR(255) NOT NULL DEFAULT 'pre-release 2.0',
TransactionID VARCHAR(150) NOT NULL DEFAULT 'pre-release 2.0',
CorrespondenceGenerated CHAR(1) NULL




--Step 3: Remove default constraint 
--Alter Table: Remove Default Constraint
ALTER TABLE [InsuranceBusinessService].[Archer]
DROP CONSTRAINT DF_Archer_BATCHID;

ALTER TABLE [InsuranceBusinessService].[Archer]
DROP CONSTRAINT DF_Archer_TransactionID;


--Step 4: Drop Deprecated Tables;
BEGIN TRANSACTION; --Replaced by [InsuranceBusinessService].Disbursement
DROP TABLE dbo.[Archer_Disbursement];
COMMIT TRANSACTION;
-- ROLLBACK TRANSACTION;

BEGIN TRANSACTION; --Replaced by [InsuranceBusinessService].CommonLogs
DROP TABLE dbo.[Archer.CommonLogs];
COMMIT TRANSACTION;
-- ROLLBACK TRANSACTION;

BEGIN TRANSACTION; --Replaced by [InsuranceBusinessService].DisbursementLedger
DROP TABLE dbo.[Archer_Disbursement_Ledger];
COMMIT TRANSACTION;
-- ROLLBACK TRANSACTION;

BEGIN TRANSACTION; --Replaced by [InsuranceBusinessService].Correspondence
DROP TABLE dbo.[Archer_Disbursement_Letters];
COMMIT TRANSACTION;
-- ROLLBACK TRANSACTION;

BEGIN TRANSACTION; --Unused structure - removing.
DROP TABLE dbo.[Archer_RunLog_Disbursements];
COMMIT TRANSACTION;
-- ROLLBACK TRANSACTION;
```

> **[⬅️ Back to ARCHER Release Notes](..//ARCHER-2.1.1/2.1.1.md)**
