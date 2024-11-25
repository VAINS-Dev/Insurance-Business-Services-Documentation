

# Database Table Additions 📊

> **Release Version:** `v1.0.4`  
> **Release Date:** `2024-11-25`

---

## 📄 Overview

Summarize the new tables added in this release and the purpose.

---

## 🆕 New Tables

### **1. Table Name: `CoreSdviCancellationActions`**

> _Description_: Tracks Cancellation actions processed by Cancel Sdvi for VALife Solution

- **Columns**:

  | Column Name                 | Data Type         | Constraints   | Description                 |
  | -----------------           | --------------    | ------------- | --------------------------- |
  | `ID`                        | INT               | IDENTITY(1,1) NOT NULL    | Auto Incrementing ID         |
  | `BatchID`                   | VARCHAR(255)      | NOT NULL                  | Daily batch Identifier          |
  | `TransactionID`             | VARCHAR(255)      | NOT NULL                  | Unique Transaction ID for Log tracing   |
  | `PolicyNumber`              | VARCHAR(14)       | NOT NULL                  | Insurance Policy Number     |
  | `TerminationDate`           | INT               | NOT NULL                  | Termination date in YYYYMMDD format                 |
  | `DateCreated`               | DATETIME          | NOT NULL DEFAULT GETDATE()| Record create timestamp     |
  | `DateLastUpdated`           | DATETIME          | NOT NULL DEFAULT GETDATE()| Record last update timestamp     |
  | `ReferToPSD`                | CHAR(1)           | NOT NULL                  | Indicator if record was referred for manual action     |
  | `PaidToSuspense`            | CHAR(1)           | NOT NULL                  | Indicates if action was taken to surrender policy to suspense     |
  | `ReferredForDisbursement`   | CHAR(1)           | NOT NULL                  | Indicates if record was referred to disbursement (If Enabled)     |
  | `DisbursementID`            | VARCHAR(255)      | NULL                      | Unique Disbursement ID used on Disbursement and Dis bursementLedger tables    |
  | `ErrorIndicator`            | BOOLEAN           | NOT NULL                  | 0 = False, 1 = True    |

### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.0.4 - VBA-INSURANCE-CORE
USE Insentry;

COMMIT TRANSACTION;

BEGIN TRANSACTION;
-- Create Core SDVI Cancellation Tracking Table
CREATE TABLE [InsuranceBusinessService].[CoreSdviCancellationActions] (
    [ID]                      INT           IDENTITY (1, 1) NOT NULL,
    [BATCHID]                 VARCHAR (255) NOT NULL,
    [TransactionID]           VARCHAR (255) NOT NULL,
    [PolicyNumber]            VARCHAR (14)  NOT NULL,
    [TerminationDate]         INT           NOT NULL,
    [DateCreated]             DATETIME      DEFAULT (getdate()) NOT NULL,
    [DateLastUpdated]         DATETIME      DEFAULT (getdate()) NOT NULL,
    [ReferToPSD]              CHAR (1)      NOT NULL,
    [PaidToSuspense]          CHAR (1)      NOT NULL,
    [ReferredForDisbursement] CHAR (1)      NOT NULL,
    [DisbursementID]          VARCHAR (255) NULL,
    [ErrorIndicator]          INT           NOT NULL,
    CONSTRAINT [PK_CoreSdviCancellationActions] PRIMARY KEY CLUSTERED ([ID] ASC)
);

