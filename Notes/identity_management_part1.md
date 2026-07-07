# **Implementing an Identity Management Solution**
### *Part 1 — Identity Management, Device Joining, Licensing & Custom Security Attributes*

---

## **Lab Overview**

Watched a lab covering user and group management in Microsoft Entra ID. Performed the following actions hands-on:

- Adding users
- Deleting users
- Adding groups

> **Critical Note:**
> When creating a group, the option **"Microsoft Entra roles can be assigned to this group"** cannot be edited after creation.
> To change it, the group must be **deleted and recreated**.

---

# **Dynamic Groups**

---

## **Rule Syntax**

Dynamic groups use attribute-based rules to automatically assign membership. Rules follow this pattern:

> `attribute — operator — value`

---

### **Example Rules**

`user.jobTitle - startsWith "xyz"`
Match users whose job title begins with a specific string.

`user.department - eq "Developer"`
Match users whose department exactly equals "Developer".

`user.companyName - ne "companyname"`
Match users whose company name does not equal a specific value.

---

### **Operators**

**startsWith** — The attribute value begins with the specified string.

**eq** — The attribute value exactly equals the specified value.

**ne** — The attribute value does not equal the specified value.

---

### **Connectors**

**AND** — All rules in the set must be true for a match.

**OR** — At least one rule in the set must be true for a match.

---

## **Group Ownership & Nesting Behaviour**

**Group Owner scope**
An owner can only manage users within their specific group. They do not automatically gain admin rights outside it.

**Manual membership (Assigned groups)**
Members can be manually added or removed at any time.

**Dynamic group membership**
Dynamic groups cannot have manually added members — membership is ruled entirely by the defined query.

---

## **Nesting Rules**

**Dynamic groups can be nested *under* other groups.**
A Security Group can contain a Dynamic Group as a member.

**No group can be nested *under* a Dynamic Group.**
A Dynamic Group cannot contain another group as a member.

```
Security Group
     ↓
[Dynamic] SG2      ✖  SG3 cannot nest under a Dynamic Group
```

---

# **Role Assignments & Group Nesting**

---

**Assigned groups with role assignments do not allow nesting inside them.**

If a group has a role assignment, other groups cannot be placed inside it as members.

### **Example**

SG2 has a **User Administrator** role assignment. Anyone added to SG2 automatically inherits the User Administrator role.

```
Assigned SG1 ← Role Assignment → Assigned SG2 ← Assigned SG3
```

**Dynamic groups** can be nested under assigned groups, but cannot have any groups nested under themselves.

---

# **Device Management in Microsoft Entra ID**

---

## **Entra ID Registered Devices — BYOD**

Microsoft Entra ID supports **Bring Your Own Device (BYOD)**.

Users connect to the company's Entra tenant using MDM tools such as **Microsoft Intune**. Users can access company resources while keeping personal files and applications private.

**Supported operating systems:**
- Windows 10 / 11
- iOS
- Android
- macOS

---

## **Microsoft Entra Hybrid Joined Devices**

Policies can be pushed using **MEMMS** and **Conditional Access**.

**Supported operating systems:**
- Windows 10
- Windows 11

> Home editions of Windows are **not supported** for Hybrid Join.

### **Hybrid Join Architecture**

```
Company-owned laptop → Entra ID (Cloud)
                              ↓
          Active Directory Domain Services (On-premises)
```

---

## **Cloud vs Hybrid Device Management**

Entra ID joined devices are intended for **cloud-first or cloud-only** organisations.

A device can be in one of two states:

**Entra ID Joined** — Cloud only. No on-premises dependency.

**Hybrid Joined** — Connected to both cloud (Entra ID) and on-premises (Active Directory).

---

### **Why Use Hybrid Join?**

**Legacy Win32 applications** cannot be migrated to the cloud and require on-premises infrastructure.

**Entra ID does not support Group Policy Objects (GPOs).** On-premises admins must retain GPO management for those workloads.

**Hybrid join is also useful** when admins need to manage different OS images on-premises, particularly across the range of Windows 8.1 through Windows 11.

---

# **Group Policy Objects (GPOs)**

---

## **What Are GPOs?**

Centralised collections of configuration and security settings managed within **on-premises Active Directory**.

---

## **Why GPOs Do Not Work in Entra ID**

GPOs have hard infrastructure dependencies that do not exist in the cloud.

**GPOs require:**
- Domain Controllers
- LDAP
- SYSVOL

**Microsoft Entra ID is cloud-native, built on:**
- REST APIs
- Web protocols

These are fundamentally incompatible. GPOs cannot exist in Entra ID.

---

# **Licensing — Azure & Entra**

---

## **Licence Tiers**

Azure is free at its base level. Advanced IAM features require one of the following:

**P1 licence** — Core premium identity features.

**P2 licence** — Includes everything in P1, plus advanced protection and governance.

**Identity Governance (Entra Suite)** — Includes:
- Privileged Identity Management (PIM)
- Entitlement Management
- Governance features

> **Note:** Licence management has moved. It now takes place in the **M365 Admin Center**, not in Entra.

---

## **Applying Licences**

Licences can be assigned to **individual users** or to **groups**.

An email notification is sent automatically or can be triggered manually.

**Group licensing requirement:** There must be enough available licences to cover all members of the group. Assignment will fail if the licence count is insufficient.

---

# **Custom Security Attributes (CSA)**

---

## **Overview**

Custom Security Attributes are available under **P1 / P2 licences**.

Before using CSAs, a **Global Administrator** must assign themselves one of the following roles:

- **Attribute Assignment Administrator** — Can assign attribute values to users and apps.
- **Attribute Definition Administrator** — Can create and manage attribute sets and definitions.
- **Attribute Assignment Reader** — Can view attribute values without modifying them.

---

## **Lab Example**

**Attribute set created:** CC (Security Clearance Level)

**Description:** Access control for the HR team.

**Defined values:**
- Level 1 — Low
- Level 2 — Medium
- Level 3 — High

---

## **Key Concepts**

Custom Security Attributes are **key-value pairs** that can be assigned to:

- Users
- Enterprise Applications / Service Principals

---

### **What CSAs Enable**

**Fine-grained access control**
Apply precise permission logic beyond standard role assignments.

**Object categorisation**
Tag and organise users or applications by custom criteria.

**Secure storage of sensitive profile data**
Store HR or compliance data with restricted visibility.

---

### **Use Cases**

**Advanced Access Control**
Tag applications or service principals for Conditional Access filtering based on custom attributes.

**HR Data Integration**
Store employee metadata such as clearance level, project team, or employment type.

**Data Privacy**
Restrict attribute visibility to authorised administrators only — other admins cannot read the values.

---

# **Exam Notes — Critical**

---

**Global Administrator cannot read, define, or assign Custom Security Attributes.**
The GA role must explicitly grant itself the required attribute role first.

**CSAs can only be assigned to users and enterprise apps / service principals.**
They cannot be assigned to groups or devices.

**Scope delegation must be attribute-set specific.**
It cannot be granted at the tenant-wide level.

**CSAs and attribute sets cannot be deleted — only deactivated.**

**CSAs and attribute sets cannot be renamed.**
Only descriptions can be changed after creation.

**CSAs cannot be used in dynamic group rules.**

**CSAs can be used in Conditional Access (ABAC — Attribute-Based Access Control).**

---

## **Conditional Access Example — ABAC**

**Policy: Block access to any enterprise application where:**

```
CustomSecurityAttribute.Sensitivity = High
AND the user is outside the corporate network
```

This demonstrates using a CSA value as a Conditional Access filter, combining attribute-based and network-based conditions.

---

*End of document.*
