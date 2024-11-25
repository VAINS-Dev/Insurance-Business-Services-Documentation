### > Stored Procedure Configuration - [`[InsuranceBusinessService].[StoredProcedureConfiguration]`]
The stored procedure configuration table allows setting of various stored procedures used throughout the services.

⚙️ Stored Procedure Configuration Settings

| Service             | ConfigKey                                  | Config Value                                                                 | Value Type |
|---------------------|--------------------------------------------|-------------------------------------------------------------------------------|------------|
| `LIPAS-Client `       | SPNEXTCONTROLID                            | `VAC10DBSLPS400.LIFEPRO_CONV1.DBO.SPNEXTCONTROLID `                             | STRING     |
| `VALife-Notifier `    | GetLIPASSDVIPoliciesForNotice              | `VAC10DBSLPS400.INSENTRY.DBO.GetSDVINotificationRecords `                       | STRING     |
| `ARCHER`              | STORED_PROCEDURE_GETPREMIUMPAYMENTS        | `VAC10DBSLPS400.INSENTRY.DBO.ARCHER_GetPremiumPayments`                         | STRING     |
| `ARCHER`              | STORED_PROCEDURE_GETLOANPAYMENTS           | `VAC10DBSLPS400.INSENTRY.DBO.ARCHER_GetLoanPayments`                            | STRING     |
| `ARCHER`              | STORED_PROCEDURE_GETLIENPAYMENTS           | `null`                                                                          | STRING     |
| `ARCHER`              | STORED_PROCEDURE_GETFULLMATUREENDOWMENTREFUNDS | `null`                                                                       | STRING     |
| `ARCHER`              | STORED_PROCEDURE_GETSTANDARDREFUNDS        | `null`                                                                          | STRING     |
| `LIPAS-Client`        | STORED_PROCEDURE_GETACCOUNTINGCONTROLNUMBER | `VAC10DBSLPS400.INSENTRY.InsuranceBusinessService.GetAccountingControlNumber` | STRING     |
| `ARCHER`              | STORED_PROCEDURE_GETSUSPENSEBYPOLICYNUMBER | `VAC10DBSLPS400.INSENTRY.DBO.ARCHER_GetSuspenseByPolicyNumber`                  | STRING     |
| `ARCHER`              | STORED_PROCEDURE_GETLOANPAYMENTDATE        | `VAC10DBSLPS400.INSENTRY.DBO.ARCHER_GetLoanPaymentDate`                         | STRING     |
| `VBA-INSURANCE-CORE ` | STORED_PROCEDURE_GETSDVICANCELLATIONRECORDS | `VAC10DBSLPS400.INSENTRY.InsuranceBusinessService.GetSDVICancellationRecords` | STRING     |
| `LIPAS-Client `       | GETINTERNALCONTROLCHECK                    | `VAC10DBSLPS400.INSENTRY.InsuranceBusinessService.GetInternalControlCheck`      | STRING     |

---
> **[⬅️ Back to LIPAS-Client Configuration](../Configuration/LIPAS-Client.Configuration.md)**

