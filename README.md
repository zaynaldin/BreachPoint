# 🔒 BreachPoint - Cloud-Hosted Domain Vulnerability Scanner

BreachPoint is a cloud-native security scanner hosted on Azure. It allows administrators to audit target domains, identify open network ports, and map discovered services to public CVE databases. Featuring an intuitive web dashboard and non-intrusive scanning, BreachPoint simplifies attack surface management and network vulnerability mapping.

### 🎓 Academic Info
* **Unit:** ICT-171 Final Project
* **Student:** Zaynaldin Ahmed Abdelfattah Attia
* **ID:** 35997081

### ☁️ Azure Deployment
* **Domain:** [https://breachpoint.ddns.net/](https://breachpoint.ddns.net/)
* **Public IP:** [20.89.20.174](http://20.89.20.174)
* **SSH Username:** `breachpoint`

---

### 🛠️ Core Features of BreachPoint
* **Port Discovery:** Scans common network ports on a target domain to identify exposed services.
* **CVE Mapping:** Automatically cross-references open ports with known vulnerabilities.
* **Web Dashboard:** A clean web interface to easily run scans and view logs.

### 📖 Step-by-Step Cloud Deployment & Implementation Guide
This guide is designed to take you from a local application to a fully live, secure cloud-hosted web server on Microsoft Azure. Whether you are deploying an API, a portfolio site, or a custom cybersecurity tool like BreachPoint, these foundational steps apply to almost any web technology stack.

### 📋 Prerequisites

Before you begin, ensure you have the following ready:

1. **A Cloud Account:** An active Microsoft Azure account (such as a Free Tier or Student Account).
2. **Local Terminal:** A terminal or command-line interface (Terminal on macOS/Linux, or PowerShell/Git Bash on Windows).
3. **Application Code:** A web application code structure ready in a local folder or pushed to a GitHub repository.
4. **Basic CLI Comfort:** Familiarity with running basic commands (navigating directories, connecting to remote systems).

### 🛠️ Phase 1: Provisioning the Cloud Server

The first step is setting up your virtual hardware in the cloud.

1. **Create an Azure Virtual Machine:**
   * Log into the Azure Portal and search for **Virtual Machines**.
   * Click **Create** $\rightarrow$ **Azure Virtual Machine**.
   * Select a lightweight, cost-effective Linux image (e.g., **Ubuntu Server 22.04 LTS**).
   * Set your administrator username (e.g., `breachpoint`).

2. **Configure Administrator Account:**
   * Under **Administrator account**, select **Password** as your authentication type.
   * Set your administrator username (e.g., `breachpoint`).
   * Enter a strong, secure password of your choice. Keep this safe, as you will need it to log into the system!
   * (you can use the normal SSH key way, however I used this method because it's way more beginner friendly)
  
  3. **Verify Your VM Properties (Visual Check):**
   Once your VM deployment is complete, navigate to your resource. Your Azure Virtual Machine dashboard configuration should be something like this layout:
   (remember, the specifications, vm, and storage will differ from one person to another depedning on their preferences)


   +---------------------------------------+---------------------------------------+
   | 💻 VIRTUAL MACHINE PROPERTIES         | 🌐 NETWORKING DETAILS                 |
   +---------------------------------------+---------------------------------------+
   | Computer name:      ICT171            | Public IP address:    20.89.20.174    |
   | Operating system:   Linux (ubuntu 22.04) | Private IP address:   10.1.1.4        |
   | VM architecture:    x64               | Virtual network:      ICT171-vnet     |
   | Agent status:       Ready             |                                       |
   +---------------------------------------+---------------------------------------+
   | 🎛️ HARDWARE SPECIFICATIONS             | 💿 STORAGE & SOURCE DETAILS           |
   +---------------------------------------+---------------------------------------+
   | VM Size:            Standard B2ats v2 | OS Disk Name:         ICT171_OsDisk   |
   | vCPUs:              2                 | Source Publisher:     canonical       |
   | RAM Memory:         1 GiB             | Source Plan:          server          |
   +---------------------------------------+---------------------------------------+



