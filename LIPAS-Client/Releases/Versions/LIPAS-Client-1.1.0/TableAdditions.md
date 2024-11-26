
# Database Table Additions 📊

> **Release Version:** `v1.1.0`  
> **Release Date:** `2024-11-26`

---

## 📄 Overview

Summarize the new tables added in this release and their purpose.

---

## 🆕 New Tables

### **1. Table Name: `CommonLogs`**

> _Description_: Stores application common logging data

- **Columns**:

  | Column Name       | Data Type      | Constraints   | Description                 |
  | ----------------- | -------------- | ------------- | --------------------------- |
  | `LogDate`              | DATETIME            | NOT NULL   | Date of log entry           |
  | `LogLevel`            | VARCHAR(30)| NOT NULL | Log level of the log entry|
  | `ContextType`       | INT          | NULL      |Context Type - 1 = Policy Number, 2 = NameID|
  | `ContextID`     | VARCHAR(25)| NULL | ContextID related to ContextType|
  |`Source`     | VARCHAR(100) | NOT NULL| Source Application|
  |`Message` | VARCHAR(MAX) | NOT NULL | Log Message|
  |`StackTrace`| NVARCHAR(MAX) NULL| Stack Trace of any error or result|
  |`FunctionName`|VARCHAR(150) | NOT NULL | Source function that created the log entry|
  |`Category`|VARCHAR(150)| NOT NULL | Application Code Location Tracer|
  |`Guid`|VARCHAR(MAX) | NOT NULL | Unique transactionid or batchID associated with a log entry|

### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.1.0 - LIPAS-Client
USE Insentry;

COMMIT TRANSACTION;



BEGIN TRANSACTION;
--Create CommonLog Table;
CREATE TABLE [InsuranceBusinessService].[CommonLogs] (
    [LogDate]      DATETIME       NOT NULL,
    [LogLevel]     VARCHAR (30)   NOT NULL,
    [ContextType]  INT            NULL,
    [ContextID]    VARCHAR (25)   NULL,
    [Source]       VARCHAR (100)  NOT NULL,
    [Message]      VARCHAR (MAX)  NOT NULL,
    [StackTrace]   NVARCHAR (MAX) NULL,
    [FunctionName] VARCHAR (150)  NOT NULL,
    [Category]     VARCHAR (150)  NOT NULL,
    [Guid]         VARCHAR (MAX)  NOT NULL
);


COMMIT TRANSACTION;

```

---

### **2. Table Name: `WebServiceLogs`**

> _Description_: Stores web service request/response logs

- **Columns**:

  | Column Name     | Data Type | Constraints | Description |
  | -----------     | --------- | ----------- | ----------- |
  | `TransactionID` | VARCHAR(150) | NOT NULL             | Unique Transaction ID      |
  | `LogLevel` | VARCHAR(20) | NOT NULL | Log level of a log|
  | `RequestDate`| DATETIME | NOT NULL DEFAULT GETDATE()| Date of outgoing service request|
  | `ServiceURL` | VARCHAR(MAX)| NOT NULL| Service Url request was initiated too|
  | `RequestOptions`| NVARCHAR(MAX)| NOT NULL | Request options sent to service url|
  | `ResponseDate`| DATETIME| NULL | Datetime response was received|
  | `ResponseCode`| INT | NULL | Http response code|
  | `Response`| NVARCHAR | NULL | response header data|
  | `ResponseData`| NVARCHAR(MAX) | NULL | response data|

### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.1.0 - LIPAS-Client
USE Insentry;

COMMIT TRANSACTION;



BEGIN TRANSACTION;
--Create WebServiceLog Table;
CREATE TABLE [InsuranceBusinessService].[WebServiceLogs] (
    [TransactionID]  VARCHAR (150)  NOT NULL,
    [LogLevel]       VARCHAR (20)   NOT NULL,
    [RequestDate]    DATETIME       DEFAULT (getdate()) NOT NULL,
    [ServiceURL]     VARCHAR (MAX)  NOT NULL,
    [RequestOptions] NVARCHAR (MAX) NOT NULL,
    [ResponseDate]   DATETIME       NULL,
    [ResponseCode]   INT            NULL,
    [Response]       NVARCHAR (MAX) NULL,
    [ResponseData]   NVARCHAR (MAX) NULL
);


COMMIT TRANSACTION;

```
---
### **3. Table Name: `BatchControlFile`**

