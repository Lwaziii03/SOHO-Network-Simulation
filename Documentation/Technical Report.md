# Technical Report: SOHO Network Design and Simulation

## Project Overview

This project demonstrates the design, configuration, and simulation of a **Small Office/Home Office (SOHO)** network using **Virtual Machines (Windows and Linux)** and **Windows Firewall**. The goal was to build a secure, scalable, and cost-effective environment for a small business — supporting staff and guest connectivity, centralized storage, automated backups, and network segmentation.

## 1. Network Design & Planning

The network was designed to support 5–7 users, including both **staff and guest connections**, within a budget of **R70,000**.

### Key components:

- **UniFi Dream Router:** Primary router with VLAN and guest support, built-in firewall, and intrusion prevention.
- **Synology DS224+ NAS:** Centralized file and backup server with snapshot and encryption support.
- **IronWolf 8TB Drives (x2):** Configured in RAID1 for redundancy.
- **Brother HL-L8360CDW Printer:** Network printer supporting secure print release and role-based access.

### Network topology:

- **Staff PCs:** Connected to _StaffNet_ VLAN simulation.
- **Guest PC:** Connected to _GuestNet_, isolated from internal resources but with internet access.
- **File Server:** Centralized data and backup node connected to _StaffNet_.

The network design was implemented and visualized using **Draw.io**, with additional simulation and testing conducted in **VirtualBox**.

## 2. Virtualization Implementation

**Virtual Machines:**

- **Staff-PC1:** Windows 10 (host)
- **Staff-PC2:** Linux (VM)
- **Guest-PC:** Windows VM (isolated network)
- **File/Backup Server:** Windows Server VM

**Virtual Network Configuration:**

- Staff PCs and File Server share an internal network "StaffNet."
- Guest PC assigned to a separate "GuestNet" with NAT internet access.
- VLAN-like segmentation achieved through Windows Firewall rules and internal network isolation.

**Virtualization Benefits:**

- Snapshots and cloning used for fast rollback and replication.
- Sandbox environment for testing configurations without impacting the host OS.
- Safe experimentation with firewall policies and malware defense.
- Enhanced flexibility and disaster recovery options.

## 3. Firewall & Security Configuration

**Key firewall rules:**

- Blocked all inbound traffic from _GuestNet_ to _StaffNet_ and the File Server.
- Restricted FTP (Port 21) and other insecure services.
- Allowed only essential services like SMB for internal file sharing.

**Testing Results:**

- Staff PCs successfully accessed shared resources (\\FILESERVER).
- Guest PC was unable to ping or access the File Server, confirming isolation.
- Internet connectivity confirmed for all systems via NAT adapter.

## 4. Backup and File Management

A scheduled backup was configured on the File Server using Windows Backup:

- **Time:** 23:00 daily
- **Retention:** 30 days
- **Storage:** RAID1 NAS system
- **Redundancy:** Mirrored drives ensure data remains available if one fails.

This approach ensures reliable data protection while minimizing production downtime.

## 5. Network Testing & Verification

- **Ping Tests:** Verified full connectivity within StaffNet and isolation from GuestNet.
- **File Sharing Tests:** Confirmed access between staff PCs and File Server.
- **Firewall Testing:** Validated blocked communication from Guest PC to internal network.
- **Printer Access:** Verified shared printer availability from File Server.

## 6. Tools & Technologies

- Draw.io
- Oracle VirtualBox
- Windows 10 / Windows Server / Linux Ubuntu
- Windows Firewall
- Synology NAS Management Console
- Google Sheets (hardware budgeting)
