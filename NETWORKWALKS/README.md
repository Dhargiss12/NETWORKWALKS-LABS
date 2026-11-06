# 🔐 Cybersecurity Lab Environment Setup

### Building an isolated virtual lab for penetration testing and ethical hacking practice

<p align="left">
  <img src="https://img.shields.io/badge/VirtualBox-Hypervisor-183A61?style=for-the-badge&logo=virtualbox&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali_Linux-Security_OS-557C94?style=for-the-badge&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Linux-Operating_System-FCC624?style=for-the-badge&logo=linux&logoColor=black" />
  <img src="https://img.shields.io/badge/Networking-TCP%2FIP-0078D4?style=for-the-badge&logo=cisco&logoColor=white" />
  <img src="https://img.shields.io/badge/Windows-Host_OS-0078D6?style=for-the-badge&logo=windows&logoColor=white" />
</p>

---

## 📌 Project Overview

This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using Oracle VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be practiced safely.

The laboratory uses virtual networking to understand network communication and provides a foundation for adding additional virtual machines for future security-testing exercises.

---

## 🎯 Objectives

The main objectives of this project are to:

- Install and configure Oracle VirtualBox.
- Install and configure Kali Linux as a virtual machine.
- Understand NAT, NAT Network, and Host-Only networking.
- Configure virtual network adapters.
- Configure and verify IPv4 addressing.
- Test network connectivity and DNS resolution.
- Create a clean virtual machine snapshot for recovery.
- Document the complete laboratory setup.
- Prepare the environment for future cybersecurity exercises.

---

## 🛡️ Purpose of the Lab

The lab provides a controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network Reconnaissance
- Port Scanning
- Vulnerability Assessment
- Packet Analysis
- Web Security Testing
- Exploitation Practice
- Security Tool Experimentation

⚠️ **Important:** This laboratory must only be used for systems that I own or have explicit permission to test.

---

## 🏗️ Lab Architecture

The laboratory uses Oracle VirtualBox to run Kali Linux on a Windows host machine.

Additional virtual machines can be connected to the virtual network in future projects for attacker and target simulations.

---

## ⚙️ Lab Configuration

| Component | Configuration |
|---|---|
| Host OS | Windows 11 |
| Host RAM | 16 GB |
| Processor | Intel Core i5-1334U |
| Hypervisor | Oracle VirtualBox |
| Security OS | Kali Linux |
| Kali RAM | 4096 MB |
| Kali CPU | 2 CPUs |
| Virtual Network | NAT / Host-Only |
| IP Configuration | DHCP / Static IPv4 |

---

# 🪜 Lab Setup Procedure

## Step 1. Install 7-Zip

7-Zip is used to extract the Kali Linux virtual machine package when it is distributed in a compressed archive format.

**Tool:** 7-Zip

Download: https://www.7-zip.org/

---

## Step 2. Install Oracle VirtualBox

Oracle VirtualBox was installed as the hypervisor to create and manage virtual machines.

Download: https://www.virtualbox.org/wiki/Downloads

---

## Step 3. Configure the Virtual Network

VirtualBox provides different networking modes for connecting virtual machines.

| Network Mode | Description |
|---|---|
| NAT | Provides external network access to a virtual machine. |
| NAT Network | Allows connected VMs to communicate while providing external network access. |
| Host-Only | Enables private communication between the host and connected VMs. |
| Bridged Adapter | Connects a VM directly to the physical network. |

NAT and Host-Only networking are explored to understand internet connectivity and private communication between virtual machines.

A dedicated NAT Network can also be configured when multiple VMs need to communicate with each other.

---

## Step 4. Install Kali Linux

Kali Linux is downloaded from the official website and configured as a virtual machine in Oracle VirtualBox.

**Virtual Machine Configuration:**

- RAM: 4096 MB
- Processor: 2 CPUs
- Network Adapter: NAT
- Operating System: Kali Linux

Download: https://www.kali.org/get-kali/

---

## Step 5. Configure Kali Linux Network

The Kali Linux network interface is inspected to verify its IP address and network configuration.

**Check IP Address:**

```bash
ip addr
```

**Check Network Interfaces:**

```bash
ip link
```

**Check Routing Table:**

```bash
ip route
```

**Check DNS Configuration:**

```bash
cat /etc/resolv.conf
```

If a static IPv4 address is required, the IP address, subnet mask, default gateway, and DNS settings must match the selected virtual network configuration.