> _Description_: Stores daily batch information

- **Columns**:

  | Column Name     | Data Type | Constraints | Description |
  | -----------     | --------- | ----------- | ----------- |
  | `ID`| INT| IDENTITY(1,1) NOT NULL| Auto-incrementing identifier|
  | `BATCHID`| VARCHAR(255) | NOT NULL | Randomly generated daily batch identifier|
  | `ProcessingDate`| INT | NOT NULL | YYYYmmDD Format batch was generated|
  | `DateCreated` | DATETIME| NOT NULL | Date batchID was generated|


### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.1.0 - LIPAS-Client
USE Insentry;

COMMIT TRANSACTION;

BEGIN TRANSACTION;
--Create Batch Control File Table;
CREATE TABLE [InsuranceBusinessService].[BatchControlFile] (
    [ID]             INT           IDENTITY (1, 1) NOT NULL,
    [BATCHID]        VARCHAR (255) NOT NULL,
    [ProcessingDate] INT           NOT NULL,
    [DateCreated]    DATETIME      NOT NULL
);


COMMIT TRANSACTION;
```
---
### **3. Table Name: `Correspondence`**

> _Description_: Stores outgoing correspondence data

- **Columns**:

  | Column Name     | Data Type | Constraints | Description |
  | -----------     | --------- | ----------- | ----------- |
  | `BATCHID` | VARCHAR(150)| NOT NULL| Daily batch id|
  | `TransactionID`| VARCHAR(150) | NOT NULL| unique transaction id|
  | `ID`| INT| IDENTITY(1,1) NOT NULL| auto-incrementing ID|
  | `IncludeElectronicComms`| Char(1) | NULL| 'Y' = Yes, 'N'=No|
  | `RequestId`| INT| NULL| Request ID from SPNEXTCONTROLID LifePRO procedure|
  | `FormSubType`| NVARCHAR(50)| NOT NULL| Form Type|
  | `FormDescription`| VARCHAR(100)| NOT NULL | Brief form description|
  | `DateAdded`| DATETIME| DEFAULT GETDATE() NOT NULL| Date record added|
  | `DateLastUpdated`| DateTime| DEFAULT GETDATE() NOT NULL| Date record updated|
  | `PolicyNumber`| VARCHAR(50)| NOT NULL| PolicyNumber record|
  | `Processed`| CHAR(1)| NOT NULL | Processed Flag|
  | `SentToXPrint`| CHAR(1)| NOT NULL| Sent to Xprint Request Table flag|
  |`Xml`| XML| NULL| XML Data |
  

### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.1.0 - LIPAS-Client
USE Insentry;

COMMIT TRANSACTION;


BEGIN TRANSACTION;
--Create Correspondence table;

CREATE TABLE [InsuranceBusinessService].[Correspondence] (
    [BATCHID]                VARCHAR (150) NOT NULL,
    [TransactionID]          VARCHAR (150) NOT NULL,
    [ID]                     INT           IDENTITY (1, 1) NOT NULL,
    [IncludeElectronicComms] CHAR (1)      NULL,
    [RequestId]              INT           NULL,
    [FormSubType]            NVARCHAR (50) NOT NULL,
    [FormDescription]        VARCHAR (100) NOT NULL,
    [DateAdded]              DATETIME      DEFAULT (getdate()) NOT NULL,
    [DateLastUpdated]        DATETIME      DEFAULT (getdate()) NOT NULL,
    [PolicyNumber]           VARCHAR (50)  NOT NULL,
    [Processed]              CHAR (1)      NOT NULL,
    [SentToXPrint]           CHAR (1)      NOT NULL,
    [Xml]                    XML           NULL,
    PRIMARY KEY CLUSTERED ([TransactionID] ASC)
);

COMMIT TRANSACTION;

```


