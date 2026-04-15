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
<img width="910" height="650" alt="9" src="https://github.com/user-attachments/assets/23b9897c-8e64-4512-a812-12a305611394" />

Security Defaults were enabled, blocking legacy authentication mechanisms, ensuring Multi-Factor Authentiction is enforced platform wide, providing protection against phishing attacks, and generally providing a much stronger security baseline. 

### Step 3: Turn on Per-User MFA
<img width="910" height="650"  alt="10" src="https://github.com/user-attachments/assets/666f4a51-658e-4199-ab42-7df0d4b09e53" />

Per-User MFA was turned off for each User in the Tenant, and although MFA would be enforced regardless due to Security Defaults, it is good security hygiene to turn it on again.

## Validation

<table>
  <tr>
    <th>Test ID</th>
    <th>Scenario</th>
    <th>Test Steps</th>
    <th>Expected Result</th>
    <th>Actual Result</th>
    <th>Status</th>
  </tr>
  
  <tr>
    <td>TC-01</td>
    <td>Ensuring Agent Smith lacks read and update permissions</td>
    <td>
        1. Sign in as Smith
        2. Navigate to Users
        3. Check read/write/update permissions
    </td>
    <td>No read/write/update permissions</td>
    <td>Result as expected</td>
    <td>Pass</td>
  </tr>
  
  <tr>
    <td>TC-02</td>
    <td>Confirming Smith's roles have been revoked through the view of a Global Administrator</td>
    <td>
        1. Login as Global Administrator
        2. Navigate to Users
        3. Click on Agent Smith 
        4. Select Assigned Roles
    </td>
    <td>Smith has no assigned role</td>
    <td>Result as expected</td>
    <td>Pass</td>
  </tr>
  
  <tr>
    <td>TC-03</td>
    <td>Testing whether MFA works by trying to sign in as a Microsoft Tenant User</td>
    <td>
        1. Sign in as any Microsoft Tenant User
        2. User can press next but will be presented with MFA screen
    </td>
    <td>MFA should be enforced at sign in with any user</td>
    <td>Result as expected</td>
    <td>Pass</td>
  </tr>

  <tr>
    <td>TC-04</td>
    <td>Confirming Security Defaults are enabled for the Microsoft Tenant</td>
    <td>
        1. Once signed-in, navigate to Overview under Entra ID
        2. Click Properties
        3. Scroll to bottom and check if it has been enabled
    </td>
    <td>Security Defaults should be enabled</td>
    <td>Result as expected</td>
    <td>Pass</td>
  </tr>

  <tr>
    <td>TC-05</td>
    <td>Checking to see if Per-User MFA was enabled</td>
    <td>
        1. Once signed-in, navigate to Users
        2. Click the three dots ⋯ and click Per-User MFA
        3. Check whether MFA has been enabled/enforced per user
    </td>
    <td>Every user should either have MFA enforced or enabled</td>
    <td>Result as expected</td>
    <td>Pass</td>
  </tr>
  
</table>

## Lessons Learnt
- Elected person(s) should sign off on granting administrative privileges
- Enforce the rollout of secure baselines
- Structured change management process (features, policies, roles)