---

## Step 6. Verify Network Connectivity

Network connectivity is tested using standard Linux networking commands.

**Test Gateway Connectivity:**

```bash
ping -c 4 <GATEWAY_IP>
```

**Test Internet Connectivity:**

```bash
ping -c 4 8.8.8.8
```

**Test DNS Resolution:**

```bash
nslookup google.com
```

These tests help verify IP connectivity, routing, and DNS resolution.

---

## Step 7. Create a Clean VM Snapshot

After completing the initial Kali Linux configuration, a VirtualBox snapshot can be created.

**Example Snapshot Name:**

```text
Kali-Linux-Initial-Setup
```

The snapshot provides a clean recovery point before performing further experiments.

If a future configuration change causes problems, the virtual machine can be restored to its previous state.

---

# 🔎 Lab Verification

| Test | Command | Expected Result |
|---|---|---|
| Check IP Address | `ip addr` | Assigned IP displayed |
| Check Network Interface | `ip link` | Interface status displayed |
| Check Routing | `ip route` | Routing information displayed |
| Test Gateway | `ping -c 4 <GATEWAY_IP>` | Successful replies |
| Test Internet | `ping -c 4 8.8.8.8` | Successful replies |
| Test DNS | `nslookup google.com` | Domain resolves |
| Verify Nmap | `nmap --version` | Nmap version displayed |

---

# 🐞 Problems Encountered & Solutions

## Problem 1. Kali Linux Network Connectivity

**Issue:** Network connectivity was unavailable after changing VirtualBox network adapter settings.

**Troubleshooting:**

1. Checked the VirtualBox network adapter configuration.
2. Verified the virtual network cable connection.
3. Inspected network interfaces using `ip link`.
4. Checked IP address and routing information.
5. Restarted the network connection when required.

**Verification:** Repeated connectivity tests after correcting the configuration.

## Problem 2. Kali Linux Startup Issue

**Issue:** The graphical desktop did not load correctly during virtual machine startup.

**Troubleshooting:**

1. Checked virtual machine resource allocation.
2. Reviewed VirtualBox configuration.
3. Performed a complete power-off and restart.
4. Verified the virtual machine startup again.

**Result:** The graphical desktop loaded successfully after restarting the virtual machine.

---

# 💡 What I Learned

Through this project, I gained practical experience in configuring a virtual environment for cybersecurity practice.

The important concepts explored include:

### 1. NAT vs NAT Network

Understood the difference between NAT and NAT Network and how they affect internet connectivity and communication between virtual machines.

### 2. Virtual Machine Networking

Learned how VirtualBox network adapters connect virtual machines to different network configurations.

### 3. IPv4 Configuration

Explored IP addresses, subnet masks, default gateways, and DNS settings.

### 4. Linux Networking Commands

Practiced using `ip addr`, `ip link`, `ip route`, `ping`, and `nslookup` to inspect and troubleshoot network connectivity.

### 5. VM Snapshots

Understood how snapshots provide recovery points before performing configuration changes and security experiments.

### 6. Technical Troubleshooting

Gained experience identifying configuration issues, investigating possible causes, and verifying solutions.

---

# 🔐 Security & Ethical Use

This laboratory is intended strictly for educational purposes and authorized cybersecurity testing.

All scanning, reconnaissance, vulnerability assessment, and testing activities must be restricted to systems owned by me or systems for which explicit permission has been granted.

---

# 🔗 Tools & Resources

- [7-Zip](https://www.7-zip.org/)
- [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Kali Linux](https://www.kali.org/get-kali/)
- [Nmap](https://nmap.org/)
- [Wireshark](https://www.wireshark.org/)

---

# 👤 Author

**Dhargiss V**

B.Tech Computer Science and Engineering – Cyber Security

- GitHub: [Dhargiss12](https://github.com/Dhargiss12)
- LinkedIn: [Connect with me](https://www.linkedin.com/)

---

## 📌 Project Information

| Field | Details |
|---|---|
| Project Name | Cybersecurity Lab Environment Setup |
| Category | Cybersecurity / Virtualization |
| Hypervisor | Oracle VirtualBox |
| Operating System | Kali Linux |
| Focus | Virtual Lab Setup and Network Configuration |
| Status | Ongoing |

---

*This repository documents my hands-on experience in building and configuring a virtual cybersecurity laboratory. It will be updated with verified configurations, screenshots, troubleshooting notes, and technical findings as the project progresses.*