---
### **4. Table Name: `WorkQueue`**

> _Description_: Stores workqueue data for pending and historical processing.

- **Columns**:

  | Column Name     | Data Type | Constraints | Description |
  | -----------     | --------- | ----------- | ----------- |
  | `BATCHID`| VARCHAR(255)| NOT NULL| Daily batch identifier|
  | `ServiceType`| VARCHAR(45) NULL | Short descriptor for calling service|
  | `ID` | INT | IDENTITY(1,1) NOT NULL| Auto-incrementing ID|
  | `TransactionID`| VARCHAR(150)| NOT NULL | Unique transaction ID|
  | `CreateDate`| DATETIME| NOT NULL| Date record/row created|
  | `ActionType`| VARCHAR(50)| NOT NULL | Short descriptor for pending action|
  | `ActionDate`| DATETIME| DEFAULT GETDATE() NOT NULL| Date inserted for action|
  | `DateLastUpdated`| DATETIME| DEFAULT GETDATE() NOT NULL| Date record last updated|
  | `TransactionType`| INT| NOT NULL| Transaction type identifier|
  |`PolicyNumber`| Varchar(50)| NOT NULL| Policy number for pending action|
  | `WorkActionData`| NVARCHAR(MAX) | NULL| Workdata used for transaction processing|
  | `Status`| CHAR(1) | NOT NULL| Processing status, P=Processed, F=Failed, R=Rejected, N=New, I=In Progress
  | `QueueID`| INT| NOT NULL | Queue Process ID|
  | `IsArchived`| BIT| NOT NULL| Boolean flag if that data has been archived|



### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.1.0 - LIPAS-Client
USE Insentry;

COMMIT TRANSACTION;


BEGIN TRANSACTION;
--Create WorkQueue Table;
CREATE TABLE [InsuranceBusinessService].[WorkQueue] (
    [BATCHID]         VARCHAR (255)  NOT NULL,
    [ServiceType]     VARCHAR (45)   NULL,
    [ID]              INT            IDENTITY (1, 1) NOT NULL,
    [TransactionID]   VARCHAR (150)  NOT NULL,
    [CreateDate]      DATETIME       NOT NULL,
    [ActionType]      VARCHAR (50)   NOT NULL,
    [ActionDate]      DATETIME       DEFAULT (getdate()) NOT NULL,
    [DateLastUpdated] DATETIME       DEFAULT (getdate()) NOT NULL,
    [TransactionType] INT            NOT NULL,
    [PolicyNumber]    VARCHAR (50)   NOT NULL,
    [WorkActionData]  NVARCHAR (MAX) NULL,
    [Status]          CHAR (1)       NOT NULL,
    [QueueID]         INT            NOT NULL,
    [IsArchived]      BIT            CONSTRAINT [DEFAULT_WorkQueue_IsArchived] DEFAULT ((0)) NOT NULL,
    PRIMARY KEY CLUSTERED ([ID] ASC)
);

