---

## Stored Procedure Changes (Existing SP's Changed)

```markdown
# Stored Procedure Changes 🛠️

> **Release Version:** `vX.X.X`  
> **Release Date:** `YYYY-MM-DD`

---

## 📄 Overview

* Describe the modifications made to existing stored procedures.

---

## 📝 Modified Stored Procedures

### **1. Procedure Name: `usp_ExistingProcedure`**

- **Changes**:

  - **Added Parameter**: `@newParam VARCHAR(20)`
  - **Modified Logic**: Implemented new filtering based on `@newParam`.
  - **Deprecated**: Parameter `@oldParam` is now deprecated and will be removed in future releases.

- **Impact**:

  - Applications must pass `@newParam` to utilize the updated procedure.
  - Warnings will be logged if `@oldParam` is used.

- **Migration Notes**:

  > **Note**: It's recommended to update all application code to replace `@oldParam` with `@newParam`.

---

## 🔄 Version History

| Version | Date       | Description                |
| ------- | ---------- | -------------------------- |
| 1.2.0   | YYYY-MM-DD | Added `@newParam`          |
| 1.1.0   | YYYY-MM-DD | Performance optimizations  |
| 1.0.0   | YYYY-MM-DD | Initial release            |

---

## 📋 Action Items

- [ ] Developers: Update stored procedure calls in the application.
- [ ] Testers: Verify the procedure works with the new parameter.
- [ ] Operations: Monitor logs for deprecated parameter usage.

---

> **[⬅️ Back to {Project Name} Release Notes](../AppName-Release#/release#.md)**