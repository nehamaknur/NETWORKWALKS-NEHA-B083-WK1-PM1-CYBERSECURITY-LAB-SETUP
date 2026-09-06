<div align="center">

# 🛡️ Cybersecurity Lab Environment Setup

Building a custom isolated testing infrastructure on a Windows 11 host with static NAT routing, dedicated DNS resolution & snapshot recovery.

[![Cybersecurity Lab](https://img.shields.io/badge/Project-Isolated_Cybersecurity_Lab-00ff66?style=for-the-badge&logo=kalilinux&logoColor=white)](https://github.com) [![VirtualBox](https://img.shields.io/badge/Hypervisor-VirtualBox_v7.1.18-blue?style=for-the-badge&logo=virtualbox&logoColor=white)](https://github.com) [![Kali Linux](https://img.shields.io/badge/OS-Kali_Linux_2026.1-orange?style=for-the-badge&logo=kalilinux&logoColor=white)](https://github.com) [![Network](https://img.shields.io/badge/Subnet-10.0.0.0/24-teal?style=for-the-badge)](https://github.com) [![Skill](https://img.shields.io/badge/Skill-Penetration_Testing-red?style=for-the-badge&logo=hackthebox&logoColor=white)](https://github.com) [![GitHub](https://img.shields.io/badge/GitHub-CortexNeha-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com) [![Author](https://img.shields.io/badge/Author-Neha_Maknur-blue?style=for-the-badge&logo=readthedocs&logoColor=white)](https://github.com)


</div


  
<h2>📍 Project Overview</h2>

This project documents the setup of an isolated virtual cybersecurity laboratory using Oracle VM VirtualBox and Kali Linux.

The lab provides a controlled environment for practicing cybersecurity concepts, network reconnaissance, vulnerability assessment, and penetration-testing techniques in a safe and authorized environment.

The main purpose of this project is to build a hands-on cybersecurity environment where security tools and techniques can be practiced without affecting real-world systems or networks.

## 🎯 Objectives

- Install and configure Oracle VM VirtualBox and Kali Linux.
- Build an isolated virtual cybersecurity laboratory.
- Configure a custom NAT Network for the virtual lab.
- Configure appropriate IP addressing, gateway, and DNS settings.
- Assign and verify network settings for the Kali Linux virtual machine.
- Create virtual machine snapshots for recovery and experimentation.
- Document the complete setup process for future reference and repeatability.

## 🎯 Purpose of the Lab

The purpose of this lab is to create a controlled virtual environment for learning and practicing cybersecurity concepts, networking, and security tools using Kali Linux.

The lab provides an isolated environment where cybersecurity experiments can be performed safely without affecting real-world systems or networks.

## ⚙️ Lab Environment

| Component                 | Configuration                                    |
| ------------------------- | ------------------------------------------------ |
| Host Operating System     | Windows 11                                       |
| Host RAM                  | 8 GB                                             |
| Processor                 | AMD Ryzen 5 5500U with Radeon Graphics           |
| Virtualization Platform   | Oracle VM VirtualBox 7.1.18-173720-Win           |
| Security Operating System | Kali Linux `kali-linux-2026.1-virtualbox-amd64`  |
| Network Mode              | NAT Network                                      |
| Kali Linux IP             | `10.0.0.2/24`                                    |
| Default Gateway           | `10.0.0.1`                                       |
| DNS Server                | `8.8.8.8`                                        |
| Snapshot                  | My Fresh Kali Linux                              |

This section lists the host system, virtualization software, Kali Linux version, network configuration, and other resources used to build the lab.

## 🖥️ Lab Architecture   

![Cybersecurity Lab Architecture](1-title-image.png)

The lab network can be expanded in future projects by adding additional virtual machines for testing and practice.

## 💻 Virtual Machine Configuration

The Kali Linux virtual machine was configured with the following settings:

* **RAM:** `2048 MB`
* **Network Adapter:** NAT Network
* **Operating System:** Kali Linux
* **Virtualization Platform:** Oracle VM VirtualBox

## 🚀 Installation & Setup

### 1. Install 7-Zip

7-Zip was installed to extract the downloaded Kali Linux virtual machine files.

### 2. Install VirtualBox

Oracle VM VirtualBox 7.1.18 was installed on the Windows 11 host to provide the virtualization environment for the cybersecurity lab.

### 3. Obtain Kali Linux

The Kali Linux `2026.1` VirtualBox image was downloaded and extracted using 7-Zip before importing it into VirtualBox.

![Kali Linux Homepage](3-kali-linux.png)

### 4. Import the Virtual Machine

The downloaded Kali Linux virtual machine was imported into Oracle VM VirtualBox. The virtual machine was configured with **2048 MB RAM** and connected to the **NAT Network**. A shared folder was also created between the Windows host and Kali Linux VM for file sharing.

### 5. Configure the NAT Network

A dedicated NAT Network was created in VirtualBox with the following configuration:

| Network Component | Configuration |
| ----------------- | ------------- |
| NAT Network       | `10.0.0.0/24` |
| Gateway           | `10.0.0.1`    |

![NAT Network Configuration](2-network-settings-virtualbox.png)

### 6. Configure Kali Linux Networking

Kali Linux was configured with the following network settings:

| Network Component | Configuration |
| ----------------- | ------------- |
| IP Address        | `10.0.0.2/24` |
| Default Gateway   | `10.0.0.1`    |
| DNS Server        | `8.8.8.8`     |

![Kali Linux Network Configuration](4-kali-network-settings.png)

> **Troubleshooting:** `10.0.0.1` was tested as the DNS server but did not work. `8.8.8.8` was configured and worked successfully.

### 8. 📸 Create a Snapshot

A clean virtual machine snapshot was created after completing the initial configuration.

![Kali Linux Snapshot](VM-snapshot.png)

## 🔎 Lab Verification

| Verification Command | Purpose |
|---|---|
| `ip a` | Verified the Kali Linux IP address `10.0.0.2/24` |
| `ip route` | Verified the default gateway `10.0.0.1` |
| `ping 10.0.0.1` | Confirmed connectivity to the NAT Network gateway |
| `ping 8.8.8.8` | Confirmed connectivity to the external network |
| `nslookup google.com` | Confirmed DNS resolution |

## 🔧 Troubleshooting

### Problem Faced

During the Kali Linux network configuration, `10.0.0.1` was initially tested as the DNS server, but DNS resolution did not work.

### Why It Happened

Although `10.0.0.1` was working as the gateway, it was not functioning as a DNS resolver in this lab configuration.

### How I Recovered

I tested another DNS server and configured `8.8.8.8` in Kali Linux. DNS resolution then worked successfully.

### Result

The Kali Linux virtual machine was successfully configured with:

* **IP Address:** `10.0.0.2/24`
* **Default Gateway:** `10.0.0.1`
* **DNS Server:** `8.8.8.8`

The network configuration was then verified successfully, and a clean snapshot named `My Fresh Kali Linux` was created as a recovery point.

## 📚 What I Learned

### 💻 Virtualization

* Learned how VirtualBox is used to create and manage virtual machines.
* Understood how Kali Linux runs as a virtual machine on a Windows host.

### 🌐 Networking

* Learned how to create and configure a NAT Network.
* Understood the roles of IP address, subnet mask, default gateway, and DNS.

### 🔧 Troubleshooting

* Learned how to identify and resolve a DNS configuration issue.
* Tested different DNS settings and verified the working configuration.

### 📸 Snapshots & Recovery

* Learned how to create a virtual machine snapshot.
* Understood how snapshots provide a recovery point before performing further experiments or making configuration changes.

### 📝 Documentation

* Learned how to document configurations, screenshots, troubleshooting steps, and results in a structured GitHub README.

## 🔐 Security Tools & Practice

The laboratory will be used to practice cybersecurity concepts including:

- Network reconnaissance
- Network scanning
- Service enumeration
- Vulnerability assessment
- Linux security fundamentals
- Network security concepts
- Penetration-testing methodologies

All testing will be performed only against systems that are owned by me or explicitly authorized for testing.

## 🛠️ Tools Used

- **Oracle VM VirtualBox 7.1.18** — (https://www.virtualbox.org/wiki/Downloads)
- **Kali Linux 2026.1** — (https://www.kali.org/get-kali/)
- **7-Zip** — (https://www.7-zip.org/download.html)
- **GitHub** — (https://github.com/)
  
# 👤 Author

**Neha Maknur**
B.Sc. Computer Science Graduate
Cybersecurity Learner

LinkedIn: (https://lnkd.in/p/d3URNTtf)

## 📍 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup | **Repository:** GitHub

This project is part of the Cybersecurity at Networkwalks Week 01 practical work and focuses on building and documenting a cybersecurity and penetration-testing lab.

