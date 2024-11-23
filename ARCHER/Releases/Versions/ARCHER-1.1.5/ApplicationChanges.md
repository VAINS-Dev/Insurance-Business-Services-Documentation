**[Back to 1.1.5](../../Versions/ARCHER-1.1.5/1.1.5.md)**


Application Changes

Removal of Configuration Utility

	•	Change: Migrated from the configuration utility to using a .env file for storing configuration data more securely.

Updates to .env Configuration File

	•	Addition: New service-specific Coder_IDs for:
	•	Loan
	•	Premium
	•	ME (Medical Examination)
	•	Service

Logic Changes for VILN-16457

	•	Change: Updated application logic to support the requirements of VILN-16457.

New Function: GetSuspensePaymentHistory

	•	Purpose: Retrieves the suspense history of a policy for a specified suspense amount.
	•	Functionality:
	•	Iterates to find payment dates and amounts matching the suspense amount.
	•	Returns an object or array of objects to the caller.

New Function: GetAccountingControlNumber

	•	Purpose: Retrieves the accounting control number for recent transactions based on type code and transaction.
	•	Supported Services:
	•	Loan
	•	Lien
	•	Premium

Updates to ARCHERLogger

	•	Change: Added [AccountingControlNumber] to logging details for enhanced tracking.

Updates to ValidateDatabase

	•	Change: Modified to support changes related to [AccountingControlNumber].

New Logic in getAccountingControlNumber.js

	•	Change: Implemented logic to obtain the accounting control number after confirming successful payment posting.
	•	Supported Services:
	•	Loans
	•	Premiums
	•	Liens

Short Summary

These changes enhance security, improve transaction tracking, and extend support for additional services within the application suite.

	•	Security Improvement: Transition to .env files for configuration.
	•	Enhanced Functionality:
	•	New functions for retrieving payment history and accounting control numbers.
	•	Logic updates to support specific service requirements.
	•	Extended Logging: Inclusion of accounting control numbers in logs for better traceability.