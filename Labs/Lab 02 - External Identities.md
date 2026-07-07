# **Lab 02: External Identities and Tenant Configuration in Microsoft Entra ID**

---

##  **Objective**

To explore and configure **External Identities**, **Cross-Tenant Access**, and **User Settings** within Microsoft Entra ID.  
This lab focuses on understanding how external collaboration, identity providers, and tenant properties are managed to ensure secure and controlled access across organizational boundaries.

---

##  **Tools & Services Used**

- Microsoft Entra Admin Center  
- Azure Portal  
- Microsoft Account (ziyan.shaikh100@outlook.com)

---

##  **Steps Performed**

---

### **Step 1 - Configured Tenant Properties**

I began by reviewing the **Default Directory** properties to understand tenant-level configurations such as region, language, and access management.  
Key details included tenant ID, technical contact, and privacy settings.

[![Tenant Properties](Screenshots/Default_Directory_Properties.png)](Screenshots/Default_Directory_Properties.png)

---

### **Step 2 - Reviewed User Settings**

Next, I explored **User Settings** to define permissions and access levels for internal and external users.  
I ensured that:
- Users can register applications and create security groups.  
- Guest users have limited access to directory objects.  
- LinkedIn account connections are enabled for professional integration.  
- “Keep user signed in” is turned on for better session continuity.

[![User Settings](Screenshots/User_Settings.png)](Screenshots/User_Settings.png)

---

### **Step 3 - Configured External Collaboration Settings**

I then configured **External Collaboration Settings** to manage how guest users interact with the tenant.  
Key configurations included:
- Restricting guest user access to limited directory properties.  
- Allowing only specific admin roles to invite guest users.  
- Enabling external users to remove themselves from the organization.  
- Setting collaboration restrictions to control domain invitations.

[![External Collaboration Settings](Screenshots/External_Collaboration_Settings.png)](Screenshots/External_Collaboration_Settings.png)

---

### **Step 4 - Managed Identity Providers**

Under **All Identity Providers**, I verified which authentication methods were configured for external access.  
The following providers were active:
- Microsoft Entra ID  
- Email One-Time Passcode  
- Microsoft Account  

Additionally, Google and Facebook were available for configuration, offering flexibility for external identity management.

[![Identity Providers](Screenshots/All_Identity_Providers.png)](Screenshots/All_Identity_Providers.png)

---

### **Step 5 - Configured Cross-Tenant Access Settings**

Finally, I reviewed **Cross-Tenant Access Settings** to manage inbound and outbound collaboration between tenants.  
I confirmed that:
- B2B collaboration for users and applications is allowed.  
- B2B direct connect is blocked for both users and applications.  
- Tenant restrictions are applied to block external users and applications by default.

[![Cross-Tenant Access Settings](Screenshots/Cross_Tenant_Access_Settings.png)](Screenshots/Cross_Tenant_Access_Settings.png)

---

##  **Key Learnings**

- Microsoft Entra ID provides granular control over external collaboration and identity management.  
- Proper configuration of guest access and cross-tenant settings strengthens organizational security.  
- Identity providers like Microsoft and Google enhance flexibility for external authentication.  
- Tenant-level settings ensure compliance and centralized management.

---

##  **Lab Outcome**

Successfully configured and documented **External Identities**, **Cross-Tenant Access**, and **User Settings** in Microsoft Entra ID.  
This lab deepened my understanding of how organizations manage external collaboration securely while maintaining administrative control.

---

##  **Screenshots Summary**

| Step | Description | Screenshot |
|------|--------------|-------------|
| 1 | Tenant Properties | [View](Screenshots/Default_Directory_Properties.png) |
| 2 | User Settings | [View](Screenshots/User_Settings.png) |
| 3 | External Collaboration Settings | [View](Screenshots/External_Collaboration_Settings.png) |
| 4 | Identity Providers | [View](Screenshots/All_Identity_Providers.png) |
| 5 | Cross-Tenant Access Settings | [View](Screenshots/Cross_Tenant_Access_Settings.png) |

---

