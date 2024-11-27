# Installation Guide 📦

> **ARCHER Version:** `v2.1.1`

> **LIPAS-Client Version:** `v.1.1.0`

> **VBA-INSURANCE-CORE Version:** `v.1.0.4` 

> **Last Updated:** `2024-11-27`

---

## 📄 Overview

* This document provides step-by-step instructions for installing the application, including prerequisites, installation steps, and post-installation configuration.

---

## 🛠 Prerequisites

* VAC10DBSLPS400 Web Server Access
* Node.js v.20 or above
* SQL Server User Name / Password

---

## 📥 Installation Steps (General)
### Insurance Business Services Installation Loader

1. **Download the Installer**
    - Locate installer at the following file path on the VA Network
    - `vbainslas1.vba.va.gov/LifePro/1_TEAM/dschnabel/InsuranceBusinessService.bat`

2. **Create Root Folder**
    - Create `Insurance-Business-Services` root folder

3. **Open and Install .bat file**
    - Move `InsuranceBusinessService.bat` file to newly created root folder

4. **Run the Installer**
    - Execute the `.bat` file
    - > Note: If a new version of the installer is available, the new version will automatically be fetched and the .bat will install and restart on the new version.
    - > Note: When the application has loaded, a configuration file will be created within `Insurance-Business-Services/Configuration/databaseConfig.json`.
        - > `Configuration file exists. Would you like to view the configuration? (y/n)` 
        - > This is optional if the technician wishes to view the current configuration. Edits need to occur within the file at `Insurance-Business-Services/Configuration/databaseConfig.json`.

5. **Obtain Auth Token**
    - Prompt: `Please enter your GitHub Personal Access Token (PAT)`
    - Will be provided during dual technician install `(Provided by VA)`

6. **Enter Auth Token**
    - When prompted, paste PAT authorization token to authenticate a session.

7. **Verfication and Initial Setup**
    - Once authenticated, the `.bat` solution will automatically pull the latest version of the `Insurance-Business-Services-Documentation` respository from Github. This documentation is built in markdown, however it is a public repository and accessible for viewing within the browser.
    - Available at `https://github.com/VAINS-Dev/Insurance-Business-Services-Documentation`

8. **Trigger ARCHER Install**
    - Prompt: `Would you like to download ARCHER repository? (y/n)` = `y`
    - Prompt: `Which branch of ARCHER would you like to download (Default: development)` = `preproduction`
    - > Note: If folder already exists with contents, the contents of the folder will be backed up to `Insurance-Business-Services/Repo-Backup/*`
    - Process will commense to pull the build down
    - Prompt: `Would you like to update dependencies for ARCHER (y/n)` = `y`
    - Solution dependencies will be pulled down to `Insurance-Business-Services/A.R.C.H.E.R` folder

9. **Trigger LIPAS-Client Install**
    - Prompt: `Would you like to download LIPAS-Client repository? (y/n)` = `y`
    - Prompt: `Which branch of LIPAS-Client would you like to download (Default: development)` = `preproduction`
    - > Note: If folder already exists with contents, the contents of the folder will be backed up to `Insurance-Business-Services/Repo-Backup/*`
    - Process will commense to pull the build down
    - Prompt: `Would you like to update dependencies for LIPAS-Client (y/n)` = `y`
    - Solution dependencies will be pulled down to `Insurance-Business-Services/LIPAS-Client` folder

10. **Trigger VBA-Insurance-Core Install**
    - Prompt: `Would you like to download VBA-Insurance-Core repository? (y/n)` = `y`
    - Prompt: `Which branch of VBA-Insurance-Core would you like to download (Default: development)` = `preproduction`
    - > Note: If folder already exists with contents, the contents of the folder will be backed up to `Insurance-Business-Services/Repo-Backup/*`
    - Process will commense to pull the build down
    - Prompt: `Would you like to update dependencies for VBA-Insurance-Core (y/n)` = `y`
    - Solution dependencies will be pulled down to `Insurance-Business-Services/VBA-Insurance-Core` folder

