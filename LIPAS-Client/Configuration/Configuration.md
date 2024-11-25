### > Configuration - `[InsuranceBusinessService].[Configuration]`
+ > The configuration table contains application-specific configuration settings.
>> Note: All booleans must be lowercase false/true in the Config Value of the table.

---

## ⚙️ Configuration Settings

| Service/Application |Description | ConfigKey                              | Config Value                       | Value Type |
|---------------------|------------|----------------------------------------|------------------------------------|------------|
| `LIPAS-Client`      | Table Schema |`TABLE_SCHEMA`                         | `[InsuranceBusinessService]`       | `STRING`   |
| `LIPAs-Client`      | Log Table Name Designation |`LOG_TABLE_NAME`                       | `[CommonLogs]`                     | `STRING`   |
| `LIPAS-Client`      | How many log days should be kept|`LOG_DAYS_KEPT`                        | `10`                               | `INT`      |
| `LIPAS-Client`      | File path for if text logging is enabled|`TEXT_FILE_FILEPATH`                   | `../../../logs/`                   | `STRING`   |
| `LIPAS-Client`      | LifePRO CoderID for any main function| `ARCHER_MAIN_ACCOUNT`                  | `DAD1`                             | `CHAR`     |
| `ARCHER`            | LifePRO CoderID for Premium processing|`ARCHER_PREMIUM_ACCOUNT`               | `PR01`                             | `CHAR`     |
| `ARCHER`            | LifePRO CoderID for Loan processing |`ARCHER_LOAN_ACCOUNT`                  | `LN01`                             | `CHAR`     |
| `NULL`              | LifePRO CoderID for Lien processing|`ARCHER_LIEN_ACCOUNT`                  | `DSC1`                             | `CHAR`     |
| `NULL`              | LifePRO CoderID for refund processing|`ARCHER_REFUND_ACCOUNT`                | `WEBP`                             | `CHAR`     |
| `VBA-INSURANCE-CORE`| LifePRO CoderID for SDVI Termination processing|`ARCHER_SDVI_TERMINATION_ACCOUNT`      | `DSC1`                             | `CHAR`     |
| `LIPAS-Client`      | EXL LifePRO product endpoint|`EXL_LIFEPRO_PRODUCT_ENDPOINT`         | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | EXL LifePRO policy endpoint| `EXL_LIFEPRO_POLICY_ENDPOINT`          | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | EXL LifePRO claims endpoint| `EXL_LIFEPRO_CLAIMS_ENDPOINT`          | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | EXL LifePRO party endpoint| `EXL_LIFEPRO_PARTY_ENDPOINT`           | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | EXL LifePRO authz endpoint| `EXL_AUTHZ_EXTERNAL_ENDPOINT`          | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | Authorization service account email| `AUTH_EMAIL`                           | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | Authorization domain| `AUTH_AD_DOMAIN`                       | `VA`                               | `STRING`   |
| `LIPAS-Client`      | Authorization password| `AUTH_PASSWORD`                        | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | LIPAS MVI endpoint | `MVI_LIPAS_ENDPOINT`                   | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | Product API Key | `EXL_LIFEPRO_PRODUCT_KEY`              | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | Policy API Key | `EXL_LIFEPRO_POLICY_KEY`               | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | Claims API Key | `EXL_LIFEPRO_CLAIMS_KEY`               | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | Party API Key | `EXL_LIFEPRO_PARTY_KEY`                | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | LDS Workflow Endpoint | `LDS_WORKFLOW_SERVICE_ENDPOINT`        | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | LDS Common Service Endpoint | `LDS_COMMON_SERVICE_ENDPOINT`          | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | LDS API Key | `LDS_WORKFLOW_SERVICE_KEY`             | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      |  Must be `true` |`SQL_READ_ENABLED`                     | `true`                             | `BOOL`     |
| `LIPAS-Client`      |  Hostname for Database |`DB_HOST`                              | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      |  Username for DB access |`DB_USERNAME`                          | `EInsurance`                       | `STRING`   |
| `LIPAS-Client`      | Database password for username | `DB_PASSWORD`                          | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | Default database | `DB_DATABASE`                          | `DevData`                          | `STRING`   |
| `LIPAS-Client`      | Must be `true` | `DB_LOGGING_ENABLED`                   | `true`                             | `BOOL`     |
| `LIPAS-Client`      | Integrated security flag| `DB_INTEGRATED_SECURITY`               | `false`                            | `BOOL`     |
| `LIPAS-Client`      | Trust database connection|`DB_TRUSTCONNECTION`                   | `true`                             | `BOOL`     |
| `LIPAS-Client`      | Email communication custom parameter| `EMAIL_COMMUNICATIONS`                 | `52`                               | `INT`      |
| `LIPAS-Client`      | Text communication custom parameter|  `TEXT_COMMUNICATIONS`                  | `53`                               | `INT`      |
| `LIPAS-Client`      | Email and Text communication custom parameter|  `EMAIL_AND_SMS_COMMUNICATIONS`         | `54`                               | `INT`      |
| `LIPAS-Client`      | Cell phone number custom parameter|  `CELL_PHONE_NUMBER`                    | `58`                               | `INT`      |
| `LIPAS-Client`      | Loan repayment custom parameter| `LOAN_REPAYMENT_AMOUNT`                | `61`                               | `INT`      |
| `LIPAS-Client`      | Overpayment lien custom parameter| `OVERPAYMENT_LIEN`                     | `36`                               | `INT`      |
| `LIPAS-Client`      | Premium lien custom parameter| `PREMIUM_LIEN`                         | `35`                               | `INT`      |
| `LIPAS-Client`      | Administrative lien custom parameter|`ADMINISTRATIVE_LIEN`                  | `41`                               | `INT`      |
| `LIPAS-Client`      | Incompetency custom parameter| `INCOMPETENCY`                         | `38`                               | `INT`      |
| `LIPAS-Client`      | ICN custom parameter| `ICN`                                  | `52`                               | `INT`      |
| `LIPAS-Client`      | XPRINT_REQUEST Table location | `XPRINT_DatabaseTable_Location`        | `DevData`                          | `STRING`   |
| `LIPAS-Client`      | LifePRO CoderID System account |`SYSTEM_ACCOUNT`                       | `DSC1`                             | `STRING`   |
| `LIPAS-Client`      |  LifePRO Database `[LIFEPRO_CONV]` & `[LIFEPRO]`|`LIFEPRO_DATABASE`                     | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      | Enables web service request/response logging| `WEB_SERVICE_DETAIL_LOGGING`           | `true`                             | `BOOL`     |
| `LIPAS-Client`      | Enables SQL logging| `SQL_LOGGING`                          | `true`                             | `BOOL`     |
| `LIPAS-Client`      | Enables Text File logging| `TEXT_FILE_LOGGING`                    | `false`                            | `BOOL`     |
| `ARCHER`            | Enables ADHOC Identifier processing for ARCHER| `ADHOC_ARCHER_BATCH_IDENTIFIER`        | `NULL`                             | `STRING`   |
| `LIPAS-Client`      |  Email for Insurance Services Auth|`INSURANCE_SERVICES_EMAIL`             | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      |  Password for Insurance Services Auth| `INSURANCE_SERVICES_PASSWORD`          | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      |  Endpoint for Insurance Services Auth| `INSURANCE_SERVICES_ENDPOINT`          | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      |  API Key for Insurance Services Auth| `INSURANCE_SERVICES_API_KEY`           | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      |  LDS Underwriting Endpoint | `LDS_UNDERWRITING_SERVICE_ENDPOINT`    | *\[Redacted\]*                     | `STRING`   |
| `VBA-INSURANCE-CORE`|  Template for PDF production for Cancel Sdvi processing| `CANCEL_SDVI_TEMPLATE_NAME`            | `CancelSdviTerminationTemplate.pdf`| `STRING`   |
| `VBA-INSURANCE-CORE`| Network path for saving of Cancel SDVI PDF's|`CANCEL_SDVI_NETWORK_PATH`             | *\[Redacted\]*                     | `STRING`   |
| `LIPAS-Client`      |  Custom parameter for Fraud| `FRAUD_INDICATOR`                      | `45`                               | `INT`      |
| `LIPAS-Client`      |  Development SQL logging |`DEVELOPMENT_SQL_LOGGING`              | `true`                             | `BOOL`     |
| `LIPAS-Client`      |  Accounts Receivable custom parameter| `ACCOUNTS_RECEIVABLE`                  | `33`                               | `INT`      |
| `VBA-INSURANCE-CORE`|  LifePRO reason code for SDVI Cancellation processing|`SDVI_CANCELLATION_REASON_CODE`        | `14`                               | `INT`      |
| `VBA-INSURANCE-CORE`|  SDVI Cancellation Custom Parameter|`SDVI_CANCELLATION_DUE_FOR_VALIFE_CPARM`| `86`                             | `INT`      |
---

> **[⬅️ Back to LIPAS-Client Configuration](../Configuration/LIPAS-Client.Configuration.md)**