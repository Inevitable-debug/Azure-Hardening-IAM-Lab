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
|-----|-----------------------------------------|-----------------------------------------------------|---------------------|---------------------|
|  1  | **Account Compromise**                  | **Compromise of Trinity's Account**                 | High                | Mitigate            | 
|  2  | **Confidentiality and Data Protection** | **Unauthorised Access of Sharepoint**               | High                | Mitigate            | 
|  3  | **Insider Threats**                     | **Reconaissance on Administrative Units**           | Medium              | Mitigate            | 
|  4  | **Processes and Organisation**          | **Service Request Interception**                    | Medium              | Mitigate            |
|  5  | **Social Engineering**                  | **Abuse of Misassigned Authority**                  | Low                 | Accept              |

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
    <td colspan = "3">Agent Smith can reset Trinity's password and may be able to disable or bypass Multi-Factor Authentication (MFA)</td>
  </tr>
  <tr>
    <th>Cause</th>
    <td colspan = "3">Misconfiguration of roles for users in the Microsoft 365 Tenant</td>
  </tr>
  <tr>
    <th>Potential Impact</th>
    <td colspan = "3">Operational disruption of services, loss of finances (legal costs, wage costs), reputational damage, legal liabilities, psychological impacts on employees and customers</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Current risk</th>
    <td>Possible</td>
    <td>Major</td>
    <td>High</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Agent Smith can already bypass a layer of defense; only one remaining is MFA, which might be able to be bypassed or disabled</td>
    <td>Confidential data could be compromised and Trinity's account can be used as a basis for social engineering</td>
    <td></td>
  </tr>
  <tr>
    <th>Recommended treatment</th>
    <td colspan = "3">Configure role-based access control properly; revoke access to Helpdesk Administrator from Agent Smith</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Residual Risk</th>
    <td>Rare</td>
    <td>Moderate</td>
    <td>Low</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Applying the security controls rectifies the problem, but maybe some risk can remain if Smith establishes a foothold or exfiltrates sensitive data</td>
    <td colspan = "2">If residual risk remains, it is likely to be limited by the permissions of Helpdesk administrator - troublesome, but not a nightmare. </td>
  </tr>
  <tr>
    <th>Management Response</th>
    <td>Mitigate</td>
    <td colspan = "2">The risk proposes a systemic security vulnerability in the Microsoft tenant to both customers submitting support tickets, company personnel and data.</td>
  </tr>
</table>

---

<table>
  <tr>
    <th colspan = "4">Risk #2: Unauthorised Access of Sharepoint</th>
  </tr>
  <tr>
    <th>Description</th>
    <td colspan = "3">If Agent Smith compromises Trinity's account, he will be able to access her Sharepoint and the data therein. (MFA)</td>
  </tr>
  <tr>
    <th>Cause</th>
    <td colspan ="3">Compromise of Trinity's Microsoft 365 Tenant user account</td>
  </tr>
  <tr>
    <th>Potential Impact</th>
    <td colspan = "3">Exposure of potential company secrets erodes financial value, loss of trust over Trinity's privacyy</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Current risk</th>
    <td>Possible</td>
    <td>Moderate</td>
    <td>High</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Risk of accessing Trinity's SharePoint is contingent on him compromising her account; both risks are possible</td>
    <td>Smith compromising Trinity's SharePoint could yield customer records, IP rights, or confidential data. It is unknown - so risk is moderate/unknown.</td>
    <td></td>
  </tr>
  <tr>
    <th>Recommended treatment</th>
    <td colspan = "3">Secure the SharePoint by enforcing robust RBAC, ensuring Smith cannot establish a foothold in Trinity's account</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Residual Risk</th>
    <td>Rare</td>
    <td>Moderate</td>
    <td>Low</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>If Smith can exploit some sort of open API in Microsoft 365 or from the Sharepoint, he may gain access; otherwise it is rare to have residual risk.</td>
    <td colspan = "2">Assuming the SharePoint is still compromised somehow, it would once again expose all the data within it. A moderate amount of risk but not a disaster. </td>
  </tr>
  <tr>
    <th>Management Response</th>
    <td>Mitigate</td>
    <td colspan = "2">An encryption-at-rest encryption scheme can be applied to ensure the data is secured while in Trinity's SharePoint. Even if her SharePoint is compromised, it provides an extra layer of         defense.</td>
  </tr>