COMMIT TRANSACTION;
```
---

### **5. Table Name: `Disbursement`**
> _Release_: Not Released

> _Description_: Stores pending and released disbursements through automation

- **Columns**:

    | Column Name             | Data Type       | Constraints               | Description                                      |
    | ----------------------- | --------------- | ------------------------- | ------------------------------------------------ |
    | `ID`                    | INT             | IDENTITY(1,1) NOT NULL    | Auto Incrementing ID                             |
    | `GenerateCorrespondence`| CHAR(1)         | NULL                      | Indicates if correspondence should be generated - requires letterCode |
    | `LetterCode`            | VARCHAR(15)     | NULL                      | Letter code for LIPAS                            |
    | `BATCHID`               | NVARCHAR(150)   | NOT NULL                  | Daily batch id                                   |
    | `TransactionID`         | NVARCHAR(150)   | NOT NULL                  | Unique Transaction ID                            |
    | `DisbursementID`        | NVARCHAR(150)   | NOT NULL                  | Unique Disbursement ID                           |
    | `PolicyNumber`          | VARCHAR(15)     | NOT NULL                  | Policy number for record                         |
    | `InitiatingService`     | VARCHAR(50)     | NOT NULL                  | Service inserting the disbursement record        |
    | `DateCreated`           | DATETIME        | NOT NULL                  | Date the record was created                      |
    | `DateLastUpdated`       | DATETIME        | NOT NULL                  | Date the record was last updated                 |
    | `DisbursementReasonShort`| VARCHAR(80)    | NULL                      | Short description of the disbursement reason     |
    | `InternalControl`       | CHAR(1)         | NOT NULL                  | Internal control flag                            |
    | `ICReasonCode`          | INT             | NULL                      | Reason code for internal control                 |
    | `NAME_ID`               | INT             | NOT NULL                  | Identifier for the name associated with the disbursement |
    | `PendingRefundAmount`   | DECIMAL(10, 2)  | NOT NULL                  | Amount pending for refund                        |
    | `ContractCode`          | CHAR(1)         | NULL                      | Code for the contract                            |
    | `ContractStatus`        | CHAR(2)         | NULL                      | Status of the contract                           |
    | `ProductID`             | VARCHAR(10)     | NULL                      | Identifier for the product                       |
    | `AmountRefunded`        | DECIMAL(10, 2)  | NULL                      | Amount that has been refunded                    |
    | `DateRefunded`          | DATETIME        | NULL                      | Date the refund was processed                    |
    | `RefundStatus`          | CHAR(1)         | NOT NULL                  | Status of the refund                             |
    | `PolicyNoteLogged`      | CHAR(1)         | NULL                      | Indicates if a policy note has been logged       |
    | `LedgerEntryCreated`    | CHAR(1)         | NULL                      | Indicates if a ledger entry has been created     |
    | `PayeeName`             | VARCHAR(MAX)    | NULL                      | Name of the payee                                |
    | `DisbursementOption`    | CHAR(1)         | NOT NULL                  | Option for disbursement                          |
    | `DisbursementAmount`    | DECIMAL(10, 2)  | NULL                      | Amount of the disbursement                       |
    | `AccountingControlNumber`| BIGINT         | NULL                      | Control number for accounting                    |
    | `LetterGenerated`       | CHAR(1)         | NULL                      | Indicates if a letter has been generated         |
    | `ErrorCode`             | INT             | NULL                      | Error code associated with the disbursement      |

### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.1.0 - LIPAS-Client
USE Insentry;

COMMIT TRANSACTION;


BEGIN TRANSACTION;
-- Create Disbursement table;
CREATE TABLE [InsuranceBusinessService].[Disbursement] (
    [ID]                      INT             IDENTITY (1, 1) NOT NULL,
    [GenerateCorrespondence]  CHAR (1)        NULL,
    [LetterCode]              VARCHAR (15)    NULL,
    [BATCHID]                 NVARCHAR (150)  NOT NULL,
    [TransactionID]           NVARCHAR (150)  NOT NULL,
    [DisbursementID]          NVARCHAR (150)  NOT NULL,
    [PolicyNumber]            VARCHAR (15)    NOT NULL,
    [InitiatingService]       VARCHAR (50)    NOT NULL,
    [DateCreated]             DATETIME        NOT NULL,
    [DateLastUpdated]         DATETIME        NOT NULL,
    [DisbursementReasonShort] VARCHAR (80)    NULL,
    [InternalControl]         CHAR (1)        NOT NULL,
    [ICReasonCode]            INT             NULL,
    [NAME_ID]                 INT             NOT NULL,
    [PendingRefundAmount]     DECIMAL (10, 2) NOT NULL,
    [ContractCode]            CHAR (1)        NULL,
    [ContractStatus]          CHAR (2)        NULL,
    [ProductID]               VARCHAR (10)    NULL,
    [AmountRefunded]          DECIMAL (10, 2) NULL,
    [DateRefunded]            DATETIME        NULL,
    [RefundStatus]            CHAR (1)        NOT NULL,
    [PolicyNoteLogged]        CHAR (1)        NULL,
    [LedgerEntryCreated]      CHAR (1)        NULL,
    [PayeeName]               VARCHAR (MAX)   NULL,
    [DisbursementOption]      CHAR (1)        NOT NULL,
    [DisbursementAmount]      DECIMAL (10, 2) NULL,
    [AccountingControlNumber] BIGINT          NULL,
    [LetterGenerated]         CHAR (1)        NULL,
    [ErrorCode]               INT             NULL,
    PRIMARY KEY CLUSTERED ([ID] ASC)
);

COMMIT TRANSACTION;
```
---
### **6. Table Name: `DisbursementLedger`**
> _Release_: Not Released

