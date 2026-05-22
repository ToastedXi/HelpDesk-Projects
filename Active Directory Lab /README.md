# Active Directory Home Lab

## Overview

This project documents the creation of a fully functional Active Directory home lab environment using Oracle VirtualBox, Windows Server 2022, and Windows 11.

The goal of this project was to build and understand a realistic enterprise Windows environment while learning:
- Active Directory Domain Services (AD DS)
- DNS configuration
- Domain Controllers
- Organizational Units (OUs)
- User and Group Management
- Security Groups
- PowerShell administration
- Enterprise Windows networking
- Active Directory troubleshooting

---

# What We Made

This lab simulates a small enterprise Active Directory environment with centralized authentication and identity management.

The environment includes:
- A Windows Server 2022 Domain Controller
- A Windows 11 domain-joined client
- Active Directory Domain Services (AD DS)
- DNS Server configuration
- Organizational Units (OUs)
- Domain users
- Security groups
- Group-based access management

We successfully:
- Installed and configured Active Directory
- Promoted a Windows Server to a Domain Controller
- Created the `lab.local` domain
- Joined a Windows 11 machine to the domain
- Created Organizational Units (OUs)
- Created users and security groups
- Managed permissions using groups
- Used PowerShell for administration
- Troubleshot DNS and networking issues

---

# Objectives

The goals of this project were to:

- Build a functional Active Directory environment
- Learn how enterprise identity management works
- Understand how DNS supports Active Directory
- Configure a Domain Controller
- Create Organizational Units (OUs)
- Create and manage domain users
- Create and manage security groups
- Join a Windows 11 client to the domain
- Learn PowerShell administration
- Troubleshoot networking and DNS issues

---

# Technologies Used

| Technology | Purpose |
|---|---|
| Oracle VirtualBox | Virtualization platform |
| Windows Server 2022 | Domain Controller |
| Windows 11 | Domain-joined client |
| Active Directory Domain Services | Identity management |
| DNS Server | Domain name resolution |
| PowerShell | AD administration |
| NAT Network | VM communication |

---

# Lab Diagram

```text
                 ┌──────────────────────┐
                 │    DC01.lab.local    │
                 │ Windows Server 2022  │
                 │ Domain Controller    │
                 │ DNS Server           │
                 │ IP: 10.0.2.10        │
                 └──────────┬───────────┘
                            │
                    VirtualBox NAT Network
                           LabNet
                        10.0.2.0/24
                            │
                 ┌──────────┴───────────┐
                 │   WIN11-CLIENT       │
                 │   Windows 11         │
                 │ Domain Joined Client │
                 │ IP: 10.0.2.x         │
                 └──────────────────────┘
```

---

# How The Environment Was Built

## 1. VirtualBox Networking

A VirtualBox NAT Network called:

```text
LabNet
```

was created to allow communication between the virtual machines.

Both VMs were connected to:
- Adapter 1 → NAT Network → LabNet

---

## 2. Windows Server 2022 Setup

The Windows Server 2022 VM was configured as the Domain Controller.

### Configuration

| Setting | Value |
|---|---|
| Hostname | DC01 |
| Domain | lab.local |
| IP Address | 10.0.2.10 |
| DNS | 127.0.0.1 |

A static IP was configured because Domain Controllers should not use DHCP.

---

## 3. Installing Active Directory Domain Services

Installed:
- Active Directory Domain Services
- DNS Server

PowerShell command used:

```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```

---

## 4. Promoting The Server To A Domain Controller

The server was promoted to a Domain Controller using:

```powershell
Install-ADDSForest -DomainName "lab.local"
```

This created:
- The lab.local domain
- DNS zones
- Active Directory database
- Kerberos infrastructure

---

## 5. Configuring Windows 11

The Windows 11 VM was configured to use the Domain Controller as its DNS server.

DNS Configuration:

```text
10.0.2.10
```

The Windows 11 client was then joined to the domain:

```text
lab.local
```

using:

```text
LAB\Administrator
```

---

# What We Learned

## Active Directory Fundamentals

Learned how Active Directory centralizes:
- Authentication
- Authorization
- Identity management
- User and device management

Developed an understanding of how enterprise Windows environments authenticate users and manage permissions.

---

## DNS Dependency In Active Directory

One of the biggest lessons learned was how heavily Active Directory depends on DNS.

Learned:
- Why clients must use the Domain Controller as DNS
- How SRV records work
- How DNS supports Kerberos and LDAP
- Why incorrect DNS breaks domain joins

This lab reinforced the importance of proper DNS configuration in enterprise environments.

---

## Organizational Units (OUs)

Learned how OUs are used to:
- Organize users and computers
- Separate departments logically
- Apply Group Policy
- Delegate administration

Built a realistic enterprise OU structure.

---

## User & Group Management

Learned how enterprise environments manage:
- Users
- Security groups
- Access control
- Permissions

Understood the importance of:
- Role-based access control (RBAC)
- Group-based permissions
- Least privilege

---

## Authentication vs Authorization

Learned the difference between:

| Concept | Meaning |
|---|---|
| Authentication | Verifying identity |
| Authorization | Determining access |

Understood how Active Directory handles both authentication and authorization.

---

## PowerShell Administration

Used PowerShell extensively to:
- Create users
- Create groups
- Create OUs
- Enumerate Active Directory objects
- Troubleshoot networking
- Manage AD infrastructure

Developed familiarity with enterprise administration through scripting and automation.

---

## Networking & Troubleshooting

This project involved troubleshooting several real-world issues including:
- Multiple VirtualBox adapters
- Incorrect DNS configuration
- Disabled network adapters
- DNS communication failures
- Domain join failures
- AD DNS registration issues

Learned how to diagnose and resolve:
- DNS problems
- Network adapter issues
- Active Directory communication failures
- VirtualBox networking issues

---

# Skills Demonstrated

- Windows Server Administration
- Active Directory Administration
- DNS Configuration
- PowerShell Scripting
- Virtualization
- Network Troubleshooting
- Identity & Access Management (IAM)
- Enterprise Windows Infrastructure
- Active Directory Troubleshooting

---

# Future Improvements

Planned future additions:
- Group Policy Objects (GPOs)
- Shared folders & NTFS permissions
- File Server
- Sysmon deployment
- SIEM integration
- BloodHound
- Kali Linux attacker VM
- Active Directory security auditing
- PowerShell automation scripts

---

# Author

Built as part of a cybersecurity and system administration home lab project focused on learning enterprise Active Directory environments and Windows infrastructure administration.