</table>

---

<table>
  <tr>
    <th colspan = "4">Risk #3: Reconaissance on Administrative Units</th>
  </tr>
  <tr>
    <th>Description</th>
    <td colspan = "3">Agent Smith has read permissions as HelpDesk Administrator to view Administrative Units (AUs) on Member accounts</td>
  </tr>
  <tr>
    <th>Cause</th>
    <td colspan ="3">HelpDesk Administrator role grants Smith read permissions to view AUs of Member Accounts</td>
  </tr>
  <tr>
    <th>Potential Impact</th>
    <td colspan = "3">Negligible impacts; potentially a long term impact if this intelligence gathering leads to a hack later</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Current risk</th>
    <td>Likely</td>
    <td>Minor</td>
    <td>Low</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Smith is likely to have viewed the AUs on Member Accounts if he has a basic understanding of what his role grants, and it has a low opportunity cost to check</td>
    <td>Loss of confidentiality of AUs that have been distributed to the Member accounts within the Microsoft Tenant</td>
    <td></td>
  </tr>
  <tr>
    <th>Recommended treatment</th>
    <td colspan = "3">Revoke Smith's access to the HelpDesk Administrator role; this prevents his read-only permissions to view the AUs</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Residual Risk</th>
    <td>Rare</td>
    <td>Minor</td>
    <td>Low</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Smith is unlikely to circumvent his loss of read permissions unless he establishes a deeper foothold. Thus, it is rare for there to be residual risk.</td>
    <td colspan = "2">There could still be a minor threshold of damage done if Smith recorded the AUs and the Tenant did not change them to invalidate Smith's intelligence gathering </td>
  </tr>
  <tr>
    <th>Management Response</th>
    <td>Mitigate</td>
    <td colspan = "2">Change the existing AUs on Member Accounts to nullify Smith's intelligence gathering and implement measures to secure the resources themselves that the member accounts can access.</td>
  </tr>
</table>

---

<table>
  <tr>
    <th colspan = "4">Risk #4: Service Request Interception</th>
  </tr>
  <tr>
    <th>Description</th>
    <td colspan = "3">Agent Smith can intercept Service Requests from customers or users through the Azure ticketing system. He could exploit them for financial gain or compromise their systems as well.</td>
  </tr>
  <tr>
    <th>Cause</th>
    <td colspan ="3">Smith's permissions as a HelpDesk Administator allows him to manage Service Requests from users or customers.</td>
  </tr>
  <tr>
    <th>Potential Impact</th>
    <td colspan = "3">Operational disruption of services, loss of consumer trust, legal liabilities, reputational damages</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Current risk</th>
    <td>Possible</td>
    <td>Major</td>
    <td>High</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Depending on Smith's agenda, he could intercept these requests if he is pursuing financial gain or wants to spread a virus (e.g Bitcoin Miner) to other PCs.</td></td>
    <td>Significant potential reputational, legal or regulatory damage if Smith is able to successfully impersonate an employee and exploit a user of their services.</td>
    <td></td>
  </tr>
  <tr>
    <th>Recommended treatment</th>
    <td colspan = "3">Revoke Smith's access to the HelpDesk Administrator role; this ensures they can no longer manage ticketing requests.</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Residual Risk</th>
    <td>Unlikely</td>
    <td>Major</td>
    <td>Low</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Smith is unlikely to be able to finish his potential exploitation of a customer or user from a ticket after having his permissions revoked. </td>
    <td colspan = "2">Smith might still be able to exploit a user based on the information he receives from a support ticket, which can tarnish organisational reputation and incur legal liabilities. </td>

  </tr>
  <tr>
    <th>Management Response</th>
    <td>Mitigate</td>
    <td colspan = "2">Revoke Smith's access to HelpDesk Administrator and immediately contact any customers Smith served through the Ticketing Portal for potential damage control.</td>
  </tr>