11. **Trigger Insurance-Business-Services-Database Install**
    - Prompt: `Would you like to download Insurance-Business-Services-Database repository? (y/n)` = `y`
    - Prompt: `Which branch of Insurance-Business-Services-Database would you like to download (Default: development)` = `preproduction`
    - > Note: If folder already exists with contents, the contents of the folder will be backed up to `Insurance-Business-Services/Repo-Backup/*`
    - Process will commense to pull the build down
    - Prompt: `Would you like to update dependencies for VBA-Insurance-Core (y/n)` = **`n`** (NO)
    - > Do not download dependencies
---

## 📥 Installation Steps (General)
1. **Open `Configuration` folder at `Insurance-Business-Services/Configuration`**
    - Complete the `databaseConfig.json` file with credentials for VAC10DBSLPS400.v
        ```json
            {
            "DatabaseConfiguration": {
                "DB_HOST": "host_value", //*Required*
                "DB_USERNAME": "username_value", //*Required*
                "DB_PASSWORD": "password_value", //*Required*
                "DB_DATABASE": "database_value", //*Required*
                "DB_INTEGRATED_SECURITY": true, //No Change
                "DB_TRUSTCONNECTION": true, //No Change
                "DB_TRUST_SERVER_CERTIFICATE": true, //No Change
                "DB_ENCRYPT": true, //No Change
                "DB_CONNECTION_TIMEOUT": 30000, //No Change
                "DB_DRIVER": "msnodesqlv8" //No Change
            }
        }
        ```

2. **Create Schema and Assign Owner**
    - This application suite uses a new database schema `[InsuranceBusinessServices]`
    - The schema must be created and given a database owner
    - The Archer ppd and prod service account must also be added as an owner
    ```sql

    BEGIN TRANSACTION;
    --Creates Schema
    CREATE SCHEMA InsuranceBusinessService;
    COMMIT TRANSACTION;


    BEGIN TRANSACTION;
    --Grants access to archer application user name
    GRANT ALTER, SELECT, INSERT, UPDATE, DELETE ON SCHEMA::InsuranceBusinessService TO [Archer];
    --Grants access to Drew-Schnabel (VA)
    GRANT ALTER, SELECT, INSERT, UPDATE, DELETE ON SCHEMA::InsuranceBusinessService TO [VBA\PSDDSCHA];
    COMMIT TRANSACTION;
    ```

## 📥 Installation Steps (LIPAS-Client)

1. **Install SQL Stored Procedures and Table Changes**
    - For LIPAS-Client [`v.1.1.0`](../../LIPAS-Client/Releases/Versions/LIPAS-Client-1.1.0/1.1.0.md) 


## 📥 Installation Steps (VBA-INSURANCE-CORE)
  
1. **Install SQL Stored Procedures and Table Changes**
    - For VBA-INSURANCE-CORE [`v.1.0.4`](../../VBA-INSURANCE-CORE/Releases/Versions/VBA-INSURANCE-CORE%20-%201.0.4/1.0.4.md)


## 📥 Installation Steps (ARCHER)
  
1. **Install SQL Stored Procedures and Table Changes**
    - For VBA-INSURANCE-CORE [`v.2.1.1`](../../ARCHER/Releases/Versions/ARCHER-2.1.1/2.1.1.md)





## 🔧 Post-Installation Configuration
1. **Run Initial LIPAS-Client Build**
    - Run the initial build process
    - Within `LIPAS-Client/Executables/`
    - Execute `Run-Initial-Setup.bat`