COMMIT TRANSACTION;
```

---

### **2. Table Name: `DeductionLedger`**

> _Description_: Tracks Deduction changes or stops needed as a result of a cancelled SDVI policy. This table will be used to aid and assist for timely deduction stop/changes to ensure minimal Veteran Impact.

- **Columns**:

  | Column Name        | Data Type      | Constraints                 | Description |
  | -----------        | ---------      | -----------                 | ----------- |
  | `BATCHID`            |  VARCHAR(255)  | NOT NULL                  | Daily batch ID            |
  | `TransactionID`      |  VARCHAR(255)  | NOT NULL                  | Unique transaction ID            |
  | `NameID`             |  INT           | NOT NULL                  | LifePRO NameID            |
  | `NameCode`           |  VARCHAR(3)    | NOT NULL                  | First 3 Characters of Veterans last name            |
  | `PolicyNumber`       |  VARCHAR(14)   | NOT NULL                  | Veteran policy number            |
  | `DateCreated`        |  DATETIME      | NOT NULL DEFAULT GETDATE()| Date record was created           |
  | `TerminationEvent`   |  VARCHAR(80)   | NOT NULL                  | Short hand description of termination event            |
  | `TerminationDate`    |  INT           | NOT NULL                  | YYYYMMDD representation of Termination Date            |
  | `ModePremium`        |  DECIMAL(10,2) | NOT NULL                  | Policy Mode Premium amount            |
  | `LoanDeduction`      |  DECIMAL(10,2) | NOT NULL                  | Current Contract 2 LifePRO Deduction Amount            |
  | `LoanCPDeduction`    |  DECIMAL(10,2) | NOT NULL                  | Current Custom parameter LifePRO Deduction Amount            |
  | `DeductionType`      |  VARCHAR(10)   | NOT NULL                  | Deduction Type            |
  | `DeductionOffice`    |  VARCHAR(10)   | NOT NULL                  | Deduction Office            |
  | `OtherLSTDeductions` |  CHAR(1)       | NOT NULL                  | Y/N flag if other non-SDVI non-VMLI policy deductions exist            |



### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.0.4 - VBA-INSURANCE-CORE
USE Insentry;

COMMIT TRANSACTION;

BEGIN TRANSACTION;
--Create Deduction Ledger Table;
CREATE TABLE [InsuranceBusinessService].[DeductionLedger] (
    [BATCHID]            VARCHAR (255)   NOT NULL,
    [TransactionID]      VARCHAR (255)   NOT NULL,
    [NameID]             INT             NOT NULL,
    [NameCode]           VARCHAR (3)     NOT NULL,
    [PolicyNumber]       VARCHAR (14)    NOT NULL,
    [DateCreated]        DATETIME        DEFAULT (getdate()) NOT NULL,
    [TerminationEvent]   VARCHAR (80)    NOT NULL,
    [TerminationDate]    INT             NOT NULL,
    [ModePremium]        DECIMAL (10, 2) NOT NULL,
    [LoanDeduction]      DECIMAL (10, 2) NOT NULL,
    [LoanCPDeduction]    DECIMAL (10, 2) NOT NULL,
    [DeductionType]      VARCHAR (10)    NOT NULL,
    [DeductionOffice]    VARCHAR (10)    NOT NULL,
    [OtherLSTDeductions] CHAR (1)        NOT NULL
);

COMMIT TRANSACTION;


```


---


### **3. Table Name: `PendingImage`**

> _Description_: Tracks PDF documents committed to the network folder for indexing

- **Columns**:

  | Column Name         | Data Type     | Constraints | Description |
  | -----------         | ---------     | ----------- | ----------- |
  | `BATCHID`             | VARCHAR(255)  | NOT NULL    | Daily batchID            |
  | `TransactionID`       | VARCHAR(255)  | NOT NULL    | Unique TransactionID            |
  | `ContextID`           | VARCHAR(20)   | NOT NULL    | ContextID (PolicyNumber)            |
  | `ContextType`         | INT           | NOT NULL    | INT Descriptor for integer            |
  | `CreateDate`          | DATETIME      | NOT NULL    | Date record created            |
  | `Description`         | VARCHAR(50)   | NOT NULL    | Brief description of document            |
  | `DocumentType`        | INT           | NOT NULL    | Document Type INT            |
  | `PDFData`             | VARBINARY(MAX)| NULL        | Binary Data for Document            |
  | `DocRepoCommitted`    | CHAR(1)       | NULL        | Indicator if sent to DocRepo            |
  | `WorkflowCommitted`   | CHAR(1)       | NULL        | Indicator if sent to Workflow            |
  | `DateLastUpdated`     | DATETIME      | CONSTRAINT [DEFAULT_PendingImage_DateLastUpdated] DEFAULT (getdate()) NULL            |             |


### Create Table:
```sql
BEGIN TRANSACTION;

USE INSENTRY;
/* 
VBA-INSURANCE-CORE 1.0.4 Release

*/
COMMIT TRANSACTION;


BEGIN TRANSACTION;
-- Create Pending Image table;
CREATE TABLE [InsuranceBusinessService].[PendingImage] (
    [BATCHID]           VARCHAR (255)   NOT NULL,
    [TransactionID]     VARCHAR (255)   NOT NULL,
    [ContextID]         VARCHAR (20)    NOT NULL,
    [ContextType]       INT             NOT NULL,
    [CreateDate]        DATETIME        NOT NULL,
    [Description]       VARCHAR (50)    NOT NULL,
    [DocumentType]      INT             NOT NULL,
    [PDFData]           VARBINARY (MAX) NULL,
    [DocRepoCommitted]  CHAR (1)        NULL,
    [WorkflowCommitted] CHAR (1)        NULL,
    [DateLastUpdated]   DATETIME        CONSTRAINT [DEFAULT_PendingImage_DateLastUpdated] DEFAULT (getdate()) NULL
);

COMMIT TRANSACTION;

```


