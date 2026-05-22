# Active Directory Home Lab

## Overview

This project documents the creation of a fully functional Active Directory home lab environment using Oracle VirtualBox, Windows Server 2022, and Windows 11.

The purpose of this lab was to learn:
- Active Directory Domain Services (AD DS)
- DNS configuration
- Domain Controllers
- Organizational Units (OUs)
- User and Group Management
- Security Groups
- Domain Joining
- Enterprise Windows networking
- PowerShell administration
- Active Directory troubleshooting

This lab simulates a small enterprise Windows environment.

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

# Lab Architecture

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
