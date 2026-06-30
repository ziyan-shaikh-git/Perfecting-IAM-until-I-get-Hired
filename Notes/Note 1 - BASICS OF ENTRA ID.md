# Note 1 - BASICS OF ENTRA ID





### 1\. UPN (User Principal Name)



It should be unique.



Note: While configuring the Create User Properties, you’ll need to provide the first name, last name, user type, and authentication info.



These are the first four fields when connecting your Entra ID with Third-party Signature Applications / Dynamic Groups.



Managed Users: Created, Named, Deleted, and Restored Users.



Groups: Microsoft Entra ID allows you to create two different types of groups.



### 2\. Types of Groups



##### Security Groups



Most common type of group.



Used to manage member and computer access to shared resources for a group of users.



Example: Managing access for VMs on the cloud.



##### Microsoft 365 Groups



Provide collaboration opportunities by giving members access to a shared mailbox, calendar, files, and SharePoint site.



##### Membership Types

###### 

###### **Assigned**:  Members are added and maintained manually.



### 3\. Dynamic Groups



Members are added based on rules, creating a dynamic group.



These groups are still either a Security Group or Microsoft 365 Group — only their members are controlled by rules.



Note: Once created, you cannot change the group type.



Note: The deleted group (30-day policy) does not apply to both types — security groups are deleted directly.



### 4\. Groups on Azure Entra ID



Help organize users, making it easier to:



Manage permissions on users.



Manage licenses on users.



You can assign specific security permissions or licenses to groups and add users accordingly.



Practical: Created two groups — one Security Group and one M365 Group. Tested deletion and restoration.



### 5\. Dynamic Groups in Detail



Automatically assign memberships based on user or device attributes.



Ensures resources are accessible to the right people.



Members can be added or removed based on attributes (e.g., location, salary).



Can provide access to applications or cloud resources (SharePoint, documents, etc.) and assign licenses to members.



Requires P1 or P2 license.



### 6\. Dynamic User, Device \& Query



Users are added or deleted using an API query (rule you define).



Dynamic User: Added/removed based on user properties.



Dynamic Device: Added/removed automatically based on device properties.



Once selected, you’ll define a Dynamic Query — a rule that becomes a parameter for user inclusion/exclusion.



### 7\. Rule Definition



Define rules using AND / OR:



AND: All defined properties must match for a user to be added.



OR: If one property matches, the user is added or removed.



Define the operator (e.g., contains) and value (e.g., containing what?).



### 8\. Configure \& Manage External Identities



Inviting external users to Azure resources is beneficial but must be secure.



Microsoft Entra B2B Collaboration:



Part of External Identities in Entra.



Allows inviting guest users to collaborate securely.



Share applications and services with external users while maintaining control over corporate data.



### 9\. Example of B2B Collaboration



Scenario: Company A invites an external auditor from Company B.



Option 1: Create a new user in Company A’s tenant.



Option 2: Send an invite to the auditor’s existing Company B email to become a guest with restricted access.



Guest users can also be non-business accounts (e.g., Yahoo or Gmail).



### 10\. Permissions for Guest Users



Same as Member User: Rare but possible.



Limited Access (Default):



Cannot search other users/groups.



Can view non-hidden groups and their users.



Restricted Access:



Cannot view anything related to users or groups (even non-hidden ones).



### 11\. Guest Invite Settings



Controls who can invite guests into your tenant:



Anyone (default).



Member users or admins with specific roles.



Only admins with specific roles.



No one (most restrictive).



### 12\. IAB (Identity Access Basics)



Added users, assigned groups, and created static groups.



Removed and restored users/groups.



Added external identity (guest user).



Date: 18th June 2026.



Next Topic: Entra ID Roles \& Role-Based Access Control.



### 13\. Entra ID Roles \& Role-Based Access Control



Entra ID Roles



Manage permissions on Entra ID only.



Examples: Create groups, reset passwords, assign licenses.



Role example: User Administrator.



Role-Based Access Control (RBAC)



Manage permissions on Azure resources (storage, VMs, load balancers).



Grant or deny access to resources.



### 14\. Administrative Units



Allow admins to manage specific groups of users.



Example:



Admin A manages Group 1 (User A \& User B).



Admin A cannot manage User C.



Visual diagram shows Admin A linked to Group 1.



### 15. Things to Remember



Premium P1 or P2 license required for Administrative Unit admins.



Group nesting doesn’t work for Administrative Units - permissions aren’t inherited when a group is added.

