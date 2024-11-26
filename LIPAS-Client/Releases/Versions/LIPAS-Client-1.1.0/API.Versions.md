# API Versioning Release Document 📄

> **Application:** `LIPAS-Client`
> **Release Version:** `v1.1.0`  
> **Release Date:** `2024-11-26`
> **Release Type:** `latest-release`

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
| `/v1/Claim/${GUID}/UpdateDeathClaimHeader` | Update claim header             | N/A                    | Maintained      |   | LifePRO       | v.20.SP4         |
| `/v2/Claim/${GUID}/01/${this.PolicyNumber}/GetClaimList`  | Get Pending Claim List    | N/A                    | Maintained    |                       | LifePRO      | v.20.SP4          |

### Party API - LPRestParty
| Endpoint                | Use Case                          | Application Leveraged In | Change Type | Description                                                                 | Owner | Version|
|-------------------------|-----------------------------------|--------------------------|-------------|-----------------------------------------------------------------------------|-------|-------|
|`/v1/Address/AddAddress` | Add Address to NameRecord | | Maintained| | LifePRO | v.20.SP4|
|`/v1/Address/GetAddress` | Get Address  | | Maintained | | LifePRO | v.20.SP4|
|`/v1/Address/GetAddressByNameID`| Gets Address by NameID | | Maintained | | LifePRO | v.20.SP4|
| `/v1/Address/${this.PartyID_NameID}/${GUID}/GetPrimaryAddress`| Gets Primary Address by NameID| | Maintained| | LifePRO | v.20.SP4|
| `/v1/EFT/GetEFT`| Gets EFT by NameID | | Maintained| |LifePRO | v.20.SP4 |
| `/v1/EFT/InsertEFT` | Inserts EFT by NameID || Maintained || LifePRO | v.20.SP4|
| `/v1/EFT/UpdateEFT` | Updates EFT by NameID || Maintained || LifePRO | v.20.SP4|
| `/v1/EFT/DeleteEFT`| Deletes EFT by NameID || Maintained || LifePRO | v.20.SP4 |
| `/v1/PartyCustomParameter/${GUID}/${this.NameID}/getCustomParameter` | Retrieves party custom parameters by NameID| | Maintained|| LifePRO| v.20.SP4|
|`/v1/PartyCustomParameter/${GUID}/${this.NameID}/${this.ParamDefinitionID}/getCustomParameter`| Retrieves party custom parameters by definition ID| | Maintained|| LifePRO | v.20.SP4|
|`/v3/Party/${GUID}/PartySearch`| Executes a party search by NameID, SSN or Name||Maintained| | LifePRO | v.20.SP4|
|`/v4/Party/${GUID}/${this.NameID}/GetPartyRelationships`| Gets Relationships associated with a NameID| | Maintained| |LifePRO | v.20.SP4|

