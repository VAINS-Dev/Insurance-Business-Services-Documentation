### > Feature Switch - `[InsuranceBusinessService].[FeatureSwitch]`

+ > The feature switch table disables/enables features both small and large using boolean flags. 
>> Note: All booleans must be lowercase false/true in the ConfigValue of the table.

---

## ⚙️ Feature Switch Configuration Settings

| Service                 | Description                                         | ConfigKey             |  Config Value            | Value Type    |   
|-------------------------|----------------------------------------------       |---------------        |--------------------------|-------|
| `ARCHER`| Used to enable the premium payment automation `req ARCHER v.2.1.1+` | `PREMIUM_PAYMENTS`           | `true`  | Boolean|                      
| `ARCHER`| Used to enable loan payment automation `req ARCHER v.2.1.1+`        | `LOAN_PAYMENTS`| `true` |Boolean|                           
| `VALIFE-NOTIFIER`| Non-Implemented Feature-                                   | `VALI_LETTER_GENERATION` | `true`| Boolean|
| `ARCHER` | Non-Implemented Feature                                            | `LIEN_PAYMENTS`| `false` | Boolean|
| `ARCHER` | Non-Implemented Feature                                            | `MATURE_ENDOWMENTS`| `false` | Boolean|
| `ARCHER` | Non-Implemented Feature                                            | `ARCHER_CREATE_WORKFLOW`| `false` | Boolean|
| `ARCHER` | `Requires v.2.1.1.+       `                                        | `PREMIUM_CORR_NOTIFICATIONS`| `false` | Boolean|
| `ARCHER` | `Requires v.2.1.1.+       `                                        | `LOAN_CORR_NOTIFICATIONS`| `false` | Boolean|
| `ARCHER` | Non-Implemented Feature                                            | `LIEN_CORR_NOTIFICATIONS`| `false` | Boolean|
| `ARCHER` | Non-Implemented Feature                                            | `DIV_CREDIT_TO_PAYPREMIUM_NOTIFICATIONS`| `false` | Boolean|
| `ARCHER` | Non-Implemented Feature                                            | `MATURE_ENDOWMENT_NOTIFICATIONS`| `false` | Boolean|
| `ARCHER` | Non-Implemented Feature                                            | `STANDARD_REFUND_NOTIFICATIONS`| `false` | Boolean|
| `LIPAS-Client` | Demonstrates if Workflow was available at app start                | `WORKFLOW_UNAVAILABLE`| `true` | Boolean|
| `LIPAS-Client` | Demonstrates if Insurance Services was available at app start      | `INSURANCE_SERVICES_AVAILABLE`| `false` | Boolean|
| `LIPAS-Client` | Enables Developer Mode - Pauses processing until confirmation      | `DEVELOPMENT_MODE`| `true` | Boolean|
| `VBA-INSURANCE-CORE` | Enables Cancel SDVI Processing     | `CANCEL_SDVI_PROCESSING`| `true` | Boolean|
| `LIPAS-Client` | Designates if Insurance Services is required     | `INSURANCE_SERVICES_INT_REQUIRED`| `false` | Boolean|
| `ARCHER` | Enables outgoing letters for SDVI Termiantion      | `CANCEL_SDVI_OUTGOING_REFUND_LETTERS`| `false` | Boolean|

                        


---

> **[⬅️ Back to LIPAS-Client Configuration](../Configuration/LIPAS-Client.Configuration.md)**