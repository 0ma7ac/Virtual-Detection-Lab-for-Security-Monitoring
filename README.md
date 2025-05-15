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

---

## 📦 Elastic Stack Setup (Coming Soon)

🚧 *Screenshots and setup steps for Elastic Stack, Agents, and detection rules will be added here.*

---

## 📁 Project Structure

```bash
~/dev/detection-lab-elk
├── detection-lab-elk-design.drawio.pdf  # Lab design diagram
├── README.md                             # This documentation file
