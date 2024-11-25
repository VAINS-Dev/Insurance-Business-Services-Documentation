# API Versioning Release Document 📄

> **Application:** `LIPAS-Client`
> **Release Version:** `v1.0.0`  
> **Release Date:** `2024-08-01`
> **Release Type:** `preview`

---

## 📄 Overview

* This document outlines the changes made to the API endpoints, including additions, modifications, and deletions to the LIPAS-Client library.

---

## 📝 API Changes

### Authorization - Authz
| Endpoint                | Use Case                          | Application Leveraged In | Change Type | Description                                                                 | Owner | Version|
|-------------------------|-----------------------------------|--------------------------|-------------|-----------------------------------------------------------------------------|-------|-------|
| `/authz/token`      | Retrieve token from LifePRO Service            | LIPAS-Client    | Maintain    |                          | LifePRO      |   v.20.SP4      |

### Claim API - LPRESTClaim
| Endpoint                | Use Case                          | Application Leveraged In | Change Type | Description                                                                 | Owner | Version|
|-------------------------|-----------------------------------|--------------------------|-------------|-----------------------------------------------------------------------------|-------|-------|
| `/v1/Claim/${GUID}/UpdateDeathClaimHeader` | Update claim header             | N/A                    | Added      |   | LifePRO       | v.20.SP4         |
| `/v2/Claim/${GUID}/01/${this.PolicyNumber}/GetClaimList`  | Get Pending Claim List    | N/A                    | Added    |                       | LifePRO      | v.20.SP4          |

### Party API - LPRestParty
| Endpoint                | Use Case                          | Application Leveraged In | Change Type | Description                                                                 | Owner | Version|
|-------------------------|-----------------------------------|--------------------------|-------------|-----------------------------------------------------------------------------|-------|-------|
|`/v1/Address/AddAddress` | Add Address to NameRecord | | Added| | LifePRO | v.20.SP4|
|`/v1/Address/GetAddress` | Get Address  | | Added | | LifePRO | v.20.SP4|
|`/v1/Address/GetAddressByNameID`| Gets Address by NameID | | Added | | LifePRO | v.20.SP4|
| `/v1/Address/${this.PartyID_NameID}/${GUID}/GetPrimaryAddress`| Gets Primary Address by NameID| | Added| | LifePRO | v.20.SP4|
| `/v1/EFT/GetEFT`| Gets EFT by NameID | | Added| |LifePRO | v.20.SP4 |
| `/v1/EFT/InsertEFT` | Inserts EFT by NameID || Added || LifePRO | v.20.SP4|
| `/v1/EFT/UpdateEFT` | Updates EFT by NameID || Added || LifePRO | v.20.SP4|
| `/v1/EFT/DeleteEFT`| Deletes EFT by NameID || Added || LifePRO | v.20.SP4 |
| `/v1/PartyCustomParameter/${GUID}/${this.NameID}/getCustomParameter` | Retrieves party custom parameters by NameID| | Added|| LifePRO| v.20.SP4|
|`/v1/PartyCustomParameter/${GUID}/${this.NameID}/${this.ParamDefinitionID}/getCustomParameter`| Retrieves party custom parameters by definition ID| | Added|| LifePRO | v.20.SP4|
|`/v3/Party/${GUID}/PartySearch`| Executes a party search by NameID, SSN or Name||Added| | LifePRO | v.20.SP4|
|`/v4/Party/${GUID}/${this.NameID}/GetPartyRelationships`| Gets Relationships associated with a NameID| | Added| |LifePRO | v.20.SP4|