> _Description_: Stores pending and released disbursements through automation

- **Columns**:

| Column Name     | Data Type | Constraints | Description |
| -----------     | --------- | ----------- | ----------- |
| `ID`| INT| IDENTITY(1,1) NOT NULL| Auto incrementing id|
| `BATCHID`                | NVARCHAR(150) | NOT NULL | Daily batch identifier |
| `TransactionID`          | NVARCHAR(150) | NOT NULL | Unique Transaction ID |
| `DisbursementID`         | NVARCHAR(150) | NOT NULL | Unique Disbursement ID |
| `PolicyNumber`           | VARCHAR(20)   | NOT NULL | Policy number for record |
| `DateCreated`            | DATETIME      | NOT NULL | Date the record was created |
| `DateLastUpdated`        | DATETIME      | NOT NULL | Date the record was last updated |
| `DisbursementAmount`     | DECIMAL(10,2) | NOT NULL | Amount of the disbursement |
| `AccountingControlNumber`| BIGINT        | NOT NULL | Control number for accounting |
| `DisbursementOption`     | CHAR(1)       | NULL     | Option for disbursement |
| `DateDisbursed`          | DATETIME      | NULL     | Date the disbursement was processed |
| `PayeeName`              | NVARCHAR(MAX) | NOT NULL | Name of the payee |
| `PayeeAddress1`          | NVARCHAR(MAX) | NULL     | Payee address line 1 |
| `PayeeAddress2`          | NVARCHAR(MAX) | NULL     | Payee address line 2 |
| `PayeeAddress3`          | NVARCHAR(MAX) | NULL     | Payee address line 3 |
| `City`                   | NVARCHAR(150) | NULL     | City of the payee |
| `State`                  | NVARCHAR(100) | NULL     | State of the payee |
| `Country`                | NVARCHAR(100) | NULL     | Country of the payee |
| `ZipCode`                | NVARCHAR(10)  | NULL     | Zip code of the payee |
| `ABANumber`              | VARCHAR(100)  | NULL     | ABA Number |
| `AccountNumber`          | VARCHAR(100)  | NULL     | Account Number |
| `PEXTR_RECORD_ID`        | VARCHAR(150)  | NULL     | PEXTR Record ID |
| `PEXTR_POLICY_NUMBER`    | VARCHAR(50)   | NULL     | PEXTR Policy Number |
| `PEXTR_TRANSACTION_DATE` | INT           | NULL     | PEXTR Transaction Date |
| `PEXTR_TRANSACTION_AMOUNT`| DECIMAL(10,2)| NULL     | PEXTR Transaction Amount |
| `PEXTR_INDIV_LAST_NAME`  | VARCHAR(150)  | NULL     | PEXTR Individual Last Name |
| `PEXTR_INDIV_FIRST_NAME` | VARCHAR(150)  | NULL     | PEXTR Individual First Name |
| `PEXTR_ADDR_LINE_1`      | VARCHAR(150)  | NULL     | PEXTR Address Line 1 |
| `PEXTR_ADDR_LINE_2`      | VARCHAR(150)  | NULL     | PEXTR Address Line 2 |
| `PEXTR_ADDR_LINE_3`      | VARCHAR(150)  | NULL     | PEXTR Address Line 3 |
| `PEXTR_ADDR_CITY`        | VARCHAR(150)  | NULL     | PEXTR Address City |
| `PEXTR_ADDR_STATE`       | VARCHAR(10)   | NULL     | PEXTR Address State |
| `PEXTR_ADDR_ZIP`         | VARCHAR(10)   | NULL     | PEXTR Address Zip |
| `PEXTR_ADDR_COUNTRY`     | VARCHAR(80)   | NULL     | PEXTR Address Country |
| `Status`                 | CHAR(1)       | NULL     | Processing status |

