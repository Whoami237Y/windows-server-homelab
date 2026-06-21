# windows-server-homelab
Home lab: Installed Windows Server 2022 and configured Active Directory Domain Services (AD DS) from scratch — built to develop hands-on IT support and sysadmin fundamentals.

# Windows Server 2022 — Active Directory Home Lab

A hands-on home lab built to practice Windows Server administration and Active Directory setup from scratch — skills directly applicable to IT support and systems administration roles.

---

## Lab Overview

| Component | Details |
|---|---|
| **OS** | Windows Server 2022 (64-bit, ISO from Microsoft) |
| **Hostname** | DC01 |
| **Role** | Domain Controller (Primary) |
| **Domain** | lab.local |
| **IP Address** | 192.168.1.10 (Static) |
| **Subnet Mask** | 255.255.255.0 |
| **Default Gateway** | 192.168.1.1 |
| **DNS Server** | 127.0.0.1 (self-hosted) |
| **PDC Emulator** | DC01.lab.local |

---

## What This Lab Covers

- Downloading and mounting a Windows Server 2022 ISO from official Microsoft sources
- Installing Windows Server 2022 in a virtualized environment
- Configuring a static IP address and DNS settings manually via Network Connections
- Renaming the machine and setting up the server as a Domain Controller (`DC01`)
- Installing and configuring **Active Directory Domain Services (AD DS)**
- Promoting the server to a Domain Controller for the `lab.local` domain
- Verifying the AD setup using PowerShell (`Get-ADDomain`, `hostname`)

---

## Environment Setup

### Step 1 — Download Windows Server 2022 ISO
- Source: [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2022)
- Selected: English (United States) — 64-bit ISO
![image alt](https://github.com/Whoami237Y/windows-server-homelab/blob/96a55834e7465ee431528f87f2c2596e6d165352/screenshots/1.jpg)
![image alt](https://github.com/Whoami237Y/windows-server-homelab/blob/ad8d215bf5c87fa9753e68e4d11175ebf6f51b53/screenshots/2.jpg)

### Step 2 — Install & Configure the VM
- Installed Windows Server 2022 in a virtualized environment
- Set machine hostname to `DC01` via System Settings
- Verified hostname via PowerShell:
```powershell
hostname
# Output: DC01
```
![image alt](https://github.com/Whoami237Y/windows-server-homelab/blob/ad8d215bf5c87fa9753e68e4d11175ebf6f51b53/screenshots/2.1.jpg)
![image alt](https://github.com/Whoami237Y/windows-server-homelab/blob/96a55834e7465ee431528f87f2c2596e6d165352/screenshots/3.jpg)

### Step 3 — Configure Static IP & DNS
Configured manually via **Control Panel → Network Connections → IPv4 Properties:**
```
IP Address:       192.168.1.10
Subnet Mask:      255.255.255.0
Default Gateway:  192.168.1.1
Preferred DNS:    127.0.0.1  (pointing to itself as DNS server)
```
![image alt](https://github.com/Whoami237Y/windows-server-homelab/blob/96a55834e7465ee431528f87f2c2596e6d165352/screenshots/004.jpg)

### Step 4 — Install Active Directory Domain Services
- Installed AD DS role via Server Manager
- Promoted server to Domain Controller
- Created new forest with root domain: `lab.local`
![image alt](https://github.com/Whoami237Y/windows-server-homelab/blob/e6f62a51aafa018f0262ef471c19be5460fc2bb4/screenshots/4.1.jpg)

### Step 5 — Verify Active Directory
Confirmed successful AD setup via PowerShell:
```powershell
Get-ADDomain
```
Key output confirmed:
```
Name              : lab
DNSRoot           : lab.local
DomainMode        : Windows2016Domain
PDCEmulator       : DC01.lab.local
Forest            : lab.local
```
![image alt](https://github.com/Whoami237Y/windows-server-homelab/blob/96a55834e7465ee431528f87f2c2596e6d165352/screenshots/005.jpg)

---

## Skills Demonstrated

- Windows Server 2022 installation and initial configuration
- Manual network configuration (static IP, DNS, gateway)
- Active Directory Domain Services (AD DS) setup and promotion
- PowerShell for system verification and AD management
- Understanding of Domain Controller roles and DNS self-hosting

---

## Planned Next Steps

- [ ] Join a Windows 11 client machine to `lab.local` domain
- [ ] Create and manage users/groups via Active Directory Users and Computers
- [ ] Configure Group Policy Objects (GPO)
- [ ] Set up a second VM as a workstation endpoint

---

## Tools Used

- Windows Server 2022 (Microsoft Evaluation ISO)
- Windows PowerShell (Administrator)
- Network Connections / IPv4 Properties
- Server Manager — AD DS Role Installation

---

> **Purpose:** This lab was built independently to develop hands-on IT support and Windows administration skills outside of a formal work environment.
