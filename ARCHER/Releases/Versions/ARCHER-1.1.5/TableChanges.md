**[Back to 1.1.5 Release](./1.1.5.md)**
# Release Notes: V.1.1.5 - Stable Release - 2024-03-11

## Table Changes:

As part of the ongoing improvements to the ARCHER application within the Insurance Business Services suite, we’ve implemented important database changes to enhance functionality and support new features.

Addition of [AccountingControlNumber] Column to dbo.Archer Table

Overview

We have added a new column called [AccountingControlNumber] to the dbo.Archer table in the database. This column is designed to store unique accounting control numbers associated with each transaction or record, enabling better tracking and integration with accounting systems.

Details

	•	Table Affected: dbo.Archer
	•	New Column: [AccountingControlNumber]
	•	Data Type: VARCHAR(50) (adjust the data type as per actual implementation)
	•	Nullability: Should be specified (NULL or NOT NULL depending on requirements)
	•	Default Value: If applicable, mention any default values or constraints

Purpose and Benefits

	•	Enhanced Tracking: Allows for precise tracking of transactions within the ARCHER system and alignment with accounting records.
	•	Integration: Facilitates seamless integration with external accounting systems by providing a common reference number.
	•	Auditability: Improves audit trails by linking ARCHER records directly to accounting entries.
	•	Error Reduction: Minimizes discrepancies between systems by ensuring consistent control numbers.

Impact on Existing Data

	•	Data Migration: Existing records may require backfilling the [AccountingControlNumber] with appropriate values or placeholders.
	•	Applications and Services: Any application logic, services, or stored procedures interacting with dbo.Archer may need updates to handle the new column.
	•	Testing: Extensive testing is necessary to ensure that the addition does not adversely affect existing functionalities.

Inclusion of [AccountingControlNumber] in ARCHER Processing Views

Overview

The [AccountingControlNumber] column has also been added to the ARCHER processing views. This ensures that the new accounting control numbers are accessible wherever the views are utilized, such as in reporting, data processing, or integration tasks.

Views Affected

	•	vw_ArcherProcessing
	•	vw_ArcherTransactions
	•	vw_ArcherAudit
	•	(Include all relevant views that have been updated)

Details

	•	Column Addition: The [AccountingControlNumber] has been added to the SELECT statements within each view.
	•	Data Exposure: By including the column in the views, it becomes available for any queries or operations that utilize these views.
	•	Consistency: Ensures that all data retrieval mechanisms have consistent access to the accounting control numbers.

Purpose and Benefits

	•	Reporting: Enhances financial and operational reports by including the accounting control number.
	•	Data Analysis: Facilitates advanced data analysis and reconciliation tasks.
	•	System Integration: Supports integration with other systems that rely on the processing views for data exchange.

Impact on Dependent Systems

	•	Applications: Any applications or services consuming these views may need to be reviewed to accommodate the additional column.
	•	Performance: Evaluate if the inclusion of the new column impacts the performance of queries, especially in views that handle large datasets.
	•	Security: Ensure that access controls are in place so that sensitive accounting information is only available to authorized users.

Actions Required

For Developers

	•	Update Codebase: Modify any code interacting with dbo.Archer or the affected views to handle the [AccountingControlNumber] appropriately.
	•	Validate Data Handling: Ensure that data insertion, updates, and retrievals correctly process the new column.
	•	Testing: Perform unit and integration testing to verify that the changes do not introduce any regressions.

For Database Administrators

	•	Schema Deployment: Apply the schema changes to development, staging, and production environments following deployment protocols.
	•	Backup Data: Create backups before making changes to prevent data loss in case of unforeseen issues.
	•	Monitor Performance: After deployment, monitor database performance to detect any impacts due to the changes.

For QA/Testers

	•	Test Scenarios: Develop test cases covering all scenarios involving the new column.
	•	Regression Testing: Conduct thorough regression tests to ensure existing functionalities remain unaffected.
	•	Report Issues: Document and report any anomalies or bugs found during testing.

Additional Considerations

Data Integrity

	•	Constraints: Implement any necessary constraints or validations on the [AccountingControlNumber] to maintain data integrity.
	•	Uniqueness: If required, enforce uniqueness to prevent duplicate accounting control numbers.

Documentation

	•	Update Documentation: All technical and user documentation should reflect the changes, including data dictionaries, ER diagrams, and interface specifications.
	•	Communicate Changes: Inform all stakeholders about the changes, especially those who rely on the database structure for their operations.

Compliance and Security

	•	Compliance Requirements: Ensure that handling of the [AccountingControlNumber] complies with relevant financial regulations and organizational policies.
	•	Access Controls: Review and adjust user permissions as necessary to protect sensitive accounting information.

Conclusion

The addition of the [AccountingControlNumber] column to the dbo.Archer table and its inclusion in the processing views represent significant enhancements to the ARCHER application. These changes aim to improve financial tracking, integration capabilities, and overall data integrity within the Insurance Business Services suite.
