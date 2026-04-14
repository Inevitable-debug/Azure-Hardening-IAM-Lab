
# Azure-Hardening-IAM-Lab

## ℹ️ Overview
In this project, it will involve hardening an Identity and Access Management (IAM) tenant by applying the principle of least privilege, separation of duties and ensuring a secure baseline by disabling any unnecessary services. The existing lab has been misconfigured, exposing a huge security vulnerability in which Agent Smith can compromise Trinity's account. Smith was assigned the role of Help Desk by accident, enabling him to reset the passwords of low privilege users and other Help Desk administrators. This means Smith can reset Trinity's password, break into her account, and access a Sharepoint that has been shared with her over email. [This lab](/exploitation) will demonstrate Smith exploiting the situation to his advantage, our efforts to harden the system after the fact, and the new Role Based Access Control topology. 

---

## Misconfigured IAM Environment
<img width="562" height="402" alt="IAM Diagram drawio" src="https://github.com/user-attachments/assets/0a1f9a9a-0232-476c-b978-a6676f4f0999" />

---

## Risk Assessment
A detailed breakdown of the risks associated with overprivileging Agent Smith's account with the permissions of Helpdesk Administrator can be found [here](/risk%20report).

---

## Secure Design Changes

## Validation

## Lessons Learnt

