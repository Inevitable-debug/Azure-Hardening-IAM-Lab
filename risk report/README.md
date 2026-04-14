# Risk Assessment

## Background
This security risk assessment is being performed, as the Microsoft 365 User Agent Smith was misassigned the role of Helpdesk Administrator.
Trinity, another Microsoft 365 Helpdesk Administrator, is in danger of having her account's security compromised. Agent Smith can reset
the passwords of other Helpdesk Administrators, which threatens to weaken the security posture of Trinity's account. Trinity contains
access to a SharePoint that could contain sensitive company information. As such, this is regarded as an 'Information Asset' (IA), which has financial,
technological, or commercial value to the business objectives of this organisation. While most employees have access to IA resources that are classified under
'Internal Use', each individual Microsoft 365 User Account with administrative privileges might have access to confidential company information. As such, this is a serious security risk, and must be contained
effective immediately.

## Scope
The scope of this security risk assessment focuses on Role-based Access Control (RBAC) in Microsoft Entra ID and the Microsoft Azure Admin Center. It assesses the attack
surface area of Trinity's account to Agent Smith's potential intrusion attempts and the most logical attack vector. In this case, the attack vector would likely be a password
reset, allowing Agent Smith to bypass one layer of defense. The security of Neo and Morpheus' Microsoft 365 Administrator accounts are excluded from this risk assessment. 
This is because a Helpdesk Administrator lacks the sufficient permissions to weaken the security posture of those accounts or take them over. However, it is possible
that Trinity's account could be leveraged to perform a phishing attack against these accounts if her account was assigned with a Microsoft 365 Business licensing. Thus, a potential
phishing attack will be considered, but it is of low risk.

## Methodology
The assessment was undertaken by reviewing the current roles that are assigned to each user in the Microsoft 365 Tenant. These findings were diagramatically
represented in an RBAC diagram, showcasing what each role a user has been assigned, and what functions they can perform. The discovery that Agent Smith has excess
privileges was alarming, as it conflicts with the International Cybersecurity Benchmark ISO/IEC 27001. The idea that Agent Smith might be able to potentially compromise
the Confidentiality, Integrity and Availability of Trinity's account contradicts the core philosophy of the ISO/IEC 27001 model. Confidentiality could be compromised,
as if Smith successfully logs into Trinity's account, he will have access to her data. Integrity could also be affected, as Smith can modify existing files, databases, or directory
structures Trinity might currently have in her account. Availability may also be impacted, as Smith might lockout Trinity from being able to login due to her account being in use.
The ISO/IEC 27001 model is built on these 3 pillars of data security, and on the effective prioritisation, as well as management of risk. The most effective security controls within
the skillset, knowledge and awareness of this team will be applied to fix this security leak.

The Mitre ATT&CK Framework was used as a reference point to support the analysis of threats from Agent Smith's account. Although the tactics and techniques will not perfectly 
match every unique security breach, the goal is to choose ones of best fit. In this case, the tactic Initial Access, and the technique 'Valid Accounts: Cloud Accounts' 
is an apt fit. Initial Access refers to a user trying to infiltrate a network. Once this is granted, a foothold can be established by compromising a valid account, which
can facilitate accessing external services. In this case, Agent Smith infiltrated the network, and by potentially accessing Trinity's account, it could expose the secrets
in Trinity's SharePoint. The 'Valid Accounts: Cloud Accounts' technique's identifier is T1078.004, and specifies misconfigurations in role permissions can enable an attacker
to leverage those permissions outside the scope of their account to harvest data.

## Summary
| ID  | Classification                          | Risk                                                | Current Risk        | Mitigation Strategy |
|-----|------------------------------------------|-----------------------------------------------------|---------------------|---------------------|
|  1  | **Account Compromise**                  | **Compromise of Trinity's Account**                 | High                | Mitigate            | 
|  2  | **Confidentiality and Data Protection** | **Unauthorised Access of Sharepoint**               | High                | Mitigate            | 
|  3  | **Insider Threats**                     | **Internal Guest Account With Elevated Privileges** | High                | Mitigate            | 
|  4  | **Processes and Organisation**          | **Service Request Interception**                    | Medium              | Mitigate            |
|  5  | **Social Engineering**                  | **Business Email Compromise**                       | Low                 | Accept              |

## Business Unit Acknowledgement
I certify that I have verified all risks identified and the remediations recommended. 
Where they have been accepted, the remediations will be applied within the agreed timeframe. 
I understand the consequences of accepting any risks above the risk appetite. These risks have
been added to the business unit’s risk register for monitoring and future remediation, where applicable.

| Name                         | Position                                         | Date       |  Signature              |
|------------------------------|--------------------------------------------------|------------|------------------------|
| **Michael Mountjoy**         | Cybersecurity Auditor                            | 14/04/2026 | _**Michael Mountjoy**_ |
| **Thomas Anderson**          | Global Administrator                             | 14/04/2026 | _**Thomas Anderson**_  |

## Details
<table>
  <tr>
    <th colspan = "4">Risk #1: Compromise of Trinity's Account</th>
  </tr>
  <tr>
    <th>Description</th>
    <td>[Describe the cause of the risk]</td>
  </tr>
  <tr>
    <th>Cause</th>
    <td>Cause of risk</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Current risk</th>
    <td>Choose an item</td>
    <td>Choose an item</td>
    <td>Choose an item</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Choose an item</td>
    <td>Choose an item</td>
  </tr>
  <tr>
    <th>Recommended treatment</th>
    <td colspan = "3">Recommended treatment to bring risk to an acceptable level</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Residual Risk</th>
    <td>Choose item</td>
    <td>Choose item</td>
    <td>Choose item</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <th>Management Response</th>
    <td>Choose</td>
    <td>Provide rationale for risk strategy</td>
  </tr>
</table>
