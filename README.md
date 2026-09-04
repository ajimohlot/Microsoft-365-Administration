# Microsoft 365 Administration, Entra ID & Intune Home Lab

## Project Overview

This project demonstrates the administration of a Microsoft 365 environment for a fictional organisation, **Londonbridge Solutions Ltd**, integrating on-premises Active Directory with Microsoft Entra ID and Microsoft Intune.

The lab was designed to go beyond basic configuration by demonstrating how Microsoft 365, Active Directory, hybrid identity and endpoint management work together in a practical environment.

The project covers:

- Microsoft 365 tenant and user administration
- User licensing and administrative roles
- Microsoft 365 groups and shared mailboxes
- Active Directory and Microsoft Entra ID integration
- Microsoft Entra Connect
- Password Hash Synchronization
- OU-based synchronization filtering
- Hybrid Microsoft Entra joined Windows 11 device
- Automatic Intune enrollment using Group Policy
- Intune configuration and compliance policies
- Application deployment
- Hybrid user lifecycle management
- Microsoft 365, Entra ID and Intune troubleshooting
- Hybrid identity synchronization troubleshooting

- ## Table of Contents

- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Lab Environment & Architecture](#lab-environment--architecture)
- [Part 1 - Tenant Setup & User Administration](#part-1---tenant-setup--user-administration)
- [Part 2 - Hybrid Identity with Microsoft Entra Connect](#part-2---hybrid-identity-with-microsoft-entra-connect)
- [Part 3 - Microsoft Intune Device Management & Application Deployment](#part-3---microsoft-intune-device-management--application-deployment)
- [Part 4 - Microsoft 365, Entra ID & Intune Troubleshooting](#part-4---microsoft-365-entra-id--intune-troubleshooting)
- [Part 5 - Hybrid Identity Troubleshooting](#part-5---hybrid-identity-troubleshooting-duplicate-entra-id-user--upn-conflict)
- [Skills Demonstrated](#skills-demonstrated)
- [Troubleshooting Approach](#troubleshooting-approach)
- [Key Lessons](#key-lessons)
- [Project Evidence](#project-evidence)
- [Video Demonstrations](#video-demonstrations)
- [Conclusion](#conclusion)

## Technologies Used

- Microsoft 365 Admin Center
- Microsoft Entra ID
- Microsoft Entra Connect
- Microsoft Intune
- Active Directory Domain Services (AD DS)
- Group Policy
- Windows Server
- Windows 11
- PowerShell
- Microsoft Entra Connect Synchronization Service Manager

## Project Structure

The project is documented across five parts:

| Part | Focus | Video |
|---|---|---|
| **1** | Tenant Setup & User Administration | [Watch on YouTube](https://youtu.be/6dQwy-64h3w) |
| **2** | Hybrid Identity with Active Directory & Microsoft Entra Connect | [Watch on YouTube](https://youtu.be/IRGgU9KL-4I) |
| **3** | Microsoft Intune Device Management & Application Deployment | [Watch on YouTube](https://youtu.be/_ArTc3dFKtM) |
| **4** | Microsoft 365 & Intune Troubleshooting — 6 Scenarios | [Watch on YouTube](https://youtu.be/fxv2mHPc4SE) |
| **5** | Hybrid Identity Troubleshooting — Duplicate Entra ID User & UPN Conflict | [Watch on YouTube](https://youtu.be/Agm0q3j-tSg) |

---

## Lab Environment & Architecture

The lab combines an on-premises Active Directory environment with Microsoft 365 cloud services to simulate a hybrid organisation.

### Environment

| Component | Purpose |
|---|---|
| **DC01** | Active Directory Domain Services, DNS and Microsoft Entra Connect |
| **WIN11-CLIENT01** | Windows 11 domain-joined client used for hybrid join and Intune management |
| **Active Directory** | On-premises identity and group management |
| **Microsoft Entra ID** | Cloud identity and access management |
| **Microsoft Entra Connect** | Synchronization between on-premises AD and Microsoft Entra ID |
| **Microsoft Intune** | Endpoint configuration, compliance and application deployment |
| **Microsoft 365** | User administration, licensing, groups, roles and shared mailboxes |

### Identity Flow

The environment uses **Password Hash Synchronization (PHS)** through Microsoft Entra Connect.

The basic identity and device flow is:

`Active Directory → Microsoft Entra Connect → Microsoft Entra ID → Microsoft Intune`

For device management:

`WIN11-CLIENT01 → Hybrid Microsoft Entra Join → Automatic MDM Enrollment → Microsoft Intune`

This allowed me to manage identities from the appropriate source of authority while extending on-premises users and devices into Microsoft 365 cloud services.

---

## Part 1 - Tenant Setup & User Administration

The first stage of the project focused on establishing the Microsoft 365 environment for **Londonbridge Solutions Ltd** and performing the core administrative tasks required to support users.

### Tasks Completed

- Reviewed the Microsoft 365 tenant and available Business Premium licences
- Created user accounts and maintained user information
- Assigned Microsoft 365 licences
- Created department-based groups
- Added and verified group memberships
- Assigned the Helpdesk Administrator role
- Created an HR shared mailbox
- Configured shared mailbox membership

### Evidence

#### Microsoft 365 Users and Licensing

User accounts were created and the required Microsoft 365 licences were assigned.

![Microsoft 365 Users](1%20Tenant%20Overview%20and%20User%20Administration/M365%2004-All_Users_Created.jpg)

![Licence Assignment](1%20Tenant%20Overview%20and%20User%20Administration/M365%2005-User_Licences_Assigned.jpg)

#### Groups and Administrative Roles

Department-based groups were created to organise users and support role-based access.

![Department Groups](1%20Tenant%20Overview%20and%20User%20Administration/M365%2006-Department_Groups.jpg)

![Helpdesk Administrator Role](1%20Tenant%20Overview%20and%20User%20Administration/M365%2009-Helpdesk_Administrator_Role.jpg)

#### Shared Mailbox

An HR shared mailbox was created and the appropriate users were added as members.

![HR Shared Mailbox](1%20Tenant%20Overview%20and%20User%20Administration/M365%2011-HR_Shared_Mailbox.jpg)

> **Video Demonstration:** [Microsoft 365 Administration Lab | Tenant Setup & User Administration](https://youtu.be/6dQwy-64h3w)

---


## Part 2 - Hybrid Identity with Microsoft Entra Connect

The second stage extended the on-premises Active Directory environment into Microsoft Entra ID using **Microsoft Entra Connect**.

The goal was to create a hybrid identity environment where selected on-premises users could synchronize to Microsoft Entra ID while Active Directory remained the source of authority.

### Tasks Completed

- Verified connectivity from DC01 to Microsoft cloud services
- Reviewed the departmental OU structure in Active Directory
- Verified user UPN configuration
- Installed and configured Microsoft Entra Connect
- Selected Password Hash Synchronization (PHS)
- Configured OU filtering to control synchronization scope
- Completed the initial synchronization
- Triggered and verified a delta synchronization
- Verified synchronized users in Microsoft Entra ID
- Verified existing cloud and on-premises identity matching
- Verified Password Hash Synchronization

### Evidence

#### Active Directory Preparation

The on-premises Active Directory environment and user identities were verified before configuring synchronization.

![Active Directory OU Structure](2%20Hybrid%20Identity%20%26%20Microsoft%20Entra%20Connect/02-AD-Departmental-OU-Structure.jpg)

![AD User UPN Verification](2%20Hybrid%20Identity%20%26%20Microsoft%20Entra%20Connect/03-AD-User-UPN-Verification.jpg)

#### Microsoft Entra Connect Configuration

Password Hash Synchronization and OU filtering were configured to synchronize the required identities.

![Password Hash Synchronization](2%20Hybrid%20Identity%20%26%20Microsoft%20Entra%20Connect/04-Entra-Connect-Password-Hash-Sync.jpg)

![OU Filtering](2%20Hybrid%20Identity%20%26%20Microsoft%20Entra%20Connect/05-Entra-Connect-OU-Filtering.jpg)

#### Synchronization Verification

After configuration, synchronization was run and the resulting identities were verified in Microsoft Entra ID.

![Delta Synchronization Success](2%20Hybrid%20Identity%20%26%20Microsoft%20Entra%20Connect/08-Entra-Connect-Delta-Sync-Success.jpg)

![Synchronized Users](2%20Hybrid%20Identity%20%26%20Microsoft%20Entra%20Connect/09-Entra-Synchronized-Users.jpg)

> **Note:** During the synchronization review, I identified that one existing cloud user had not matched with the corresponding on-premises identity and a duplicate synchronized account had been created. Rather than removing the account without investigation, I documented and investigated the issue separately in **Part 5 - Hybrid Identity Troubleshooting**.

> **Video Demonstration:** [Hybrid Identity Lab | Active Directory & Microsoft Entra Connect](https://youtu.be/IRGgU9KL-4I)

---


## Part 3 - Microsoft Intune Device Management & Application Deployment

The third stage of the project focused on bringing the Windows 11 client into the cloud-managed environment and using Microsoft Intune for endpoint configuration, compliance and application deployment.

### Tasks Completed

- Configured the Windows 11 client for Hybrid Microsoft Entra Join
- Verified the hybrid join using `dsregcmd /status`
- Verified the device in Microsoft Entra ID
- Configured the Microsoft Entra MDM user scope
- Configured automatic MDM enrollment using Group Policy
- Enrolled WIN11-CLIENT01 into Microsoft Intune
- Created an Intune device group
- Created and assigned a Windows 11 configuration baseline
- Verified configuration policy deployment
- Created and assigned a device compliance policy
- Verified device compliance
- Configured application deployment
- Verified application installation on the managed Windows 11 client

### Evidence

#### Hybrid Microsoft Entra Join

The Windows 11 client was configured for Hybrid Microsoft Entra Join and the registration state was verified.

![Hybrid Join Verified](3%20Intune%20Device%20Management%20and%20Application%20Deployment/M365%2003-05%20Hybrid_Join_Verified.jpg)

![Device in Entra ID](3%20Intune%20Device%20Management%20and%20Application%20Deployment/M365%2003-06%20Device_In_Entra.jpg)

#### Automatic Intune Enrollment

Automatic MDM enrollment was configured through Group Policy and the Windows 11 client was successfully enrolled into Microsoft Intune.

![Automatic MDM GPO](3%20Intune%20Device%20Management%20and%20Application%20Deployment/M365%2003-08%20Automatic_MDM_GPO.jpg)

![Windows 11 Intune Enrolled](3%20Intune%20Device%20Management%20and%20Application%20Deployment/M365%2003-11%20WIN11_Intune_Enrolled.jpg)

#### Configuration & Compliance

Configuration and compliance policies were assigned to the managed Windows 11 device.

![Baseline Deployment](3%20Intune%20Device%20Management%20and%20Application%20Deployment/M365%2003-16%20Baseline_Deployment_Succeeded.jpg)

![Device Compliant](3%20Intune%20Device%20Management%20and%20Application%20Deployment/M365%2003-19%20Device_Compliant.jpg)

#### Application Deployment

An application was assigned through Microsoft Intune and installation was verified both in Intune and on the Windows 11 client.

![Application Deployment](3%20Intune%20Device%20Management%20and%20Application%20Deployment/M365%2003-20%20App_Deployment_Assignment.jpg)

![Application Installed on Client](3%20Intune%20Device%20Management%20and%20Application%20Deployment/M365%2003-21%20App_Deployment_Verified_Client.jpg)

> **Video Demonstration:** [Microsoft Intune Lab | Device Management & Application Deployment](https://youtu.be/_ArTc3dFKtM)

---


## Part 4 - Microsoft 365, Entra ID & Intune Troubleshooting

This stage focused on troubleshooting six practical issues across Microsoft 365, Microsoft Entra ID, Microsoft Intune and the hybrid identity environment.

For each scenario, I followed a structured troubleshooting process:

**Identify the problem → Investigate → Determine the root cause → Apply the fix → Verify the result**

### Scenario 1 - Microsoft 365 Licence Issue

A user was unable to access the required Microsoft 365 services.

**Root cause:** The user did not have the required Microsoft 365 licence assigned.

**Resolution:** Assigned the appropriate licence and verified the user's access.

![Unlicensed User](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/1-MICROSOFT%20365%20LICENCE%20ISSUE/M365%2004-01%20Unlicensed_User_Identified.jpg)

![User Access Verified](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/1-MICROSOFT%20365%20LICENCE%20ISSUE/M365%2004%2004%20User_Access_Verified.jpg)

### Scenario 2 - Entra ID Group Membership Issue

An HR user was missing the group membership required for the intended access.

**Root cause:** The user had not been added to the required HR group.

**Resolution:** Restored the group membership and verified the assignment.

![HR Group Membership Missing](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/2-Entra%20group%20membership%20issue/M365%2004-06%20HR_Group_Membership_Missing.jpg)

![HR Group Assignment Verified](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/2-Entra%20group%20membership%20issue/M365%2004-09%20HR_Group_Assignment_Verified.jpg)

### Scenario 3 - Intune Configuration Policy Not Applying

A configuration restriction was not being applied to the managed Windows 11 device.

**Investigation:** I confirmed that the device was managed and that the required settings existed in the Intune configuration profile.

**Root cause:** The configuration profile was not assigned to the required device group.

**Resolution:** Restored the assignment, synchronized the device and verified that the restrictions were applied.

![Intune Assignment Missing](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/3-Intune%20Configuration%20Policy%20Not%20Applying/M365%2004-14%20Intune_Assignment_Missing.jpg)

![Intune Policy Succeeded](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/3-Intune%20Configuration%20Policy%20Not%20Applying/M365%2004-16%20Intune_Policy_Succeeded.jpg)

![Control Panel Policy Verified](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/3-Intune%20Configuration%20Policy%20Not%20Applying/M365%2004-18%20Control_Panel_Policy_Verified.jpg)

### Scenario 4 - Intune Device Compliance Issue

WIN11-CLIENT01 was reporting as noncompliant in Microsoft Intune.

**Investigation:** I reviewed the failed compliance setting and compared the configured minimum OS requirement with the Windows version installed on the device.

**Root cause:** The minimum operating system version configured in the compliance policy did not match the client environment.

**Resolution:** Corrected the requirement and allowed Intune to re-evaluate the device.

![Device Noncompliant](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/4-Intune%20Device%20Compliance%20Issue/M365%2004-19%20Device_Noncompliant.jpg)

![Minimum OS Requirement](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/4-Intune%20Device%20Compliance%20Issue/M365%2004-21%20Minimum_OS_Requirement.jpg)

![Device Compliance Restored](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/4-Intune%20Device%20Compliance%20Issue/M365%2004-24%20Device_Compliance_Restored.jpg)

### Scenario 5 - Application Deployment Troubleshooting

An application assigned through Microsoft Intune was not automatically installing on the Windows 11 client.

**Root cause:** The application was assigned as **Available for enrolled devices** rather than **Required**.

**Resolution:** Changed the assignment to Required and verified successful installation through Intune and on the client.

![Application Available Assignment](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/5-Application%20Deployment%20Troubleshooting/M365%2004-27%20Journal_Available_Assignment.jpg)

![Application Required Assignment](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/5-Application%20Deployment%20Troubleshooting/M365%2004-28%20Journal_Required_Assignment.jpg)

![Application Installed](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/5-Application%20Deployment%20Troubleshooting/M365%2004-30%20Journal_Installed_On_Device.jpg)

### Scenario 6 - Hybrid User Offboarding

The final planned scenario demonstrated the offboarding of a synchronized hybrid user.

Because the account originated in on-premises Active Directory, identity changes were performed at the appropriate source of authority rather than relying only on cloud-side changes.

The process included:

- Signing the user out of Microsoft 365 sessions
- Disabling the account in on-premises Active Directory
- Removing the user from the on-premises Sales security group
- Running an Entra Connect delta synchronization
- Verifying the disabled state in Microsoft Entra ID
- Verifying removal of Sales access
- Removing the Microsoft 365 licence
- Confirming that the licence was reclaimed

![AD Account Disabled](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/6-Hybrid%20User%20Offboarding/M365%2004-34%20Emily_AD_Account_Disabled.jpg)

![Entra Delta Sync Success](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/6-Hybrid%20User%20Offboarding/M365%2004-36%20Entra_Delta_Sync_Success.jpg)

![Cloud Sign-In Blocked](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/6-Hybrid%20User%20Offboarding/M365%2004-38%20Emily_Cloud_SignIn_Blocked.jpg)

![Business Premium Licence Reclaimed](4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/6-Hybrid%20User%20Offboarding/M365%2004-41%20Business_Premium_Licence_Reclaimed.jpg)
> **Video Demonstration:** [Microsoft 365 & Intune Troubleshooting Lab | 6 Real-World Scenarios](https://youtu.be/fxv2mHPc4SE)

---


## Part 5 - Hybrid Identity Troubleshooting: Duplicate Entra ID User & UPN Conflict

While reviewing the hybrid identity synchronization configured earlier in the project, I discovered that **David Brown had two accounts in Microsoft Entra ID**.

The existing cloud account had not matched with the corresponding on-premises Active Directory account. Instead, Microsoft Entra Connect created a second synchronized identity.

Rather than simply deleting one of the accounts, I investigated the synchronization process to determine why the identity match had failed.

### Problem

Two David Brown identities were visible in Microsoft Entra ID:

- An existing cloud-only account
- A second account created through Microsoft Entra Connect synchronization

![Duplicate Accounts](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-01%20David_Duplicate_Accounts.jpg)

### Investigation

I compared both identities and confirmed that the original cloud account had an assigned **Helpdesk Administrator** role while the newly created account was synchronized from on-premises Active Directory.

I then verified David's on-premises identity and UPN configuration.

![Original Cloud Helpdesk Admin](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-02%20David_Original_Cloud_Helpdesk_Admin.jpg)

![AD Identity Verified](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-04%20David_AD_Identity_Verified.jpg)

### Synchronization Error

Microsoft Entra Connect Synchronization Service Manager showed an export error.

Further investigation revealed:

`AttributeValueMustBeUnique`

The detailed error identified a conflict involving David's **UserPrincipalName (UPN)**.

![Entra Connect Export Error](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-05%20Entra_Connect_Export_Error.jpg)

![AttributeValueMustBeUnique Error](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-06%20AttributeValueMustBeUnique_Error.jpg)

![UPN Conflict Identified](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-07%20David_UPN_Conflict_Identified.jpg)

### Root Cause

The existing cloud identity held the **Helpdesk Administrator** role.

Microsoft Entra Connect could not soft-match the incoming on-premises identity with the existing privileged cloud account. This resulted in the synchronized identity being created separately and subsequently produced a UPN conflict during synchronization.

### Resolution

To resolve the identity conflict, I:

1. Temporarily removed the Helpdesk Administrator role from the original cloud account.
2. Removed the duplicate synchronized identity.
3. Permanently removed the duplicate from Deleted users.
4. Triggered a Microsoft Entra Connect delta synchronization.
5. Verified that the synchronization export completed successfully.
6. Confirmed that the remaining David Brown account was now synchronized with the on-premises identity.
7. Restored the Helpdesk Administrator role.

![Admin Role Removed](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-08%20David_Admin_Role_Removed.jpg)

![Entra Connect Export Success](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-11%20Entra_Connect_Export_Success.jpg)

### Final Verification

After remediation, only the intended David Brown identity remained and the account showed that it was synchronized from on-premises Active Directory.

The Helpdesk Administrator role was then restored.

![Hybrid Identity Matched](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-12%20David_Hybrid_Identity_Matched.jpg)

![Helpdesk Administrator Restored](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-13%20David_Helpdesk_Admin_Restored.jpg)

![Final Verification](5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/M365%2005-14%20David_Final_Verification.jpg)

### Key Takeaway

This issue reinforced the importance of investigating **identity matching and source-of-authority behaviour** rather than treating duplicate accounts as a simple deletion problem.

The visible duplicate was only the symptom. Reviewing the Microsoft Entra Connect export error and the conflicting identity attributes was what exposed the underlying cause.

> **Video Demonstration:** [Hybrid Identity Troubleshooting | Duplicate Entra ID User & UPN Conflict](https://youtu.be/Agm0q3j-tSg)

---


## Skills Demonstrated

This project provided hands-on experience across Microsoft 365 administration, hybrid identity and endpoint management, including:

- Microsoft 365 user, licence and group administration
- Administrative role management
- Shared mailbox administration
- Active Directory user and group management
- Microsoft Entra ID identity administration
- Microsoft Entra Connect configuration
- Password Hash Synchronization
- OU-based synchronization filtering
- Hybrid identity matching and synchronization troubleshooting
- Hybrid Microsoft Entra Join
- Group Policy configuration
- Automatic Intune MDM enrollment
- Microsoft Intune device administration
- Configuration profile deployment
- Device compliance management
- Application deployment and troubleshooting
- Hybrid user lifecycle and offboarding
- PowerShell administration and verification
- Structured troubleshooting and root-cause analysis
- Technical documentation

## Troubleshooting Approach

A major focus of this project was not simply completing configuration tasks, but understanding how to investigate issues when the expected result was not achieved.

Across the troubleshooting scenarios, I used the following approach:

**Identify → Investigate → Isolate the root cause → Resolve → Verify**

This included checking configuration and assignments, validating identity and device state, reviewing synchronization results, using PowerShell for verification, and confirming that each resolution produced the expected result.

## Key Lessons

Some of the main lessons from the project were:

- In a hybrid environment, understanding the **source of authority** is important when managing users and access.
- Successful configuration does not always mean successful deployment; the final state should always be verified.
- Intune policy and application deployment can require synchronization and processing time before changes appear on a managed device.
- Microsoft Entra Connect synchronization errors can reveal identity conflicts that are not obvious from the Entra admin center alone.
- Duplicate identities should be investigated before accounts are deleted.
- Administrative roles can affect hybrid identity matching behaviour.
- Troubleshooting should focus on identifying the underlying cause rather than only correcting the visible symptom.

## Project Evidence

The repository contains the complete screenshot evidence captured throughout the project. The README displays selected screenshots, while the folders contain the full implementation and troubleshooting record.

- [Part 1 - Tenant Overview and User Administration](./1%20Tenant%20Overview%20and%20User%20Administration/)
- [Part 2 - Hybrid Identity & Microsoft Entra Connect](./2%20Hybrid%20Identity%20%26%20Microsoft%20Entra%20Connect/)
- [Part 3 - Intune Device Management and Application Deployment](./3%20Intune%20Device%20Management%20and%20Application%20Deployment/)
- [Part 4 - Microsoft 365, Entra ID, Intune Troubleshooting & User Lifecycle](./4%20Microsoft%20365%20%20Entra%20%20Intune%20Troubleshooting%20%26%20User%20Lifecycle/)
- [Part 5 - Hybrid Identity Troubleshooting: Duplicate Entra ID User](./5%20Hybrid%20Identity%20Troubleshooting%20Duplicate%20Entra%20ID%20User/)

## Video Demonstrations

The complete project is also documented as a five-part video series:

1. [Microsoft 365 Administration Lab | Tenant Setup & User Administration](https://youtu.be/6dQwy-64h3w)
2. [Hybrid Identity Lab | Active Directory & Microsoft Entra Connect](https://youtu.be/IRGgU9KL-4I)
3. [Microsoft Intune Lab | Device Management & Application Deployment](https://youtu.be/_ArTc3dFKtM)
4. [Microsoft 365 & Intune Troubleshooting Lab | 6 Real-World Scenarios](https://youtu.be/fxv2mHPc4SE)
5. [Hybrid Identity Troubleshooting | Duplicate Entra ID User & UPN Conflict](https://youtu.be/Agm0q3j-tSg)

## Conclusion

This project brought together several technologies that are often managed as part of the same business environment: **Active Directory, Microsoft Entra ID, Microsoft 365 and Microsoft Intune**.

Rather than treating each technology as an isolated lab, I used them together to build and manage a hybrid environment covering identity, endpoint management, access, application deployment, user lifecycle management and troubleshooting.

The unexpected duplicate identity issue also provided an opportunity to demonstrate the most important part of the project: investigating a problem methodically, identifying the root cause, applying the appropriate resolution and verifying the final result.
