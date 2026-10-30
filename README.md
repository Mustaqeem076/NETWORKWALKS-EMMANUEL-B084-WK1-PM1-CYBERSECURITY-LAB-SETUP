<div align="center">

# Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Mustaqeem-B084-C00000?style=flat-square" />
</p>

---

## Project Overview

This project focuses on setting up a **virtual cybersecurity and penetration-testing laboratory** using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

---

## Objectives

The main objectives of this project are to:

- Install and configure VirtualBox.
- Install/import Kali Linux as a virtual machine.
- Create a private **NAT Network** for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent IP address to the Kali VM.
- Verify network connectivity and DNS resolution.
- Take a clean VM snapshot for recovery.
- Document the complete setup process.
- Prepare the environment for future cybersecurity projects.

---

## Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It will be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

**Important:** This laboratory will only be used for systems that I own or have explicit permission to test. I will not use the lab or its tools to attack unauthorized systems.

---

## Lab Architecture

![](06_kali_desktop.png)

Additional target machines will be added to the same virtual network in future projects.

---

## Lab Configuration

| Component         | Configuration     |
| ----------------- | ----------------- |
| Host Machine      | Dell Latitude E7270 |
| Host OS           | Windows 10 Pro    |
| Host RAM          | 8 GB              |
| Processor         | Intel Core i5     |
| Hypervisor        | VirtualBox        |
| Security OS       | Kali Linux 2026.3 |
| Kali RAM          | 2048 MB           |
| Virtual Network   | NAT Network       |
| Network Address   | 10.0.0.0/24       |
| Kali IP Address   | 10.0.0.2/24       |
| Default Gateway   | 10.0.0.1          |
| DNS Server        | 8.8.8.8           |
| Future VM Range   | 10.0.0.3–10.0.0.99|

---

# Lab Setup Procedure

## Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip

![](01_install_7zip.png)

---

## Step 2. Install VirtualBox

VirtualBox was installed as the hypervisor.

![](02_install-virtual-box.png)

---

## Step 3. Create the NAT Network

A dedicated NAT Network was created in VirtualBox.

Configuration:
- Network Name: `NatNetwork`
- IPv4 Prefix: `10.0.0.0/24`
- DHCP: Enabled
- IPv6: Disabled

![](03_create_the_NAT_network.png)

A **NAT Network** was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

---

## Step 4. Import Kali Linux

The Kali Linux virtual machine was imported into VirtualBox.

![](04_add_kali_vm.png)

The VM network adapter was configured as follows:

```text
Adapter 1
Attached to: NAT Network
Network: NatNetwork

```
The VM was booted to the desktop screen

![](06_kali_desktop.png)

A shared folder was also configured for transferring required files between the host operating system and the Kali VM.
---

## Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```text
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

![](08_kali_OS_network_settings.png)

The network configuration was confirmed via the Terminal.
![](09_kali_network_test_1.png)
Network connectivity proved dysfunctional after ping test and browser test, so I applied the configuration to ignore duplicate addresses.

![](10_network_disfunction.png)
![](11_successful_browser_test.png)

## Step 7. Configure 'Drag-and-Drop' and 'Shared Clipboard' Features

In order to enable the transfer of files between the host machine and the virtual machine, as well as enabling a shared clipboard for easy copying and pasting across machines, the features need to be enabled in the VirtuaBox KaliVM settings, and VBox Guest Additions should be installed.

I enabled the 'Drag-and-Drop' and 'Shared Clipboard' features from the VirtualBox settings.
![](12_drag-and-drop_shared-clipboard.png)
![](13_kali_snapshot_config.png)


# What I Learned

Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

### 1. NAT vs NAT Network

A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine virtual cybersecurity laboratory.

### 2. Virtual Machine Networking

I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

### 3. Static IP Configuration

I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

### 4. VM Snapshots

A clean snapshot should be created **before performing risky or experimental activities**.

This provides a known-good recovery point for future cybersecurity exercises.

### 5. Duplicate Address Detection Bypass

I learned to bypass duplicate address detection **before performing risky or experimental activities**.

This is useful when trying to establish network uptime for VMs that may have IP clashes with other VMs (which may be turned off at the time).

### 6. Documentation

Documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

---

# Security & Ethical Use

This laboratory is intended strictly for education purposes only.

---

# Tools & Resources

- **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
- **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)

---




![](07_shared_folder_creation.png)