2. **Validate Policy Parameter Definition ID's**
    - Within `LIFEPRO_CONV1.dbo.PPRMD_CUSTOM_PARAMETER_DEFINITIONS` verify each parameter ID below and ensure `[InsuranceBusinessService].[Configuration]` is updated accordingly.
    -- Note: Execute the following to obtain required CPARMS;
    ---
     ```sql
        SELECT PARAMETER_NAME, PARM_DEFINITION_ID AS LIFEPRO_ID, ConfigKey, ConfigValue as CONFIG_ID FROM LifePRO_CONV1.DBO.PPRMD_CUSTOM_PARAMETER_DEFINITIONS
        FULL JOIN insentry.InsuranceBusinessService.configuration c ON TRY_CAST(c.ConfigValue as INT) = PARM_DEFINITION_ID
        WHERE Parameter_name IN (
        'Email Communications'
        , 'Text Communications'
        , 'Email and Text Communications'
        , 'Cell Phone Number'
        , 'Loan Repayment Amount'
        , 'Overpayment Lien Amount'
        , 'Premium Lien Amount'
        , 'Administrative Lien Amount'
        , 'Veteran is Incompetent'
        , 'Email Communications'
        , 'Fraud'
        , 'Accounts Receivable'
        , 'Policy Alert: SDVI Cancellation Due for VALife'
        , 'ICN'
        )
    ```

3. **Correcting Discrepant Parameter Definition ID's**
    - Within `[Insentry].[InsuranceBusinessService].[Configuration]` the technician will need to manually update the corresponding database row `key/value` pair accordingly.
    - Execute the following SQL Update Script to manually update incorrect `key/value` pairs
    ---
    ```sql
    SELECT * FROM [Insentry].[InsuranceBusinessService].[Configuration]
    WHERE ConfigKey = ''
    --Gets Configuration by Config Key Name
    
    UPDATE [Insentry].[InsuranceBusinessService].[Configuration]
    SET ConfigValue = 'ENTER VALUE HERE', ModifiedDate = GETDATE() 
    WHERE ID = 'ENTER VALUE HERE'

    --Updates Configuration, requires ID number obtained using above select statement
    -- ConfigValue = LIFEPRO_ID from Step 1

    ```

4. **Run LIPAS-Client Configuration Reload** (If uUpdates were required)
    - Once all configuration updates have been made, run the force-config reload executable
    - Within `LIPAS-Client/Executables/`
    - Execute `Force-Config-Reload.bat`

5. **Verify Cancellation Reason Code** (Requires LifePRO Admin)
    - Open LifePRO `[Environment]`
    - Select System Configuration
    - Select Table Definition
    - Select Cancellation Reason Codes
    - Review for `SDVI SURRENDER - VALIFE - 38 USC 1922` 
    - Document numerical code ID

    - Within `[Insentry].[InsuranceBusinessService].[Configuration]` the technician will need to manually update the corresponding database row `key/value` pair accordingly.
    - Execute the following SQL Update Script to manually update incorrect `key/value` pairs
    ---
    ```sql
    SELECT * FROM [Insentry].[InsuranceBusinessService].[Configuration]
    WHERE ConfigKey = 'SDVI_CANCELLATION_REASON_CODE'
    --Gets Configuration by Config Key Name
    
    --If the keyID is different than the LifePRO configuration, the below update will be required


    UPDATE [Insentry].[InsuranceBusinessService].[Configuration]
    SET ConfigValue = 'ENTER VALUE HERE', ModifiedDate = GETDATE() 
    WHERE ConfigKey = 'SDVI_CANCELLATION_REASON_CODE'

    --Updates Configuration, requires ID number obtained using above select statement
    -- ConfigValue = LIFEPRO_ID from Step 1

    ```


5. **JAMS Configuration**
    - ARCHER
        - Setup JAMS Job to Target A.R.C.H.E.R folder
        - path: `Insurance-Business-Services/A.R.C.H.E.R/`
        - command: `npm run start`
    - VBA-INSURANCE-CORE
        - Setup JAMS Job to Target VBA-Insurance-Core folder
        - path: `Insurance-Business-Services/VBA-Insurance-Core/`
        - command: `npm run Cancel-SDVI-Controller`

---

## 📝 Troubleshooting

* Common issues and their solutions.
* Links to additional resources or support.

---

## 🔄 Change Log

| Version | Date       | Description                         |
|---------|------------|-------------------------------------|
| `1.0.4`   | 2024-11-27 | VBA Insurance Core Release - Build|
| `1.1.0`   | 2024-11-27 | LIPAS-Client Release - Build      |
| `2.1.1`   | 2024-09-30 | ARCHER Release - Build            |

---


> **[⬅️ Back to Insurance Business Services Installation guides](./../Install.md)**









































































