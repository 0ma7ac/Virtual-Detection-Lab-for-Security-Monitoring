# 🔍 Virtual Detection Lab for Security Monitoring

This project sets up a **virtual detection environment** for simulating cyber-attacks and monitoring them using the **Elastic Stack (ELK)**. It includes virtual machines (Ubuntu, Windows 10/11, and Kali Linux) running in VMware Workstation on a Fedora host.

📄 [Click here to view the Design Diagram (PDF)](./detection-lab-elk-design.drawio.pdf)
---

## 🧠 Project Goal

To simulate attacks using Kali Linux and monitor host machines (Ubuntu & Windows) using the **Elastic Stack (SIEM)** for **real-time security monitoring, analysis, and learning**.

---

## 🏗️ Lab Architecture

- **Host OS:** Fedora Linux  
- **Virtualization:** VMware Workstation  
- **Virtual Machines:**
  - Ubuntu (with Elastic Agent)
  - Windows 10/11 (with Elastic Agent)
  - Kali Linux (as attacker machine)
- **Monitoring:** ELK Stack (ElasticSearch, Logstash, Kibana)

---

## 🛠️ Installation Guide

Please follow the YouTube tutorials below to install each component properly.

### 📥 Step-by-Step Installation Videos:

- 🖥️ **Download & Install VMware Workstation:**  
  [Watch here](https://www.youtube.com/watch?v=9XiKVjlZJdk)

- 🐧 **Install Ubuntu in VMware:**  
  [Watch here](https://www.youtube.com/watch?v=SgfrHKg81Qc)

- 🐉 **Install Kali Linux in VMware:**  
  [Watch here](https://www.youtube.com/watch?v=jXlVGa1t5P0)

- 🪟 **Install Windows 11 VM in VMware:**  
  [Watch here](https://www.youtube.com/watch?v=EMuw_IN-UOU)

> ⚠️ Make sure you allocate enough RAM, CPU cores, and networking setup (bridged or NAT) for smooth operation.


## 🕵️ Install Zeek 6.0 LTS on Ubuntu 22.04 (Binary Package)

Zeek is a powerful network traffic analysis tool used for security monitoring. Below are the official steps to install **Zeek 6.0 LTS** on **Ubuntu 22.04** using binary packages.

📖 **Source:** [Zeek Official Installation Docs](https://docs.zeek.org/en/v7.2.1/install.html#binary-packages)  
> ⚠️ *The repository URL and version may change in the future. Always check the official documentation for the latest instructions.*

---

### 🧰 Prerequisites

First, install `curl` if not already installed:

```bash
sudo apt update
sudo apt install curl -y
```

---

### 🔐 Step 1: Switch to Root

Before proceeding with repository setup, switch to the root user:

```bash
su
```

Enter your root password when prompted.

---

### 📥 Step 2: Add the Zeek Repository

```bash
echo 'deb http://download.opensuse.org/repositories/security:/zeek/xUbuntu_22.04/ /' | tee /etc/apt/sources.list.d/security:zeek.list
curl -fsSL https://download.opensuse.org/repositories/security:zeek/xUbuntu_22.04/Release.key | gpg --dearmor | tee /etc/apt/trusted.gpg.d/security_zeek.gpg > /dev/null
apt update
```

---

### 📦 Step 3: Install Zeek

```bash
apt install zeek-6.0 -y
```

> ✅ Zeek will be installed in `/opt/zeek`.

---

## ⚙️ Basic Zeek Configuration

### 🔧 Configure Network Interface

1. Go to the Zeek config directory:

```bash
cd /opt/zeek/etc/
```

2. Edit `node.cfg`:

```bash
nano node.cfg
```

3. Locate this line:

```
interface=eth0
```

4. In another terminal, run:

```bash
ip addr
```

Find your **private IP** and note the interface name (e.g., `ens33`, `enp0s3`, etc.). Replace `eth0` with your actual interface name in `node.cfg`.

5. Save and close the file (`CTRL+O`, `ENTER`, then `CTRL+X` in nano).

---

## 🚀 Running Zeek

### 🧪 First-Time Deployment

```bash
cd /opt/zeek/bin/
./zeekctl deploy
```

Monitor logs in `/opt/zeek/logs/current/`.

---

## 🔁 Optional: Run Zeek from Anywhere

To make `zeekctl` and `zeek` globally accessible:

```bash
echo 'export PATH=/opt/zeek/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

Now you can run:

```bash
zeekctl status
```

from any location.

---

## 📝 Optional: Enable JSON Logging

To log in JSON format (useful for ELK integration):

1. Edit the main Zeek config:

```bash
nano /opt/zeek/share/zeek/site/local.zeek
```

2. Add this line at the end:

```zeek
@load policy/tuning/json-logs.zeek
```

3. Save and exit.

4. Apply the change:

```bash
zeekctl deploy
```

---


---

## 📦 Elastic Stack Setup (Coming Soon)

🚧 *Screenshots and setup steps for Elastic Stack, Agents, and detection rules will be added here.*

---

## 📁 Project Structure

```bash
~/dev/detection-lab-elk
├── detection-lab-elk-design.drawio.pdf  # Lab design diagram
├── README.md                             # This documentation file
