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

---

### 📖 Step-by-Step Cloud Deployment & Implementation Guide
This guide is designed to take you from a local application to a fully live, secure cloud-hosted web server on Microsoft Azure. Whether you are deploying an API, a portfolio site, or a custom cybersecurity tool like BreachPoint, these foundational steps apply to almost any web technology stack.

### 📋 Prerequisites

Before you begin, ensure you have the following ready:

1. **A Cloud Account:** An active Microsoft Azure account (such as a Free Tier or Student Account).
2. **Local Terminal:** A terminal or command-line interface (Terminal on macOS/Linux, or PowerShell/Git Bash on Windows).
3. **Application Code:** A web application code structure ready in a local folder or pushed to a GitHub repository.
4. **Basic CLI Comfort:** Familiarity with running basic commands (navigating directories, connecting to remote systems).

---

### 🛠️ Phase 1: Provisioning the Cloud Server

The first step is setting up your virtual hardware in the cloud.

1. **Create an Azure Virtual Machine:**
   * Log into the Azure Portal and search for **Virtual Machines**.
   * Click **Create** → **Azure Virtual Machine**.
   * Select a lightweight, cost-effective Linux image (e.g., **Ubuntu Server 22.04 LTS**).

2. **Configure Administrator Account:**
   * Under **Administrator account**, select **Password** as your authentication type.
   * Set your administrator username (e.g., `breachpoint`).
   * Enter a strong, secure password of your choice. Keep this safe, as you will need it to log into the system!
   
   > 💡 **Tip:** You can choose to set up SSH keys here instead, but password authentication is often much more straightforward and beginner-friendly when you are deploying your very first cloud server.

3. **Verify Your VM Properties (Visual Check):**
   Once your VM deployment is complete, navigate to your resource. Your Azure Virtual Machine dashboard configuration should resemble the following layout:

   ```text
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
   ```
   it should look like that:
   ![Verify Your Azure VM Properties](https://raw.githubusercontent.com/zaynaldin/BreachPoint/348553b1cade45d185128de56d759e06cf42289a/images/Screenshot%202026-07-16%20151031.png)


### 🔑 Phase 2: Connecting and Hardening Your VM

With your cloud server officially online, the next step is securely logging in via the Command Line Interface (CLI) and setting up essential defensive baselines.

#### 1. Access Your Server via SSH
Open your local terminal (Terminal on macOS/Linux, or PowerShell/Git Bash on Windows) and execute the SSH command below:

```bash
ssh yourname@publicip
(e.g., 'ssh breachpoint@20.89.20.174')
```
* **The First-Time Connection Warning:** You will see a prompt saying:
  > `The authenticity of host... can't be established. Are you sure you want to continue connecting (yes/no/[fingerprint])?`
  
  Type **`yes`** and press **Enter**.

* **Entering Your Password:** The terminal will ask for your administrator password. 
  
  > ⚠️ **Linux Security Note:** When you type your password in the terminal, **no characters, dots, or asterisks will appear on the screen.** This is a standard security feature to prevent "shoulder-surfing" (people looking over your shoulder to steal your password). Just type your password blindly and hit **Enter**.

#### 2. Refresh & Update the System
Before hosting any applications online, update your package manager and patch any outdated system libraries to ensure everything is secure:

```bash
sudo apt update && sudo apt upgrade -y
```

---

### 🚀 Phase 3: Setting Up the Web Application Server

With a secure operating system environment running, we will now deploy the Apache HTTP Web Server to host and serve our application files to the public.

#### 1. Install Apache2
Run the following command to install the Apache web server package on your virtual machine:

```bash
sudo apt install apache2 -y
```
#### 2. Manage the Apache Service
Use the system service manager (`systemctl`) to ensure Apache starts up immediately and launches automatically whenever your server reboots:

```bash
# Start the web server
sudo systemctl start apache2

# Enable the service to launch on boot
sudo systemctl enable apache2

# Check the status to verify it is active and running
sudo systemctl status apache2
```
#### 3. Confirm Your Web Server is Online
Once the service is active, you can verify your web server is successfully receiving traffic:

1. Open a web browser on your computer.
2. Enter your VM's public IP address in the address bar:
   
   ```text
   http://your-public-IP
   ```
