# Active Directory – User Management, Group Policy & Testing

This phase focuses on **user administration, permission management, Group Policy configuration, and security testing** within a Windows Server 2019 Active Directory environment. The goal is to simulate real-world enterprise identity management and administrative workflows.

---

## Video Demonstration
*(Optional – add later if recorded)*  
YouTube: **Active Directory Tutorial (Phase 3/3) – User Management & GPOs**

---

## Environments and Technologies Used

- VirtualBox
- pfSense Firewall
- Active Directory Domain Services (AD DS)
- Group Policy Management
- DNS & DHCP
- PowerShell

---

## Operating Systems Used

- Windows Server 2019  
- pfSense

---

## OVERVIEW

1. Create and manage domain users.
2. Assign administrative and standard permissions.
3. Configure Group Policy Objects (GPOs).
4. Enable remote administration services.
5. Prepare a vulnerable Active Directory environment for testing.
6. Validate access and policy enforcement.

---

## 1. Domain User Creation

Create users in **Active Directory Users and Computers** to simulate real enterprise roles.

- **MaraCyber** – Domain Administrator
- **KarmaCyber** – Standard / Exploitable User
- **KLCyber** – Standard User

Configure password policies:
- Disable password expiration (lab use only).
- Disable forced password change at next login.

---

## 2. Group Membership and Permissions

- Add **MaraCyber** to the **Domain Admins** group.
- Leave **KarmaCyber** and **KLCyber** as standard domain users.
- Verify permissions by logging in as each user.

---

## 3. Group Policy Object (GPO) Configuration

Create and configure Group Policy Objects using **Group Policy Management**.

### Disable Security Protections (Lab Use Only)
- Disable Windows Defender Antivirus.
- Disable real-time protection.
- Disable Windows Defender Firewall (Domain Profile).

### Enable Remote Administration
- Enable **Remote Desktop Protocol (RDP)**.
- Enable **Windows Remote Management (WinRM)**.
- Enable **Remote Procedure Call (RPC)**.
- Configure registry setting:
  - `LocalAccountFilterPolicy = 1`

---

## 4. Enable Remote Services

Ensure administrative access for management and testing.

- Configure WinRM service startup.
- Allow basic authentication for WinRM.
- Apply policies using:
  ```powershell
  gpupdate /force
