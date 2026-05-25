# Monitoring-and-Alert-System
Built and enterprise-style Linux home lab using kali and ubuntu featuring prometheus, grafana, loki, nmap, wireshark,, and bash automation for monitoring, alerting, centralized logging, and self healing infrastructure.



# 🚀 Linux Network Operations & Monitoring Home Lab

<div align="center">

![Linux](https://img.shields.io/badge/Linux-Kali%20%26%20Ubuntu-blue?style=for-the-badge\&logo=linux)
![Monitoring](https://img.shields.io/badge/Monitoring-Prometheus%20%7C%20Grafana-orange?style=for-the-badge)
![Security](https://img.shields.io/badge/Security-Suricata%20%7C%20Fail2Ban-red?style=for-the-badge)
![Automation](https://img.shields.io/badge/Automation-Bash%20%7C%20Cron-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Production%20Style-success?style=for-the-badge)

</div>

---

# 📌 Project Overview

This project is a complete enterprise-style Linux Network Operations & Security Monitoring Home Lab built using open-source technologies.

The objective of this lab is to simulate a real-world:

* Network Operations Center (NOC)
* Security Operations Center (SOC)
* Infrastructure Monitoring Platform
* Security Monitoring Environment
* Automation & Self-Healing Infrastructure

The lab focuses on:

✅ Infrastructure Monitoring
✅ Real-Time Alerting
✅ Packet Analysis
✅ Network Scanning
✅ Centralized Logging
✅ Security Monitoring
✅ Intrusion Detection
✅ Infrastructure Automation
✅ Incident Detection & Visibility

---

# 🏗️ Final Architecture

```text
                     ┌────────────────────────────┐
                     │       Kali Linux VM        │
                     │  Monitoring & Operations   │
                     ├────────────────────────────┤
                     │ • Prometheus               │
                     │ • Grafana                  │
                     │ • Alertmanager             │
                     │ • Loki                     │
                     │ • Wireshark                │
                     │ • Nmap                     │
                     │ • Automation Scripts       │
                     └─────────────┬──────────────┘
                                   │
                          Host-Only Network
                                   │
                     ┌─────────────▼──────────────┐
                     │      Ubuntu Server VM      │
                     │      Target/Test Server    │
                     ├────────────────────────────┤
                     │ • Node Exporter            │
                     │ • Promtail                 │
                     │ • Suricata IDS             │
                     │ • Fail2Ban                 │
                     │ • Nginx                    │
                     │ • System Logs              │
                     └────────────────────────────┘
```

---

# 🖥️ Lab Environment

| Component          | Technology              |
| ------------------ | ----------------------- |
| Hypervisor         | Oracle VirtualBox       |
| Main Monitoring VM | Kali Linux              |
| Target Server VM   | Ubuntu Server 24.04 LTS |
| Network Type       | Host-Only + NAT         |
| Monitoring Stack   | Prometheus + Grafana    |
| Logging Stack      | Loki + Promtail         |
| Security Stack     | Suricata + Fail2Ban     |
| Automation         | Bash + Cron             |
| Packet Analysis    | Wireshark + tcpdump     |

---

# 📂 Project Phases

* Phase 0 — Home Lab Setup
* Phase 1 — Linux Administration
* Phase 2 — Monitoring Stack
* Phase 3 — Alerting System
* Phase 4 — Network Analysis & Operations
* Phase 5 — Centralized Logging & Security Monitoring
* Phase 6 — Automation & Self-Healing Infrastructure

---

# 📋 COPY-PASTE COMMAND REFERENCE

## 🖥️ Basic Linux Commands

```bash
sudo apt update && sudo apt upgrade -y
# Updates package lists and upgrades installed packages
```

```bash
ip a
# Displays IP addresses and network interfaces
```

```bash
ping 192.168.56.20
# Tests connectivity between VMs
```

```bash
ssh labadmin@192.168.56.20
# Remote login into Ubuntu server using SSH
```

```bash
systemctl status nginx
# Checks service status
```

```bash
ss -tulnp
# Shows listening ports and active services
```

---

# 🐳 Docker Commands

```bash
docker ps
# Lists running Docker containers
```

```bash
docker-compose up -d
# Starts monitoring stack in background
```

```bash
docker-compose down
# Stops monitoring containers
```

```bash
docker logs prometheus
# Shows Prometheus container logs
```

---

# 📊 Monitoring Commands

```bash
curl http://192.168.56.20:9100/metrics
# Verifies Node Exporter metrics endpoint
```

```bash
stress --cpu 2 --timeout 120
# Generates CPU load for alert testing
```

```bash
yes > /dev/null
# Creates continuous CPU stress
```

---

# 🌐 Network Analysis Commands

```bash
nmap -sn 192.168.56.0/24
# Discovers active hosts in network
```

```bash
nmap -sV 192.168.56.20
# Detects running services and versions
```

```bash
sudo nmap -A 192.168.56.20
# Performs aggressive scan with OS and service detection
```

```bash
sudo tcpdump -i any
# Captures live network packets
```

```bash
sudo tcpdump -i any port 22
# Captures SSH traffic only
```

```bash
sudo tcpdump -i any -w capture.pcap
# Saves packet capture into .pcap file
```

```bash
sudo wireshark
# Opens GUI packet analyzer
```

```bash
sudo iftop
# Monitors real-time bandwidth usage
```

```bash
nc -lvnp 4444
# Creates listening TCP server using netcat
```

```bash
nc 192.168.56.20 4444
# Connects to TCP listener for testing
```

---

# 📜 Logging & Security Commands

```bash
sudo tail -f /var/log/auth.log
# Monitors authentication logs live
```

```bash
sudo fail2ban-client status
# Checks Fail2Ban protection status
```

```bash
sudo tail -f /var/log/suricata/fast.log
# Displays IDS alerts from Suricata
```

```bash
ssh fakeuser@192.168.56.20
# Generates failed login attempts for testing
```

---

# 🤖 Automation Commands

```bash
crontab -e
# Opens cron scheduler configuration
```

```bash
chmod +x script.sh
# Makes script executable
```

```bash
./health_check.sh
# Runs infrastructure health check script
```

```bash
./network_scan.sh
# Runs automated Nmap network scan
```

```bash
./packet_capture.sh
# Runs automated packet capture script
```

---

# 🛠️ Tool Reference

| Tool          | Purpose                                      |
| ------------- | -------------------------------------------- |
| Prometheus    | Collects infrastructure metrics              |
| Grafana       | Visualizes metrics and logs using dashboards |
| Alertmanager  | Sends infrastructure alerts                  |
| Node Exporter | Exports Linux system metrics                 |
| Loki          | Centralized log aggregation                  |
| Promtail      | Ships logs to Loki                           |
| Nmap          | Network scanning and service discovery       |
| Wireshark     | GUI packet analysis tool                     |
| tcpdump       | CLI packet capture tool                      |
| Fail2Ban      | Blocks brute-force login attacks             |
| Suricata      | Intrusion Detection System (IDS)             |
| Docker        | Runs monitoring services in containers       |
| Bash          | Infrastructure automation scripting          |
| Cron          | Schedules automated tasks                    |
| Netcat        | Manual TCP/UDP network testing               |

---

# ⚙️ PHASE 0 — HOME LAB SETUP

## 🎯 Goal

Create a virtual enterprise-style network lab environment using VirtualBox.

---

## 🔹 Virtual Machines

### 🖥️ Kali Linux VM

Purpose:

* Monitoring Server
* Security Analysis
* Automation Control Center
* Dashboard Management

### 🖥️ Ubuntu Server VM

Purpose:

* Simulated Production Server
* Log Generation
* Network Traffic Generation
* Security Event Testing

---

## 🔹 Network Configuration

Configured:

* NAT Adapter → Internet Access
* Host-Only Adapter → Internal Lab Communication

Example Internal IPs:

```text
Kali Linux      → 192.168.56.10
Ubuntu Server   → 192.168.56.20
```

---

## 🔹 Services Enabled

* SSH Access
* Nginx Web Server
* Internal Communication Testing
* Static Networking

---

# 🐧 PHASE 1 — BASE LINUX ADMINISTRATION

## 🎯 Goal

Prepare stable Linux infrastructure for monitoring and operations.

---

## 🔹 System Configuration

Performed:

```bash
sudo apt update && sudo apt upgrade -y
```

Installed tools:

```bash
curl
wget
git
vim
htop
net-tools
unzip
```

---

## 🔹 Linux Skills Practiced

* System management
* SSH administration
* Service management
* Network troubleshooting
* Package management
* File system operations

---

## 🔹 Important Linux Commands Used

```bash
systemctl
journalctl
ss
netstat
ip a
ping
curl
ps
htop
```

---

# 📊 PHASE 2 — INFRASTRUCTURE MONITORING STACK

## 🎯 Goal

Build a production-style infrastructure monitoring platform.

---

# 🛠️ Monitoring Stack

| Tool          | Purpose                    |
| ------------- | -------------------------- |
| Prometheus    | Metrics Collection         |
| Grafana       | Dashboards & Visualization |
| Node Exporter | Linux Metrics Exporter     |
| Docker        | Containerized Deployment   |

---

## 🔹 Components Installed

### 📌 Prometheus

Configured for:

* CPU Monitoring
* RAM Monitoring
* Disk Monitoring
* Network Monitoring
* Uptime Tracking

---

### 📌 Grafana

Configured dashboards for:

* CPU Usage
* Memory Usage
* Disk Utilization
* Network Traffic
* System Uptime

---

### 📌 Node Exporter

Installed on Ubuntu Server.

Exports:

```text
CPU Metrics
Memory Metrics
Disk Metrics
Network Metrics
System Metrics
```

---

## 🔹 Monitoring Architecture

```text
Ubuntu Server → Node Exporter → Prometheus → Grafana
```

---

## 🔹 Key Skills Learned

* Infrastructure Observability
* Metrics Collection
* Dashboard Engineering
* Containerized Monitoring
* Monitoring Architecture

---

# 🚨 PHASE 3 — ALERTING SYSTEM

## 🎯 Goal

Create a real-time infrastructure alerting platform.

---

# 🛠️ Alerting Stack

| Tool             | Purpose             |
| ---------------- | ------------------- |
| Alertmanager     | Alert Routing       |
| Telegram Bot     | Alert Notifications |
| Prometheus Rules | Incident Detection  |

---

## 🔹 Alerts Implemented

### 🔥 High CPU Usage Alert

Detects:

```text
CPU Usage > 80%
```

---

### 💾 High Memory Usage Alert

Detects:

```text
Memory Usage > 80%
```

---

### ❌ Server Down Alert

Detects:

```text
Node Exporter unavailable
```

---

## 🔹 Notification Flow

```text
Prometheus → Alertmanager → Telegram Alerts
```

---

## 🔹 Incident Simulation

Performed:

* CPU Stress Testing
* Service Failure Simulation
* Infrastructure Alert Validation

---

## 🔹 Key Skills Learned

* Incident Detection
* Alert Routing
* Infrastructure Monitoring
* Observability Engineering
* SRE Fundamentals

---

# 🌐 PHASE 4 — NETWORK ANALYSIS & OPERATIONS

## 🎯 Goal

Create a professional network analysis and troubleshooting environment.

---

# 🛠️ Network Analysis Toolset

| Tool      | Purpose              |
| --------- | -------------------- |
| Nmap      | Network Scanning     |
| Wireshark | Packet Analysis      |
| tcpdump   | Packet Capture       |
| iftop     | Bandwidth Monitoring |
| netcat    | Network Testing      |

---

## 🔹 Network Operations Performed

### 📡 Host Discovery

```bash
nmap -sn 192.168.56.0/24
```

---

### 🔎 Service Enumeration

```bash
nmap -sV TARGET-IP
```

---

### 📦 Packet Capture

```bash
sudo tcpdump -i any
```

---

### 🌍 Traffic Analysis

Analyzed:

* HTTP Traffic
* DNS Traffic
* SSH Traffic
* ICMP Traffic

---

### 📊 Bandwidth Monitoring

```bash
sudo iftop
```

---

## 🔹 Key Skills Learned

* Network Reconnaissance
* Packet Inspection
* Traffic Analysis
* Infrastructure Troubleshooting
* Network Visibility

---

# 🛡️ PHASE 5 — CENTRALIZED LOGGING & SECURITY MONITORING

## 🎯 Goal

Build a mini SIEM-style centralized logging and security monitoring platform.

---

# 🛠️ Logging & Security Stack

| Tool     | Purpose              |
| -------- | -------------------- |
| Loki     | Centralized Logging  |
| Promtail | Log Shipping         |
| Grafana  | Log Visualization    |
| Fail2Ban | Intrusion Prevention |

---

## 🔹 Logs Collected

### 📄 System Logs

Collected:

```text
/var/log/*.log
```

---

### 🔐 Authentication Logs

Collected:

```text
/var/log/auth.log
```

---

## 🔹 Security Monitoring Features

### 🚫 Failed SSH Login Detection

Detected:

```text
Failed password attempts
```

---

### ✅ Successful Login Monitoring

Detected:

```text
Accepted password events
```

---

### 🔥 Security Dashboards

Created dashboards for:

* SSH Failures
* Authentication Events
* Service Errors
* Security Logs
* Incident Visibility

---

## 🔹 Logging Flow

```text
Ubuntu Logs → Promtail → Loki → Grafana
```

---

## 🔹 Key Skills Learned

* Centralized Logging
* Security Monitoring
* Authentication Analysis
* SIEM Fundamentals
* Log Aggregation

---

# 🤖 PHASE 6 — AUTOMATION & SELF-HEALING OPERATIONS

## 🎯 Goal

Automate infrastructure operations and create self-healing services.

---

# 🛠️ Automation Stack

| Tool         | Purpose            |
| ------------ | ------------------ |
| Bash Scripts | Automation         |
| Cron Jobs    | Scheduling         |
| Systemd      | Service Management |
| Nmap         | Automated Scanning |

---

## 🔹 Automation Features Implemented

### ✅ Health Check Automation

Checks:

* Server Availability
* CPU Usage
* RAM Usage
* Disk Usage
* Docker Containers
* Open Ports

---

### 🔄 Automated Service Recovery

Automatically:

```text
Detects failed services
Restarts services
Logs recovery actions
```

---

### 📅 Scheduled Infrastructure Tasks

Configured using:

```bash
crontab -e
```

Automated:

* Health Checks
* Nmap Scans
* Log Cleanup
* Packet Captures
* Backups

---

### 📦 Automated Packet Capture

Generated:

```text
.pcap traffic capture files
```

---

### 💾 Automated Backups

Backed up:

* Monitoring Configurations
* Scripts
* Docker Configurations
* Infrastructure Files

---

## 🔹 Key Skills Learned

* Infrastructure Automation
* Self-Healing Systems
* Linux Scripting
* Scheduled Operations
* DevOps Fundamentals

---

# 🧠 TECHNICAL SKILLS GAINED

## Linux & Infrastructure

* Linux Administration
* System Monitoring
* Service Management
* Infrastructure Troubleshooting

---

## Monitoring & Observability

* Prometheus
* Grafana
* Alertmanager
* Metrics Monitoring
* Incident Detection

---

## Networking & Security

* Network Analysis
* Packet Inspection
* Nmap Scanning
* Wireshark Analysis
* Centralized Logging
* Security Monitoring

---

## Automation & DevOps

* Bash Scripting
* Cron Automation
* Docker
* Infrastructure Automation
* Self-Healing Operations

---

# 📈 PROJECT OUTCOME

This project successfully demonstrates:

✅ Enterprise-style Infrastructure Monitoring
✅ Real-Time Alerting & Incident Detection
✅ Network Analysis & Packet Inspection
✅ Centralized Logging & Security Monitoring
✅ Automation & Self-Healing Infrastructure
✅ Practical Linux Administration Skills
✅ SOC/NOC Operational Workflows

---

# 🎯 TARGET ROLES

This project aligns with:

* SOC Analyst
* NOC Engineer
* DevOps Engineer
* SRE Intern
* Infrastructure Engineer
* Network Operations Analyst
* Cloud Support Engineer
* Security Operations Intern

---

# 📸 RECOMMENDED SCREENSHOTS FOR README

Add screenshots for:

* Grafana Dashboards
* Prometheus Targets
* Alertmanager Alerts
* Loki Logs
* Wireshark Packet Capture
* Nmap Scan Results
* Suricata IDS Alerts
* Automation Script Outputs

---

# 🚀 FUTURE IMPROVEMENTS

Planned upgrades:

* Kubernetes Monitoring
* Cloud Integration (AWS)
* Terraform Automation
* CI/CD Integration
* Suricata Advanced IDS Rules
* Threat Intelligence Feeds
* Advanced Security Dashboards

---

# 👨‍💻 Author

## Inesh Negi

Linux Infrastructure • Network Operations • Security Monitoring • Automation

---

# ⭐ Final Summary

This project simulates a real-world enterprise monitoring and security operations environment using open-source Linux technologies.

The home lab demonstrates practical skills in:

* Infrastructure Monitoring
* Incident Detection
* Security Visibility
* Network Operations
* Automation Engineering
* Centralized Logging
* Infrastructure Troubleshooting

making it a strong portfolio project for infrastructure, networking, DevOps, and cybersecurity roles.

