## Script: List Server Role Memberships and Generate Grant Statements

**Description**:
This script lists all logins that are members of fixed or custom **server-level roles** in SQL Server. It includes the login types, role types, and generates dynamic T-SQL `ALTER SERVER ROLE ... ADD MEMBER` statements for recreating role memberships.

**What It Shows**:
- Server role name and type (fixed or custom)
- Login name, type, and membership
- Auto-generated script to add each login to their respective role

**Use Case**:
- Audit server-level role assignments
- Script out and reapply role memberships (e.g., during migrations)
- Identify critical roles like `sysadmin`, `securityadmin`, etc.

**Requirements**:
- SQL Server 2012 or later (uses `ALTER SERVER ROLE`)
- `VIEW SERVER STATE` permission (or `sysadmin`)

**Notes**:
- This does **not** include database-level roles — only server-level.
- You can use the `AddRoleMembersStatement` output to regenerate all memberships in another environment.
- Consider exporting and versioning this as part of your security audit process.