### Policy API - LPRestPolicy
| Endpoint                | Use Case                          | Application Leveraged In | Change Type | Description                                                                 | Owner | Version|
|-------------------------|-----------------------------------|--------------------------|-------------|-----------------------------------------------------------------------------|-------|-------|
|`/v1/Report/AccountingReportByAccount/${GUID}` | Retrieves accounting history data | | Maintained || LifePRO | v.20.SP4|
|`/v1/Policy/ChangePremiumDetails`| Changes premium details mode/method/option|| Maintained| | LifePRO | v.20.SP4|
|`/v1/Quote/DividendOptionChange` | Changes a policy dividend option || Maintained || LifePRO | v.20.SP4|
|`/v1/Loan/GetAllLoanList/${GUID}/01/${this.PolicyNumber}` | Retrieves loan history data || Maintained || LifePRO | v.20.SP4|
|`/v1/Policy/GetBenefitDetails`| Gets policy Benefit Data|| Maintained|| LifePRO | v.20.SP4|
|`/v1/PolicyCustomParameter/GetPolicyParameters`| Gets policy parameters|| Maintained|| LifePRO| v.20.SP4|
|`/v1/PolicyCustomParameter/InsertPRMPDetails`| Inserts a new policy custom parameter|| Maintained|| LifePRO|v.20.SP4|
|`/v1/Premium/ProcessManualAccounting/${GUID}` | Processes policy manual accounting || Maintained|| LifePRO |v.20.SP4|
|`/v1/Policy/ProcessReverseAndRecompute/${GUID}`| Processes reversal of anniversary|| Maintained|| LifePRO | v.20.SP4|
|`/v1/Policy/ProcessSuspenseRefund/${GUID}`| Process suspense refund|| Maintained|| LifePRO| v.20.SP4|
| `/v1/Policy/UpdatePolicyStatus/01/${this.PolicyNumber}/9/9/${GUID}`| Updates policy contract status|| Maintained|| LifePRO | v.20.SP4|
|`/v1/PolicyCustomParameter/UpdatePRMPDetails`| Updates existing Policy parameter value|| Maintained|| LifePRO | v.20.SP4|
|`/v2/PolicyCustomParameter/DeletePRMPDetails/${GUID}/01/${this.PolicyNumber}/${this.ParmDefinitionID}`| Deletes a specified parameter|| Maintained|| LifePRO| v.20.SP4|
|`/v2/Quote/GetBenefitSurrenderQuote/${GUID}`| Retrieves a benefit surrender quote amount|| Maintained|| LifePRO| v.20.SP4|
|`/v2/Policy/GetPolicyRelations/${GUID}/01/${this.PolicyNumber}`| Retrieve spolicy relations by Policy Number|| Maintained||LifePRO|v.20.SP4|
|`/v2/Quote/InitiateDeathClaim/${GUID}`| Initiates a death claim for a policy|| Maintained|| LifePRO| v.20.SP4|
|`/v2/Note/InsertPolicyNotesDetails`| Inserts a policy note into an insurance record|| Maintained|| LifePRO| v.20.SP4|
|`/v3/Quote/ProcessSurrenderValues/${GUID}`| Processes the surrender of a policy|| Maintained|| LifePRO| v.20.SP4|
|`/v3/Quote/DeathBenefitQuote/${GUID}`| Retrieves a death benefit quote|| Maintained|| LifePRO| v.20.SP4|
|`/v3/Quote/SurrenderQuote/${GUID}`| Retrieves a surrender quote|| Maintained|| LifePRO| v.20.SP4|
|`/v3/Policy/ProcessPayments/${GUID}`| processes premium or loan payments|| Maintained|| LifePRO| v.20.SP4|
|`/v3/Policy/UpdatePolicy/${GUID}`| updates the policy contract record segment fields|| Maintained|| LifePRO | v.20.SP4|
|`/v4/Policy/GetPolicy/${GUID}/01/${this.PolicyNumber}`| Gets policy details|| Maintained|| LifePRO | v.20.SP4|




### VISON API - 
`Presently not used nor integrated`

### Insurance Services API 
| Endpoint                | Use Case                          | Application Leveraged In | Change Type | Description                                                                 | Owner | Version|
|-------------------------|-----------------------------------|--------------------------|-------------|-----------------------------------------------------------------------------|-------|-------|
|`/api/account/token?api=version=1.0`| Retrieves a Token| Lipas-Client| | Maintained| EIN | v.1.0.0|
|`api/document`| Retrieves document data| Lipas-Client|| Maintained| EIN| v.1.0.0






---

## 🔄 Version History

| Version | Date       | Description                |
| ------- | ---------- | -------------------------- |
| 1.0.0   | 2024-08-01 | `preview`                  |
| 1.1.0   | 2024-11-26 | `latest-build`             |

---

> **[⬅️ Back to LIPAS-Client Release Notes](../LIPAS-Client-1.1.0/1.1.0.md)**