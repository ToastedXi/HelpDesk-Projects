# Enterprise IAM Security Lab

## Overview

This project documents the creation of a fully functional Enterprise Identity and Access Management homelab using:

- Windows Server 2022
- Windows 11
- Ubuntu Server
- Kali Linux
- Active Directory
- Keycloak
- Docker
- Wazuh
- Zammad

The goal of this project was to simulate a realistic enterprise IAM environment while developing hands on experience with:

- Identity and Access Management
- Active Directory administration
- Role Based Access Control
- LDAP authentication
- Single Sign On
- Multi Factor Authentication
- SIEM monitoring
- Detection engineering
- Identity lifecycle management
- Enterprise troubleshooting
- Security operations workflows

This lab combines identity infrastructure, security monitoring, automation, and attack simulation into one enterprise style environment.

---

# Project Objectives

The goals of this project were to:

- Build a centralized identity management environment
- Configure Active Directory authentication
- Implement Role Based Access Control using security groups
- Deploy Keycloak for Single Sign On and Multi Factor Authentication
- Integrate LDAP authentication with Active Directory
- Simulate enterprise IAM workflows
- Create identity lifecycle automation scripts
- Detect IAM related attacks using a SIEM
- Practice enterprise troubleshooting methodologies
- Improve technical documentation skills

---

# Technologies Used

| Technology | Purpose |
|---|---|
| Oracle VirtualBox | Virtualization platform |
| Windows Server 2022 | Active Directory Domain Controller |
| Windows 11 | Domain joined workstation |
| Ubuntu Server | IAM and SIEM services |
| Kali Linux | Attack simulation |
| Active Directory | Central identity provider |
| Keycloak | IAM platform |
| LDAP | Directory authentication |
| Kerberos | Authentication protocol |
| Docker | Container platform |
| Docker Compose | Container orchestration |
| Zammad | Ticketing system |
| Wazuh | SIEM platform |
| Sysmon | Endpoint telemetry |
| PowerShell | IAM automation |
| BloodHound | Active Directory analysis |
| Mimikatz | Credential attack simulation |

---

# Lab Environment

```text
                               Windows Server 2022
                               Domain Controller
                               Active Directory
                               DNS LDAP Kerberos
                                          |
                                   Virtual Network
                                      LabNet
                                   10.0.2.0/24
                                          |
         ----------------------------------------------------------------
         |                              |                               |
         |                              |                               |
   Windows 11 VM                 Ubuntu Server                    Kali Linux
   Domain Client                 Keycloak Wazuh                  Attack Simulation
   End User Device               Ticketing System                Red Team Testing
```

---

# What We Built

This project simulated a real enterprise IAM environment consisting of:

- A Windows Server 2022 Active Directory Domain Controller
- A Windows 11 domain joined workstation
- An Ubuntu Server hosting:
  - Keycloak
  - Wazuh
  - Zammad
- A Kali Linux attacker workstation
- IAM security monitoring and detections
- Role based access control workflows
- MFA enforcement
- LDAP federation
- Attack simulation and detection

The environment allowed us to:

- Centralize authentication using Active Directory
- Implement Role Based Access Control using security groups
- Configure Single Sign On using Keycloak
- Enforce Multi Factor Authentication policies
- Simulate identity lifecycle management
- Monitor IAM related security events
- Detect attack activity inside the SIEM
- Practice enterprise access management workflows
- Simulate real world SOC and IAM operations

---

# Active Directory Configuration

## Organizational Unit Structure

```text
BrodieLab.local

Users
    HR
    IT
    Finance
    SOC

Groups

Workstations

Servers

Disabled Users
```

---

## Security Groups

The following Role Based Access Control groups were created:

```text
GG_HR_Users
GG_IT_Support
GG_Finance_Users
GG_SOC_Analysts
GG_Keycloak_Admins
GG_SIEM_Users
GG_Ticket_Users
```

---

## Example Users

```text
alice.hr
bob.finance
charlie.it
dana.soc
admin.iam
```

---

# Role Based Access Control

Role Based Access Control was implemented using Active Directory security groups and NTFS permissions.

## Example Shared Folders

| Folder | Access Group |
|---|---|
| HR Share | GG_HR_Users |
| Finance Share | GG_Finance_Users |
| SOC Share | GG_SOC_Analysts |
| IT Share | GG_IT_Support |

This simulated enterprise least privilege access control.

---

# Identity Lifecycle Management

PowerShell automation scripts were created to simulate:

- Joiner workflows
- Mover workflows
- Leaver workflows

---

## Joiner Workflow

Automatically:
- Creates user accounts
- Assigns departments
- Adds Role Based Access Control permissions
- Enables accounts

Example:

```powershell
New ADUser -Name "Test User"

Add ADGroupMember -Identity "GG_HR_Users"
```

---

## Mover Workflow

Automatically:
- Removes old access
- Assigns new department permissions
- Updates group memberships

---

## Leaver Workflow

Automatically:
- Disables user accounts
- Removes privileged access
- Moves accounts into Disabled Users

Example:

```powershell
Disable ADAccount -Identity "test.user"
```

---

# Keycloak IAM Deployment

Keycloak was deployed using Docker on Ubuntu Server.

## Keycloak Features Configured

- LDAP federation
- Single Sign On
- Multi Factor Authentication
- Role mappings
- Realm management

---

# LDAP Federation

Keycloak was integrated with Active Directory using LDAP.

## Authentication Flow

```text
User Login

Keycloak

LDAP Authentication

Active Directory

Authentication Success
```

