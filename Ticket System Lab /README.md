# IT Help Desk Ticketing System Homelab

## Overview

This project documents the creation of a fully functional IT Help Desk ticketing system homelab using Oracle VirtualBox, Windows Server 2022, Windows 11, Ubuntu Server, Docker, and Zammad.

The goal of this project was to simulate a real-world enterprise IT support environment while learning:
- Help Desk ticket workflows
- Incident management
- Active Directory troubleshooting
- User support processes
- Docker container deployment
- Linux server administration
- Enterprise IT documentation
- Customer communication workflows

This lab was integrated with a previously built Active Directory environment to simulate realistic enterprise IT support scenarios.

---

# Project Objectives

The goals of this project were to:

- Deploy a self hosted ticketing system
- Learn help desk ticket workflows
- Simulate enterprise IT support scenarios
- Integrate Active Directory support tasks
- Practice troubleshooting methodologies
- Learn Docker container management
- Understand Linux server administration
- Improve technical documentation skills
- Simulate customer and technician interactions

---

# Technologies Used

| Technology | Purpose |
|---|---|
| Oracle VirtualBox | Virtualization platform |
| Windows Server 2022 | Active Directory Domain Controller |
| Windows 11 | Domain joined client workstation |
| Ubuntu Server | Linux ticket system server |
| Docker | Container platform |
| Docker Compose | Container orchestration |
| Zammad | Help Desk ticketing system |
| Active Directory | Identity management |
| PowerShell | Windows administration |
| Linux CLI | Ubuntu administration |

---

# Lab Environment

```text
                 ┌──────────────────────┐
                 │ Windows Server 2022  │
                 │ Domain Controller    │
                 │ Active Directory     │
                 │ DNS Server           │
                 └──────────┬───────────┘
                            │
                    VirtualBox NAT Network
                           LabNet
                        10.0.2.0/24
                            │
        ┌───────────────────┴───────────────────┐
        │                                       │
┌───────┴────────┐                 ┌────────────┴─────────┐
│ Windows 11 VM  │                 │ Ubuntu Server        │
│ Domain Client  │                 │ Zammad Help Desk     │
│ End User Device│                 │ Docker Containers    │
└────────────────┘                 └──────────────────────┘
```

---

# What We Built

This project simulated a real enterprise IT support environment consisting of:

- A Windows Server 2022 Active Directory Domain Controller
- A Windows 11 end-user workstation
- An Ubuntu Server running Zammad ticketing system
- Multiple help desk support users
- Simulated customer ticket submissions
- Realistic IT support workflows

The environment allowed us to:
- Create and manage help desk tickets
- Simulate end user support requests
- Troubleshoot Active Directory account issues
- Practice customer communication
- Document troubleshooting steps
- Learn enterprise ticket lifecycle management

---

# Installation & Setup

## 1. Virtual Machine Setup

Three virtual machines were created using Oracle VirtualBox:

| VM | Purpose |
|---|---|
| Windows Server 2022 | Domain Controller |
| Windows 11 | Client workstation |
| Ubuntu Server | Ticket system server |

All VMs were connected using the same NAT network to allow communication between systems.

---

## 2. Ubuntu Server Preparation

Ubuntu Server was updated using:

```bash
sudo apt update && sudo apt upgrade -y
```

Docker and required dependencies were installed:

```bash
sudo apt install docker.io docker-compose-v2 git -y
```

Docker services were enabled:

```bash
sudo systemctl enable docker
sudo systemctl start docker
```

---

## 3. Installing Zammad

The Zammad Docker Compose repository was cloned:

```bash
git clone https://github.com/zammad/zammad-docker-compose.git
```

Moved into the project directory:

```bash
cd zammad-docker-compose
```

Started the Zammad containers:

```bash
sudo docker compose up -d
```

---

## 4. Docker Containers

The deployment automatically created multiple containers including:

- Zammad Web Server
- PostgreSQL Database
- Redis
- Elasticsearch
- Websocket Services
- Scheduler Services

Verified running containers using:

```bash
sudo docker ps
```

---

## 5. Accessing The Ticket System

The Ubuntu server IP was identified using:

```bash
hostname -I
```

The Zammad web interface was accessed from the Windows 11 client using:

```text
http://10.0.2.15:8080
```

---

# Ticket System Configuration

After installation:
- Help desk groups were created
- Customer users were created
- Technician/admin accounts were configured
- Ticket priorities were configured
- Example support tickets were created

Example ticket categories included:
- Password resets
- Account lockouts
- Printer issues
- VPN problems
- Software installation requests
- Network troubleshooting

---

# Active Directory Integration

This project was integrated with the previously built Active Directory lab.

Realistic support tasks included:
- Unlocking user accounts
- Resetting passwords
- Managing user permissions
- Supporting Windows login issues

Example workflow:
1. Customer creates a support ticket
2. Help desk technician reviews issue
3. Technician troubleshoots in Active Directory
4. Issue is documented inside ticket
5. Ticket is resolved and closed

---

# What We Learned

## Help Desk Ticket Workflow

Learned how enterprise ticket systems manage:
- Ticket creation
- Ticket assignment
- Prioritization
- Internal notes
- Public customer replies
- Ticket resolution
- Ticket closure

---

## Internal Notes vs Public Replies

One important concept learned was the difference between:
- Internal technician notes
- Public customer facing responses

This reflects how real enterprise ticket systems operate.

---

## Docker Container Management

Learned how to:
- Deploy applications using Docker
- Manage Docker containers
- Use Docker Compose
- Troubleshoot container startup issues
- Verify running services

---

## Linux Server Administration

Developed experience with:
- Ubuntu Server administration
- Package management
- Service management
- Linux networking
- CLI troubleshooting

---

## Active Directory Troubleshooting

Used Active Directory to:
- Reset passwords
- Unlock accounts
- Troubleshoot login issues
- Simulate enterprise user support

This reinforced understanding of:
- Identity management
- Authentication workflows
- Enterprise Windows support

---

## Enterprise IT Documentation

Learned the importance of:
- Writing ticket notes
- Documenting troubleshooting steps
- Maintaining accurate support records
- Communicating with end users professionally

---

# Skills Demonstrated

- IT Help Desk Support
- Ticket Lifecycle Management
- Active Directory Administration
- Windows Server Administration
- Linux Administration
- Docker & Containerization
- Customer Support Communication
- Troubleshooting Methodology
- Virtualization
- Enterprise Networking
- Technical Documentation

---

# Screenshots

Screenshots of the lab environment can be found inside the:

```text
/Screenshots
```

folder.

The screenshots demonstrate:
- Help desk dashboard monitoring
- Ticket queue management
- User and role administration
- Customer-to-technician communication
- Ticket lifecycle workflow
- Enterprise help desk structure
- Real-world support interaction simulation

---

# Future Improvements

Planned future improvements include:
- LDAP/Active Directory integration
- Email ticket creation
- SLA configuration
- Automated ticket routing
- Knowledge base articles
- Remote support tools
- Group Policy integration
- SIEM integration
- Monitoring and alerting

---

# Author

Built as part of a hands on IT Help Desk and system administration homelab focused on learning enterprise support workflows, Active Directory administration, Linux server management, and ticketing system operations.
