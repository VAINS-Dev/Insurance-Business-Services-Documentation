# API Versioning Release Document 📄

> **Release Version:** `vX.X.X`  
> **Release Date:** `YYYY-MM-DD`

---

## 📄 Overview

* This document outlines the changes made to the API endpoints, including additions, modifications, and deletions.

---

## 📝 API Changes

| Endpoint                | Use Case                          | Application Leveraged In | Change Type | Description                                                                 |
|-------------------------|-----------------------------------|--------------------------|-------------|-----------------------------------------------------------------------------|
| `/api/v1/resource`      | Retrieve resource data            | App A                    | Addition    | Added a new endpoint to retrieve resource data.                             |
| `/api/v1/resource/{id}` | Update resource data              | App B                    | Change      | Modified the endpoint to include validation for the `id` parameter.         |
| `/api/v1/old-resource`  | Deprecated resource retrieval     | App C                    | Deletion    | Removed the old endpoint as it is no longer supported.                      |

---

## 🔄 Version History

| Version | Date       | Description                |
| ------- | ---------- | -------------------------- |
| 1.0.1   | YYYY-MM-DD | Added new endpoint          |
| 1.0.0   | YYYY-MM-DD | Initial release             |

---

## 📋 Action Items

- [ ] Developers: Update API calls in the application to use the new endpoints.
- [ ] Testers: Verify the new and modified endpoints work as expected.
- [ ] Operations: Monitor for any issues related to the deprecated endpoints.

---

> **[⬅️ Back to {Project Name} Release Notes](../AppName-Release#/release#.md)**