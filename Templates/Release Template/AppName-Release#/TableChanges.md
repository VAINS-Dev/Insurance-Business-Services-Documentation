# Database Table Changes 🔧

> **Release Version:** `vX.X.X`  
> **Release Date:** `YYYY-MM-DD`

---

## 📄 Overview

Detail the changes made to existing database tables.

---

## 📝 Modified Tables

### **1. Table Name: `existing_table`**

- **Changes**:

  - **Added Column**: `new_column` (VARCHAR(50), NOT NULL, Default: `'default_value'`)
  - **Modified Column**: `existing_column` changed data type from INT to BIGINT
  - **Dropped Column**: `obsolete_column`

- **Reason for Changes**:

  > _Quote_: "These changes are necessary to support the new reporting requirements."

- **Impact**:

  - Applications accessing `existing_table` must accommodate the new column.
  - Potential data type mismatch warnings.

---

### **2. Table Name: `another_existing_table`**

- **Changes**:

  - **Updated Constraints**: Changed `status` column to `NOT NULL`
  - **Index Added**: `idx_status` on `status` column

---

## 🔄 Migration Scripts

```sql
-- Add new_column
ALTER TABLE existing_table
ADD COLUMN new_column VARCHAR(50) NOT NULL DEFAULT 'default_value';

-- Modify existing_column
ALTER TABLE existing_table
MODIFY COLUMN existing_column BIGINT;

-- Drop obsolete_column
ALTER TABLE existing_table
DROP COLUMN obsolete_column;
```

> **[⬅️ Back to {Project Name} Release Notes](../AppName-Release#/release#.md)**