### Create Table:
```sql
BEGIN TRANSACTION;
--Release 1.1.0 - LIPAS-Client
USE Insentry;

COMMIT TRANSACTION;


BEGIN TRANSACTION;
--Create Disbursement Table;
CREATE TABLE [InsuranceBusinessService].[DisbursementLedger] (
    [ID]                       INT             IDENTITY (1, 1) NOT NULL,
    [BATCHID]                  NVARCHAR (150)  NOT NULL,
    [TransactionID]            NVARCHAR (150)  NOT NULL,
    [DisbursementID]           NVARCHAR (150)  NOT NULL,
    [PolicyNumber]             VARCHAR (20)    NOT NULL,
    [DateCreated]              DATETIME        NOT NULL,
    [DateLastUpdated]          DATETIME        NOT NULL,
    [DisbursementAmount]       DECIMAL (10, 2) NOT NULL,
    [AccountingControlNumber]  BIGINT          NOT NULL,
    [DisbursementOption]       CHAR (1)        NULL,
    [DateDisbursed]            DATETIME        NULL,
    [PayeeName]                NVARCHAR (MAX)  NOT NULL,
    [PayeeAddress1]            NVARCHAR (MAX)  NULL,
    [PayeeAddress2]            NVARCHAR (MAX)  NULL,
    [PayeeAddress3]            NVARCHAR (MAX)  NULL,
    [City]                     NVARCHAR (150)  NULL,
    [State]                    NVARCHAR (100)  NULL,
    [Country]                  NVARCHAR (100)  NULL,
    [ZipCode]                  NVARCHAR (10)   NULL,
    [ABANumber]                VARCHAR (100)   NULL,
    [AccountNumber]            VARCHAR (100)   NULL,
    [PEXTR_RECORD_ID]          VARCHAR (150)   NULL,
    [PEXTR_POLICY_NUMBER]      VARCHAR (50)    NULL,
    [PEXTR_TRANSACTION_DATE]   INT             NULL,
    [PEXTR_TRANSACTION_AMOUNT] DECIMAL (10, 2) NULL,
    [PEXTR_INDIV_LAST_NAME]    VARCHAR (150)   NULL,
    [PEXTR_INDIV_FIRST_NAME]   VARCHAR (150)   NULL,
    [PEXTR_ADDR_LINE_1]        VARCHAR (150)   NULL,
    [PEXTR_ADDR_LINE_2]        VARCHAR (150)   NULL,
    [PEXTR_ADDR_LINE_3]        VARCHAR (150)   NULL,
    [PEXTR_ADDR_CITY]          VARCHAR (150)   NULL,
    [PEXTR_ADDR_STATE]         VARCHAR (10)    NULL,
    [PEXTR_ADDR_ZIP]           VARCHAR (10)    NULL,
    [PEXTR_ADDR_COUNTRY]       VARCHAR (80)    NULL,
    [Status]                   CHAR (1)        NULL,
    CONSTRAINT [PK_DisbursementLedger] PRIMARY KEY CLUSTERED ([ID] ASC)
);

COMMIT TRANSACTION;

```

---

> **[⬅️ Back to Release-1.1.0 Release Notes](../LIPAS-Client-1.1.0/1.1.0.md)**