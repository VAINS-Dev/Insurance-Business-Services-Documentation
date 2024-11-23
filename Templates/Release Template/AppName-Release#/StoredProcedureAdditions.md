
---

## Template 4: Stored Procedure Additions (New SP's Added)

```markdown
# Stored Procedure Additions 🧩

> **Release Version:** `vX.X.X`  
> **Release Date:** `YYYY-MM-DD`

---

## 📄 Overview

Introduce new stored procedures created in this release.

---

## 🆕 New Stored Procedures

### **1. Procedure Name: `usp_NewProcedure`**

- **Purpose**: Describe the functionality of the stored procedure.

- **Parameters**:

  | Parameter      | Data Type    | Direction | Description             |
  | -------------- | ------------ | --------- | ----------------------- |
  | `@param1`      | INT          | Input     | The ID of the record    |
  | `@param2`      | VARCHAR(50)  | Input     | Name filter             |
  | `@resultCount` | INT          | Output    | Number of records found |

- **Returns**: Result set containing filtered records.

- **Example Call**:

  ```sql
  DECLARE @resultCount INT;
  EXEC usp_NewProcedure @param1 = 100, @param2 = 'Sample', @resultCount = @resultCount OUTPUT;
  SELECT @resultCount AS 'Result Count';
```
  **[⬅️ Back to {Project Name} Release Notes](../AppName-Release#/release#.md)**