This allowed Active Directory users to authenticate centrally through Keycloak.

---

# Multi Factor Authentication

Multi Factor Authentication was enforced for privileged accounts using TOTP authentication.

Users were required to:
- Register authenticator applications
- Configure OTP tokens
- Verify second factor authentication during login

This simulated enterprise privileged account protection.

---

# Single Sign On

Single Sign On was configured using OpenID Connect.

Users authenticated once through Keycloak and gained access to:
- Ticketing platform
- SIEM dashboards
- IAM services

This simulated centralized enterprise authentication.

---

# SIEM Integration

Wazuh SIEM was used to monitor:

- Windows authentication logs
- Sysmon telemetry
- Active Directory events
- Privileged access changes
- Failed authentication attempts

---

# Windows Event Monitoring

Important Windows Security Event IDs monitored:

| Event ID | Description |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4720 | User account created |
| 4722 | User account enabled |
| 4725 | User account disabled |
| 4728 | User added to privileged group |
| 4740 | Account lockout |
| 4768 | Kerberos TGT request |
| 4769 | Kerberos service ticket request |

---

# IAM Detection Engineering

Custom SIEM detections were created for:

- Password spraying
- Account lockouts
- Privileged group modifications
- Failed login spikes
- Suspicious Kerberos ticket activity
- Unauthorized administrative actions

---

# Attack Simulation

Kali Linux was used to safely simulate IAM related attack scenarios inside the isolated lab environment.

## Simulated Attacks

| Attack | Purpose |
|---|---|
| Password Spraying | Authentication attack simulation |
| LDAP Enumeration | Directory reconnaissance |
| BloodHound Collection | Active Directory analysis |
| Kerberoasting Simulation | Kerberos attack detection |
| Failed Login Testing | SIEM alert validation |

---

# Attack Detection Workflow

This project focused heavily on the full security workflow:

```text
Attack Simulation

SIEM Detection

Security Alert

Ticket Creation

Investigation and Response
```

This simulated real SOC and IAM operations.

---

# Ticketing System Integration

Zammad was integrated to simulate enterprise IT support and IAM workflows.

## Example IAM Tickets

### New User Provisioning

- Create HR user
- Assign Role Based Access Control permissions
- Enable Multi Factor Authentication

### Access Requests

- Request Finance folder access
- Manager approval simulation
- Group assignment

### Account Lockouts

- User unable to login
- Active Directory investigation
- Account unlock workflow

### Offboarding

- Disable account
- Remove access
- Archive identity

---

# Docker and Containerization

The Ubuntu server hosted multiple Docker containers including:

- Keycloak
- PostgreSQL
- Redis
- Elasticsearch
- Wazuh services
- Zammad services

This project reinforced:
- Docker deployment
- Container orchestration
- Service troubleshooting
- Linux server administration

---

# Skills Demonstrated

- Identity and Access Management
- Active Directory Administration
- LDAP Authentication
- Kerberos Authentication
- Role Based Access Control
- Single Sign On
- Multi Factor Authentication
- SIEM Engineering
- Detection Engineering
- Windows Server Administration
- Linux Administration
- Docker and Containerization
- Help Desk Operations
- PowerShell Automation
- Enterprise Troubleshooting
- Technical Documentation
- SOC Operations
- Enterprise Networking

---

# Screenshots

Screenshots of the lab environment can be found inside the:

```text
Screenshots
```

folder.

The screenshots demonstrate:

- Active Directory configuration
- Keycloak authentication portal
- Multi Factor Authentication enrollment
- SIEM dashboards
- IAM alerting
- Role Based Access Control permissions
- Ticketing workflows
- Attack detection
- Windows authentication events
- Enterprise identity workflows

---

# Future Improvements

Planned future improvements include:

- Conditional access policies
- Azure AD integration
- Privileged Access Management
- Password self service portal
- SCIM provisioning
- Group Policy hardening
- Remote support integration
- Automated incident response
- Email based ticket creation
- Threat intelligence integration
- Advanced detection engineering
- Cloud identity federation

---

# Key Concepts Learned

## Identity and Access Management

Learned how enterprise IAM systems manage:
- Authentication
- Authorization
- User provisioning
- Access control
- Identity federation
- Multi Factor Authentication enforcement

---

## Security Monitoring

Developed experience monitoring:
- Authentication events
- Privilege escalation attempts
- Suspicious login activity
- Kerberos authentication workflows
- Active Directory group changes

---

## Enterprise IAM Workflows

Simulated:
- Joiner workflows
- Mover workflows
- Leaver workflows
- Help desk access requests
- Security alert investigation
- Identity lifecycle management

---

# MITRE ATTACK Mapping

| Technique | MITRE ID |
|---|---|
| Password Spraying | T1110.003 |
| Kerberoasting | T1558.003 |
| Account Discovery | T1087 |
| Privilege Escalation | T1068 |
| Valid Accounts | T1078 |

---

# Conclusion

This project combined identity management, security monitoring, automation, and attack simulation into a fully integrated enterprise IAM homelab.

The lab provided hands on experience with:
- Active Directory administration
- IAM engineering
- Authentication technologies
- SIEM monitoring
- Detection engineering
- Enterprise security workflows
- Help desk operations
- Red team and blue team concepts

This project significantly improved practical understanding of enterprise identity security and modern IAM operations.

---

# Author

Built as part of a hands on cybersecurity and identity management homelab focused on enterprise IAM engineering, Active Directory administration, SIEM monitoring, authentication security, and security operations workflows.
