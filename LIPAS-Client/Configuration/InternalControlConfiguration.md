### > Internal Control Configuration - `[InsuranceBusinessService].[InternalControlConfiguration]`

+ > The internal control table allows a user to modify certain aspects of the internal control review for outgoing disbursements (if enabled)
>> Note: All booleans must be lowercase false/true in the ConfigValue of the table.

---

## ⚙️ Feature Switch Configuration Settings

| Service                 | Description                                         | ConfigKey             |  Config Value            | Value Type    |   
|-------------------------|----------------------------------------------       |---------------        |--------------------------|-------|
| `LIPAS-Client`| Used to set the amount of days to disqualify a disbursement based on address change | `DAYS_SINCE_LAST_ADDRESS_CHANGE`           | `90`  | Int|                      
| `VBA-INSURANCE-CORE`| Used to enable the Termination of SDVI policies to suspense| `SDVI_SURRENDER_TO_SUSPENSE_FOR_VALI`| `true`| Boolean
|`VBA-INSURANCE-CORE`| Used to enable/disable all outgoing disbursements| `MASTER_DISBURSEMENT_PROCESSING`| `false`| Boolean|
|`VBA-INSURANCE-CORE`| Used to enable SDVI Cancellation specific refund processing| `SDVI_SURRENDER_DISBURSEMENT_PROCESSING`| `false`| Boolean|
|`LIPAS-Client`| Used to set the number of days since the last direct deposit change for diqualification of automated refund processing.| `NUMBER_OF_DAYS_SINCE_LAST_DIRECT_DEPOSIT_CHANGE`| `30` | Int|
|`LIPAS-Client`| Used to set the recent disbursement dollar threshold| `RECENT_DISBURSEMENT_DOLLAR_THRESHOLD`| `5000` | Decimal(10,2)|
|`LIPAS-Client`| Used to set the recent disbursement timeframe| `RECENT_DISBURSEMENT_TIMEFRAME_IN_DAYS`| `15` | Int

                        


---


> **[⬅️ Back to LIPAS-Client Configuration](../Configuration/LIPAS-Client.Configuration.md)**