# Azure-Hardening-IAM-Lab

## ℹ️ Overview
In this project, it will involve hardening an Identity and Access Management (IAM) tenant by applying the principle of least privilege, separation of duties and ensuring a secure baseline by disabling any unnecessary services. The existing lab has been misconfigured, exposing a huge security vulnerability in which Agent Smith can compromise Trinity's account. Smith was assigned the role of Help Desk by accident, enabling him to reset the passwords of low privilege users and other Help Desk administrators. This means Smith can reset Trinity's password, break into her account, and access a Sharepoint that has been shared with her over email. [This lab](/exploitation) will demonstrate Smith exploiting the situation to his advantage. A risk assessment was also drafted to highlight the dangers to organisational resources, staff and customers [here](/risk%20report). The role based access control (RBAC) system will also be reconfigured to ensure that no user has excess privileges and general security hygiene practises will be applied.

---

## Misconfigured IAM Environment
<img width="562" height="402" alt="IAM Diagram drawio(1)" src="https://github.com/user-attachments/assets/0e35d2a3-dee6-4427-82e7-d5a9f5eb0bd1" />

In this diagrammatical representation of an IAM Environment, Agent Smith has been misassigned the role of Helpdesk Administrator. This elevates his permissions to manage tickets, read and update User Accounts of a similar privilege level or below. Administrative Actions is diagramatically represented highlighting key permissions that
have a direct or indirect relation to the security breach, as well as which roles can use them. Users and Groups are also another collection of resources which showcase
how these roles can interact with them. 

Below will be an explanation of how CRUD was scoped to an IAM Context in managing users and groups.

— Create: Provision a new User Account in the Microsoft Tenant

— Read: View the administrative units, roles, or identifying information of a User Account

— Update: Change a password, role, or property about the User Account

— Delete: Terminate the User Account from the Microsoft Tenant

> [!NOTE]
> User provision and role assignment is hierarchically scoped. For example, a Global Administrator can provision other Global Administrators, but a User Administrator cannot provision a Global Administrator

---

## Secure Design Changes
Multiple security measures were implemented after this security breach. The roles were misconfigured, Security Defaults were disabled, and Per-User MFA was off. These steps
listed below will fix these issues.

### Step 1: RBAC was reconfigured 
<img width="562" height="402" alt="IAM Diagram drawio(2)" src="https://github.com/user-attachments/assets/00957fe4-59a5-411e-8fe4-3169955e5ee1" />

This was reconfigured to exclude Agent Smith from the HelpDesk Administrator role, which helped to contain the security breach. 

### Step 2: Turn on Security Defaults
<img width="562" height="402" alt="9" src="https://github.com/user-attachments/assets/23b9897c-8e64-4512-a812-12a305611394" />

Security Defaults were enabled, blocking legacy authentication mechanisms, ensuring Multi-Factor Authentiction is enforced platform wide, providing protection against phishing attacks, and generally providing a much stronger security baseline. 

### Step 3: Turn on Per-User MFA
<img width="562" height="402" alt="10" src="https://github.com/user-attachments/assets/666f4a51-658e-4199-ab42-7df0d4b09e53" />

Per-User MFA was turned off for each User in the Tenant, and although MFA would be enforced regardless due to Security Defaults, it is good security hygiene to turn it on again.

## Validation

## Lessons Learnt