---


### **4. Table Name: `TerminationValuation`**

> _Description_: Tracks the value of policies that are terminated for historical use.

- **Columns**:

  | Column Name         | Data Type     | Constraints               | Description |
  | -----------         | ---------     | -----------               | ----------- |
  | `ID`                  | INT           |  IDENTITY(1,1) NOT NULL   | Auto-increment ID             |
  | `BATCHID`             | VARCHAR(255)  |  NOT NULL                 | Daily batch ID            |
  | `TransactionID`       | VARCHAR(255)  |  NOT NULL                 | Unique Transaction ID            |
  | `PolicyNumber`        | VARCHAR(14)   |  NOT NULL                 | Insurance policy number            |
  | `QuoteDate`           | INT           |  NOT NULL                 | Date Quoted in YYYYMMDD            |
  | `ETIPurchaseAmount`   | DECIMAL(10,2) |  NULL                     | Amount purchased for ETI            |
  | `ETIExpiration`       | INT           |  NULL                     | ETI Expiration Date            |
  | `ETITermination`      | INT           |  NULL                     | ETI Termination Date            |
  | `BaseCV`              | DECIMAL(10,2) |  NULL                     | Base Cash Value            |
  | `PuaCV`               | DECIMAL(10,2) |  NULL                     | PUA Cash Value            |
  | `UnappliedCash`       | DECIMAL(10,2) |  NULL                     | Pending Unapplied Cash            |
  | `UnprocessedPremium`  | DECIMAL(10,2) |  NULL                     | Unprocessed Premiums in Advanced            |
  | `LoanTotal`           | DECIMAL(10,2) |  NULL                     | Loan Principal plus Interest            |
  | `LoanPrincipal`       | DECIMAL(10,2) |  NULL                     | Loan balance            |  
  | `LoanInterest`        | DECIMAL(10,2) |  NULL                     | Loan interest to quote date            |
  | `TotalLienAmount`     | DECIMAL(10,2) |  NULL                     | Total lien amount derived from Custom parameters |
  | `TaxableGain`         | DECIMAL(10,2) |  NULL                     | Taxable gain - used to surrender processing, not relavant to VA.            |
  | SurrenderAmount     | DECIMAL(10,2) |  NULL                     | Total Surrender Amount            |

### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.0.4 - VBA-INSURANCE-CORE
USE Insentry;

COMMIT TRANSACTION;

BEGIN TRANSACTION;
-- Create Termination Valuation Table
CREATE TABLE [InsuranceBusinessService].[TerminationValuation] (
    [ID]                 INT             IDENTITY (1, 1) NOT NULL,
    [BATCHID]            VARCHAR (255)   NOT NULL,
    [TransactionID]      VARCHAR (255)   NOT NULL,
    [PolicyNumber]       VARCHAR (14)    NOT NULL,
    [QuoteDate]          INT             NOT NULL,
    [ETIPurchaseAmount]  DECIMAL (10, 2) NULL,
    [ETIExpiration]      INT             NULL,
    [ETITermination]     INT             NULL,
    [BaseCV]             DECIMAL (10, 2) NULL,
    [PuaCV]              DECIMAL (10, 2) NULL,
    [UnappliedCash]      DECIMAL (10, 2) NULL,
    [UnprocessedPremium] DECIMAL (10, 2) NULL,
    [LoanTotal]          DECIMAL (10, 2) NULL,
    [LoanPrincipal]      DECIMAL (10, 2) NULL,
    [LoanInterest]       DECIMAL (10, 2) NULL,
    [TotalLienAmount]    DECIMAL (10, 2) NULL,
    [TaxableGain]        DECIMAL (10, 2) NULL,
    [SurrenderAmount]    DECIMAL (10, 2) NULL,
    CONSTRAINT [PK_TerminationValuation] PRIMARY KEY CLUSTERED ([ID] ASC)
);

COMMIT TRANSACTION;

```


---


> **[⬅️ Back to Cancel-SDVI Release Notes](../../../VBA-INSURANCE-CORE.md)**