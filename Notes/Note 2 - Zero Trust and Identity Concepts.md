# **Note 2 - Zero Trust Principles**

### *Guidance for Technical Implementation*

\---

## 

## **Core Principles**

* **Verify explicitly**
* **Use least privileged access**
* **Assume breach**

\---

## 

## **Step 1: Verify Explicitly**

Always authenticate and authorize based on all available data points, including:

* **Device health**
* **User identity and location**
* **Service or workload content**
* **Data classification**
* **Anomalies**

\---

## 

## **Step 2: Use Least Privileged Access**

After verification, access should be granted based on the principle of **least privilege** - only the minimum level of access required to perform tasks, and only for as long as necessary.

### 

### **Key Concepts**



**Just in Time (JIT)**
Access is granted only at the moment it is needed and revoked immediately after.

**Just Enough Access (JEA)**
Users receive only the permissions required for the specific task - nothing more.

**Risk-based Adaptive Policies**
Access decisions dynamically adjust based on real-time risk signals.

**Data Protection Against Out-of-Band Vectors**
Safeguards extend beyond primary channels to prevent indirect data exposure.

\---

## 

## **Step 3: Assume Breach**



Operate under the assumption that a breach is not just possible but likely.

* **Possible** - non-zero chance of occurrence
* **Likely** - high probability of occurrence

### 

### **Required Actions**



**Segment access** by network, user, devices, and application awareness.

**Encrypt all sessions** end-to-end without exception.

**Use analytics** for threat detection, posture visibility, and continuous improvement of defences.

\---

# 

# **Identity Concepts**

\---

## 

## **Why Use an Identity**



**Authentication** - Proves what or who we are.

**Authorization** - Grants permission to perform an action.

**Auditing** - Reports on what was done and by whom.

**Administration** - Allows an identity to be self-managed.

\---

## 

## **What Is an Identity Provider (IdP)**



An **Identity Provider (IdP)** is a system that creates, manages, and stores digital identities.

> Example: \*\*Microsoft Entra ID\*\*

### 

### **Common Components**

* Repository of user identities
* Authentication system
* Security protocols defending against intrusion
* Trusted entity

\---

## 

## 

## **How Identity Providers Work**

### 

### **Traditional Method**



The client sends a username and password directly to the server or service.

> `Client → Username/Password → Server/Service`

### 

### **Modern Approach**



The client communicates with the Identity Provider (IdP) *first*, before reaching any service.

\---

### 

### **Authentication Flow**



**Step 1** - The client provides credentials (username and password) to the IdP.

**Step 2** - The IdP authenticates the client and issues a **security token** or **security claim**.

**Step 3** - The token defines who the client is and what level of access they have.

\---

### 

### **Client–Server Interaction**



**Step 1** - The client attempts to access a service.

**Step 2** - The service requests authentication.

**Step 3** - The client redirects the request to the IdP.

**Step 4** - The IdP validates the identity and sends a token back to the server.

**Step 5** - The server must trust and recognise the IdP for this to succeed.

\---

### 

### **Server Validation**



The server verifies the token using the **public key** of the IdP.

Once validated, the server registers the client and issues a **cookie** - proof of authentication for subsequent connections.

> A cookie is a signed cryptographic token used for ongoing sessions.

\---

### 

### **Example: Adele's Authentication Flow**



Adele requests access to two services. Each service receives its own unique token and cookie - there is no correlation between them.

**Website access**
IdP issues Token T1 → Browser receives Cookie C1

**SharePoint access**
IdP issues Token T2 → SharePoint receives Cookie C2

\---

### 

### **Token Generation**



Each token is unique to the specific service requesting authentication. Tokens are generated using the following protocols:

* **SAML** - XML format
* **WS-Federation** - XML format
* **OpenID Connect** - JSON format

\---

## 

## **Single Sign-On (SSO)**



A feature that allows users to authenticate **once** and access multiple services without re-authenticating.

> Example: \*\*Microsoft Entra ID\*\* in the cloud.

\---

### 

### **SSO Scenario: Adele at Contoso**



Adele, an administrator at Contoso, registers using Microsoft's cloud services (Entra ID, Azure, or M365).

**Primary Domain Setup**

* Adele provides employer details (Contoso) and personal information.
* She chooses a primary domain - for example, `contoso.onmicrosoft.com`.
* All domain names end with `.onmicrosoft.com`.
* This process is called **Creating a Tenant**.
* Adele becomes the first user with **Global Administrator** access.

\---

## 

## **Microsoft Entra ID - Architecture and Key Terms**

\---

### 

### **Subscription**

*Pay over time for services and features.*

Used to purchase specific Azure cloud services. Billing is ongoing rather than a one-time purchase.

\---

### 

### **Tenant**

*The digital representation of your organisation.*

Example: `contoso.com`. A tenant is the dedicated environment created when an organisation registers with Microsoft's cloud services.

\---

### 

### **Identity**

*An object in Microsoft Entra ID that gets authenticated.*

Rights and access to resources are assigned to identities. An identity can represent a person, device, or application.

\---

## 

## **Account, User, and Identity - Key Distinctions**

\---

### 

### **Identity**

Defines the *existence* of something or someone in the system. It is the foundational concept - the "who or what" before any access is considered.

\---

### 

### **Account**

An identity that has **data associated with it**. Defines how that identity accesses services. Not every identity is an account, but every account is an identity.

\---

### 

### **User**

A **verified account** associated with a real person. The user is the actual human or software agent interacting with the system's elements.

\---