</table>

---

<table>
  <tr>
    <th colspan = "4">Risk #5: Abuse of Misassigned Authority</th>
  </tr>
  <tr>
    <th>Description</th>
    <td colspan = "3">If Smith was provisioned a Microsoft 365 License to access Outlook, he could phish other members of the organisation, existing customers, or potential ones as Helpdesk Administrator.</td>
  </tr>
  <tr>
    <th>Cause</th>
    <td colspan ="3">Smith's foothold in the HelpDesk Administrator role privileges him with the authority of a trustworthy member of the organisation.</td>
  </tr>
  <tr>
    <th>Potential Impact</th>
    <td colspan = "3">Legal liabilities, reputational damage, financial loss (legal fees), psychological impacts on employees and customers</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Current risk</th>
    <td>Rare</td>
    <td>Moderate</td>
    <td>Low</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Smith would have to convince another a User, Licensing or Global Administrator to assign him a Microsoft 365 License, which is exceedingly unlikely.</td></td>
    <td>Smith would be able to abuse his misassignment of power to trick users into trusting him and divulging personal information, or clicking on malicious phishing links.</td>
    <td></td>
  </tr>
  <tr>
    <th>Recommended treatment</th>
    <td colspan = "3">Revoke Smith's access to the HelpDesk Administrator role; contact any affected parties and offer remediation support.</td>
  </tr>
  <tr>
    <th></th>
    <th>Likelihood</th>
    <th>Consequence</th>
    <th>Risk Level</th>
  </tr>
  <tr>
    <th>Residual Risk</th>
    <td>Rare</td>
    <td>Minor</td>
    <td>Low</td>
  </tr>
  <tr>
    <th>Justification</th>
    <td>Some existing systems might have been successfully phished and presently infected. This would be rare, as a license is needed to do this and it is doubtful Smith could obtain it.</td>
    <td colspan = "2">If Smith could somehow pull off obtaining a Microsoft 365 License and infecting other systems with phishing malware, then the consequence could be moderate. </td>

  </tr>
  <tr>
    <th>Management Response</th>
    <td>Mitigate</td>
    <td colspan = "2">Revoke Smith's access to HelpDesk Administrator and immediately contact any customers Smith reached out to over email; offer remediation efforts and support.</td>
  </tr>
</table>

## Document Control
<table>
  <tr>
    <th>Document ID</th>
    <td>IAM-RISK-LAB-01</td>
  </tr>
  <tr>
    <th>Version</th>
    <td>0.7</td>
  </tr>
  <tr>
    <th>Classification</th>
    <td>Public</td>
  </tr>
  <tr>
    <th>Approval by</th>
    <td>Michael Mountjoy</td>
  </tr>
  <tr>
    <th>Approval date</th>
    <td>15/04/2026</td>
  </tr>
  <tr>
    <th>Next review date</th>
    <td>20/04/2026</td>
  </tr>
  <tr>
    <th>Contact person</th>
    <td>Michael Mountjoy</td>
  </tr>
</table>

## Revision History
<table>
  <tr>
    <th>Version</th>
    <th>Date</th>
    <th>Summary of Change</th>
    <th>Author</th>
  </tr>
  <tr>
    <td>0.1</td>
    <td>13/04/2026</td>
    <td>Scaffolding of headers for risk report</td>
    <td>Michael Mountjoy</td>
  </tr>
  <tr>
    <td>0.2</td>
    <td>14/04/2026</td>
    <td>Drafted proper Cybersecurity Risk Assessment Structure from Gov. of South Australia</td>
    <td>Michael Mountjoy</td>
  </tr>
  <tr>
    <td>0.3..0.9</td>
    <td>15/04/2026</td>
    <td>Completed risk assessment</td>
    <td>Michael Mountjoy</td>
  </tr>
  <tr>
    <td>1.0</td>
    <td>n/n/n</td>
    <td>Finishing touches to the report</td>
    <td>Michael Mountjoy</td>
  </tr>
</table>