### Policy API - LPRestPolicy
| Endpoint                | Use Case                          | Application Leveraged In | Change Type | Description                                                                 | Owner | Version|
|-------------------------|-----------------------------------|--------------------------|-------------|-----------------------------------------------------------------------------|-------|-------|
|`/v1/Report/AccountingReportByAccount/${GUID}` | Retrieves accounting history data | | Added || LifePRO | v.20.SP4|
|`/v1/Policy/ChangePremiumDetails`| Changes premium details mode/method/option|| Added| | LifePRO | v.20.SP4|
|`/v1/Quote/DividendOptionChange` | Changes a policy dividend option || Added || LifePRO | v.20.SP4|
|`/v1/Loan/GetAllLoanList/${GUID}/01/${this.PolicyNumber}` | Retrieves loan history data || Added || LifePRO | v.20.SP4|
|`/v1/Policy/GetBenefitDetails`| Gets policy Benefit Data|| Added|| LifePRO | v.20.SP4|
|`/v1/PolicyCustomParameter/GetPolicyParameters`| Gets policy parameters|| Added|| LifePRO| v.20.SP4|
|`/v1/PolicyCustomParameter/InsertPRMPDetails`| Inserts a new policy custom parameter|| Added|| LifePRO|v.20.SP4|
|`/v1/Premium/ProcessManualAccounting/${GUID}` | Processes policy manual accounting || Added|| LifePRO |v.20.SP4|
|`/v1/Policy/ProcessReverseAndRecompute/${GUID}`| Processes reversal of anniversary|| Added|| LifePRO | v.20.SP4|
|`/v1/Policy/ProcessSuspenseRefund/${GUID}`| Process suspense refund|| Added|| LifePRO| v.20.SP4|
| `/v1/Policy/UpdatePolicyStatus/01/${this.PolicyNumber}/9/9/${GUID}`| Updates policy contract status|| Added|| LifePRO | v.20.SP4|
|`/v1/PolicyCustomParameter/UpdatePRMPDetails`| Updates existing Policy parameter value|| Added|| LifePRO | v.20.SP4|
|`/v2/PolicyCustomParameter/DeletePRMPDetails/${GUID}/01/${this.PolicyNumber}/${this.ParmDefinitionID}`| Deletes a specified parameter|| Added|| LifePRO| v.20.SP4|
|`/v2/Quote/GetBenefitSurrenderQuote/${GUID}`| Retrieves a benefit surrender quote amount|| Added|| LifePRO| v.20.SP4|
|`/v2/Policy/GetPolicyRelations/${GUID}/01/${this.PolicyNumber}`| Retrieve spolicy relations by Policy Number|| Added||LifePRO|v.20.SP4|
|`/v2/Quote/InitiateDeathClaim/${GUID}`| Initiates a death claim for a policy|| Added|| LifePRO| v.20.SP4|
|`/v2/Note/InsertPolicyNotesDetails`| Inserts a policy note into an insurance record|| Added|| LifePRO| v.20.SP4|
|`/v3/Quote/ProcessSurrenderValues/${GUID}`| Processes the surrender of a policy|| Added|| LifePRO| v.20.SP4|
|`/v3/Quote/DeathBenefitQuote/${GUID}`| Retrieves a death benefit quote|| Added|| LifePRO| v.20.SP4|
|`/v3/Quote/SurrenderQuote/${GUID}`| Retrieves a surrender quote|| Added|| LifePRO| v.20.SP4|
|`/v3/Policy/ProcessPayments/${GUID}`| processes premium or loan payments|| Added|| LifePRO| v.20.SP4|
|`/v3/Policy/UpdatePolicy/${GUID}`| updates the policy contract record segment fields|| Added|| LifePRO | v.20.SP4|
|`/v4/Policy/GetPolicy/${GUID}/01/${this.PolicyNumber}`| Gets policy details|| Added|| LifePRO | v.20.SP4|




### VISON API - 
`Presently not used nor integrated`

### Insurance Services API 
| Endpoint                | Use Case                          | Application Leveraged In | Change Type | Description                                                                 | Owner | Version|
|-------------------------|-----------------------------------|--------------------------|-------------|-----------------------------------------------------------------------------|-------|-------|
|`/api/account/token?api=version=1.0`| Retrieves a Token| Lipas-Client| | Added| EIN | v.1.0.0|
|`api/document`| Retrieves document data| Lipas-Client|| Added| EIN| v.1.0.0






---

## 🔄 Version History

| Version | Date       | Description                |
| ------- | ---------- | -------------------------- |
| 1.0.0   | 2024-08-01 | Initial release             |

---

---

> **[⬅️ Back to LIPAS-Client Release Notes](../LIPAS-Client-1.0.0/1.1.0.md)**