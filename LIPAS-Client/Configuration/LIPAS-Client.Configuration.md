# Configuration Document 📄


> **Last Updated:** `2024-11-25`

---

## 📄 Overview

* This document provides detailed information about the configuration settings, parameters, and environment variables used in the application for the LIPAS-Client and associated applications.

---


### > Configuration - [`[InsuranceBusinessService].[Configuration]`](Configuration.md)
> Used for primary configuration.


### > Feature Switch - [`[InsuranceBusinessService].[FeatureSwitch]`](FeatureSwitch.md)
> To enable and disable features.

### > Stored Procedure Configuration - [`[InsuranceBusinessService].[StoredProcedureConfiguration]`](StoredProcedureConfiguration.md)
> To store stored procedure path's and configurations.

### > Internal Control Configuration - [`[InsuranceBusinessService].[InternalControlConfiguration]`](../Configuration/InternalControlConfiguration.md)
> To store internal control feature functionality and parameters.

### > Letter Configuration - [`[InsuranceBusinessService].[LetterConfiguration]`](./LetterConfiguration.md)
> To store letter codes used in automatically released correspondence.

---

## ⚙️ Sample Configuration Settings

| Setting                 | Description                                  | Value Type |  Value Options                  | Notes                                      |
|-------------------------|----------------------------------------------|---------------|---------------------------------|--------------------------------------------|
| `app_mode`              | Sets the application mode                    | `production`  | `development`, `production`     | Adjusts logging levels accordingly.        |
| `database_url`          | URL of the database connection               | `localhost`   | Any valid database URL          | Ensure the database is accessible.         |
| `max_connections`       | Maximum number of database connections       | `50`          | Any integer                     | Depends on server capacity.                |
| `enable_feature_x`      | Toggles Feature X                            | `false`       | `true`, `false`                 | Requires additional dependencies if enabled.|

---

> **[⬅️ Back to LIPAS-Client Documentation](../LIPAS-Client.md)**