# Hybrid-Active-Directory-Entra-ID-Identity-Lab

![Architecture](https://img.shields.io/badge/Architecture-Hybrid%20Identity-blue)
![Host OS](https://img.shields.io/badge/Host%20OS-Fedora%20Linux-blue)
![Hypervisor](https://img.shields.io/badge/Hypervisor-KVM%2Fvirt--manager-orange)
![Directory](https://img.shields.io/badge/Identity-Active%20Directory%20%7C%20Microsoft%20Entra%20ID-green)

Automated deployment and sync of a hybrid Windows Server Active Directory environment with Microsoft Entra ID using Microsoft Entra Connect.

## Overview
In this project, I designed, deployed, and configured a hybrid identity environment bridging on-premises Active Directory and Microsoft Entra ID. The home lab runs on a Fedora Linux host utilizing QEMU/KVM for virtualization, with Microsoft Entra Connect and Password Hash Sync (PHS) handling identity synchronization.

## Architecture Diagram

<I><B>Click the image below to view the full-sized diagram.</B></I>

<a href="https://raw.githubusercontent.com/NelkoBiH/Hybrid-Active-Directory-Entra-ID-Identity-Lab/main/docs/hybrid-lab.png">
  <img src="docs/hybrid-lab.png" alt="Hybrid Active Directory and Entra ID Architecture">
</a>

## Lab Prerequisites / Setup

* **Host Machine:** Fedora Linux Workstation (`virt-manager` / KVM Hypervisor)
* **On-Premises Infrastructure:** Windows Server 2025 Evaluation Domain Controller (`DC01.lab.local`)
* **Cloud Infrastructure:** Microsoft Entra ID Tenant
* **Synchronization Pipeline:** Microsoft Entra Connect Sync (Password Hash Synchronization - PHS)
* **Security & Governance:** Scoped Role-Based Access Control (RBAC) & Security Defaults

---

##  Key Project Milestones

### On-Premises Organizational Unit (OU) & User Design
Structured directory layout (`OU=Corporate_Users`, `OU=Corporate_Groups`) populated with test identities (`jdoe`, `asmith`) and populated attributes:

![Active Directory Setup](assets/17-active-directory.png)

### Microsoft Entra Connect Synchronization Scope
Filtering directory synchronization exclusively to target active Organizational Units:

![OU Filtering Configuration](assets/30-entra-connect.png)

### Cloud Role-Based Access Control (RBAC)
Delegating the cloud **Helpdesk Administrator** role to a synced on-premises identity (`jdoe`):

![Role Assignment](assets/37-assigning-roles.png)

---

## 📷 Complete 41-Screenshot Documentation Gallery

<details>
<summary><b>Phase 1: Windows Server VM & Network Setup (Images 01–05)</b></summary>
<br>

* **Initial Windows Server Setup:**
  ![Windows Server Setup](assets/1-windows-server-setup.png)
  ![Windows Server Installation](assets/2-windows-server-setup.png)
  ![Server Manager Dashboard](assets/3-windows-server-setup.png)

* **Network & Hostname Configuration:**
  ![Network Configuration](assets/4-network-config.png)
  ![Computer Name Assignment](assets/5-assigning-name.png)

</details>

<details>
<summary><b>Phase 2: Active Directory DS, OUs & UPN Suffixes (Images 06–20)</b></summary>
<br>

* **AD DS Installation & Domain Controller Promotion:**
  ![AD DS Installation](assets/6-active-directory-setup.png)
  ![Promote to Domain Controller](assets/7-active-directory-setup.png)
  ![Forest Configuration](assets/8-active-directory-setup.png)
  ![Deployment Options](assets/9-active-directory-setup.png)
  ![Installation Progress](assets/10-active-directory-setup.png)

* **Directory Structure & User Accounts:**
  ![ADUC Snap-in](assets/11-active-directory.png)
  ![Creating OUs](assets/12-active-directory.png)
  ![Corporate_Users OU](assets/13-active-directory.png)
  ![Creating Test Accounts](assets/14-active-directory.png)
  ![User Account Details](assets/15-active-directory.png)
  ![User Password Configuration](assets/16-active-directory.png)
  ![Populating Attributes](assets/17-active-directory.png)

* **Alternative UPN Suffix Mapping:**
  ![Domains and Trusts](assets/18-upn-suffix.png)
  ![Adding UPN Suffix](assets/19-upn-suffix.png)
  ![Applying UPN Suffix to User](assets/20-upn-suffix.png)

</details>

<details>
<summary><b>Phase 3: Entra Connect Sync Setup & Technical Troubleshooting (Images 21–35)</b></summary>
<br>

* **Installer Execution & Forest Connection:**
  ![Entra Connect Welcome](assets/21-entra-connect.png)
  ![Express Settings Options](assets/22-entra-connect.png)
  ![User Sign-in Method (PHS)](assets/23-entra-connect.png)
  ![Connecting to Entra ID](assets/24-entra-connect.png)
  ![Connecting Directories](assets/25-entra-connect.png)
  ![Service Account Creation](assets/26-entra-connect.png)
  ![Connected Forest Status](assets/27-entra-connect.png)
  ![UPN Sign-in Configuration](assets/28-entra-connect.png)
  ![Domain Verification Warning Override](assets/29-entra-connect.png)

* **Domain/OU Filtering & Configuration Execution:**
  ![Domain and OU Filtering](assets/30-entra-connect.png)
  ![Identifying Users](assets/31-entra-connect.png)
  ![Group Filtering Settings](assets/32-entra-connect.png)
  ![Optional Features](assets/33-entra-connect.png)
  ![Ready to Configure](assets/34-entra-connect.png)
  ![Configuration Complete](assets/35-entra-connect.png)

</details>

<details>
<summary><b>Phase 4: Cloud Roles, MFA & Sign-In Verification (Images 36–41)</b></summary>
<br>

* **Cloud RBAC Role Delegation:**
  ![Entra Roles and Administrators](assets/36-assigning-roles.png)
  ![Helpdesk Administrator Assignment](assets/37-assigning-roles.png)

* **Security Defaults & Multi-Factor Authentication:**
  ![Multi-Factor Authentication Policy Settings](assets/38-multi-factor-authentication.png)

* **End-to-End Cloud Authentication Verification:**
  ![InPrivate Cloud Login Prompt](assets/39-logging-in.png)
  ![Password Validation via PHS](assets/40-logging-in.png)
  ![Successful Authenticated Session](assets/41-logging-in.png)

</details>

---

