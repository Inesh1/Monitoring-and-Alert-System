# Monitoring-and-Alert-System
Built and enterprise-style Linux home lab using kali and ubuntu featuring prometheus, grafana, loki, nmap, wireshark,, and bash automation for monitoring, alerting, centralized logging, and self healing infrastructure.

<div align="center">

# 🛡️ Linux Network Operations & Security Monitoring Lab

<p align="center">
  <img src="https://img.shields.io/badge/OS-Kali%20Linux%20%26%20Ubuntu-blue?style=for-the-badge&logo=linux&logoColor=white" />
  <img src="https://img.shields.io/badge/Monitoring-Prometheus%20%7C%20Grafana-E6522C?style=for-the-badge&logo=grafana&logoColor=white" />
  <img src="https://img.shields.io/badge/Security-Suricata%20%7C%20Fail2Ban-DC143C?style=for-the-badge&logo=shield&logoColor=white" />
  <img src="https://img.shields.io/badge/Logging-Loki%20%7C%20Promtail-F5A623?style=for-the-badge&logo=grafana&logoColor=white" />
  <img src="https://img.shields.io/badge/Automation-Bash%20%7C%20Cron-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white" />
  <img src="https://img.shields.io/badge/Status-Production--Style-success?style=for-the-badge" />
</p>

<p align="center">
  <b>An enterprise-grade home lab simulating a real-world NOC/SOC environment using open-source Linux technologies.</b><br/>
  Infrastructure Monitoring · Real-Time Alerting · Packet Analysis · Centralized Logging · Automation
</p>

</div>

---

## 📌 Overview

This project is a fully functional **enterprise-style Linux Network Operations & Security Monitoring Home Lab** built end-to-end using open-source tools.

It simulates the workflows of a real-world:

| Environment | Focus |
|---|---|
| 🖥️ Network Operations Center (NOC) | Infrastructure visibility & uptime |
| 🛡️ Security Operations Center (SOC) | Threat detection & log analysis |
| 📊 Monitoring Platform | Metrics, dashboards & alerting |
| 🤖 Automation Infrastructure | Self-healing scripts & scheduled ops |

---

## 🏗️ Architecture

```
                  ┌────────────────────────────┐
                  │       Kali Linux VM        │
                  │   Monitoring & Operations  │
                  ├────────────────────────────┤
                  │  Prometheus  │  Grafana     │
                  │  Alertmanager│  Loki        │
                  │  Wireshark   │  Nmap        │
                  │  Automation Scripts         │
                  └──────────────┬─────────────┘
                                 │
                        Host-Only Network
                         192.168.56.0/24
                                 │
                  ┌──────────────▼─────────────┐
                  │      Ubuntu Server VM      │
                  │      Target Test Server    │
                  ├────────────────────────────┤
                  │  Node Exporter │ Promtail   │
                  │  Suricata IDS  │ Fail2Ban   │
                  │  Nginx         │ Sys Logs   │
                  └────────────────────────────┘
```

---

## 🖥️ Lab Environment

| Component | Technology |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Monitoring VM | Kali Linux |
| Target Server VM | Ubuntu Server 24.04 LTS |
| Network Type | Host-Only + NAT |
| Monitoring Stack | Prometheus + Grafana |
| Logging Stack | Loki + Promtail |
| Security Stack | Suricata + Fail2Ban |
| Automation | Bash + Cron |
| Packet Analysis | Wireshark + tcpdump |

**Internal IPs:**
```
Kali Linux     →  192.168.56.10
Ubuntu Server  →  192.168.56.20
```

---

## 📂 Project Phases

| Phase | Title | Description |
|---|---|---|
| 0 | 🏠 Home Lab Setup | VirtualBox environment, networking, SSH |
| 1 | 🐧 Linux Administration | System config, tools, service management |
| 2 | 📊 Monitoring Stack | Prometheus, Grafana, Node Exporter |
| 3 | 🚨 Alerting System | Alertmanager, Telegram notifications |
| 4 | 🌐 Network Analysis | Nmap, Wireshark, tcpdump, iftop |
| 5 | 🛡️ Logging & Security | Loki, Promtail, Fail2Ban, Suricata |
| 6 | 🤖 Automation | Bash scripts, Cron jobs, self-healing |

---

## ⚙️ Phase Details

<details>
<summary><b>Phase 0 — Home Lab Setup</b></summary>

### Goal
Create a virtual enterprise-style network using VirtualBox.

**VMs Configured:**
- **Kali Linux** — Monitoring server, security analysis, automation control
- **Ubuntu Server** — Simulated production server, log & traffic generation

**Network Setup:**
- NAT Adapter → Internet access
- Host-Only Adapter → Internal lab communication

**Services Enabled:** SSH, Nginx, static networking, internal connectivity

</details>

<details>
<summary><b>Phase 1 — Linux Administration</b></summary>

### Goal
Prepare stable Linux infrastructure for monitoring and operations.

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y curl wget git vim htop net-tools unzip
```

**Skills Practiced:** System management, SSH administration, service management, package management, network troubleshooting, file system operations

</details>

<details>
<summary><b>Phase 2 — Infrastructure Monitoring Stack</b></summary>

### Goal
Build a production-style infrastructure monitoring platform.

**Stack:**
```
Ubuntu Server → Node Exporter → Prometheus → Grafana
```

**Dashboards Built:**
- CPU, Memory, Disk Usage
- Network Traffic
- System Uptime

</details>

<details>
<summary><b>Phase 3 — Alerting System</b></summary>

### Goal
Create a real-time alerting pipeline with Telegram notifications.

**Alert Rules:**

| Alert | Threshold |
|---|---|
| 🔥 High CPU | > 80% |
| 💾 High Memory | > 80% |
| ❌ Server Down | Node Exporter unreachable |

**Notification Flow:**
```
Prometheus → Alertmanager → Telegram Bot
```

</details>

<details>
<summary><b>Phase 4 — Network Analysis & Operations</b></summary>

### Goal
Build a professional network analysis environment.

**Operations Performed:**
- Host discovery with Nmap
- Service enumeration & version detection
- Live packet capture with tcpdump
- Traffic analysis (HTTP, DNS, SSH, ICMP)
- Bandwidth monitoring with iftop
- Manual TCP testing with Netcat

</details>

<details>
<summary><b>Phase 5 — Centralized Logging & Security Monitoring</b></summary>

### Goal
Build a mini-SIEM with centralized log collection and security dashboards.

**Logging Flow:**
```
Ubuntu Logs → Promtail → Loki → Grafana
```

**Security Events Monitored:**
- Failed SSH login attempts
- Successful authentication events
- Service errors & anomalies

</details>

<details>
<summary><b>Phase 6 — Automation & Self-Healing Infrastructure</b></summary>

### Goal
Automate infrastructure operations and enable self-healing services.

**Automation Features:**
- Health checks (CPU, RAM, Disk, Docker, Ports)
- Automatic service restart on failure
- Scheduled Nmap scans
- Automated packet captures
- Configuration backups via Cron

</details>

---

## 🛠️ Tool Reference

| Tool | Purpose |
|---|---|
| Prometheus | Metrics collection & storage |
| Grafana | Dashboard visualization |
| Alertmanager | Alert routing & notification |
| Node Exporter | Linux system metrics exporter |
| Loki | Centralized log aggregation |
| Promtail | Log shipping agent |
| Fail2Ban | Brute-force attack prevention |
| Nmap | Network scanning & service discovery |
| Wireshark | GUI packet analysis |
| tcpdump | CLI packet capture |
| Docker | Containerized service deployment |
| Bash + Cron | Scripting & scheduled automation |
| Netcat | Manual TCP/UDP network testing |

---

## 📋 Command Reference

### 🖥️ System & SSH
```bash
sudo apt update && sudo apt upgrade -y     # Update packages
ip a                                        # Show network interfaces
ssh labadmin@192.168.56.20                 # SSH into Ubuntu server
systemctl status nginx                      # Check service status
ss -tulnp                                   # Show listening ports
```

### 🐳 Docker
```bash
docker ps                                   # List running containers
docker-compose up -d                        # Start monitoring stack
docker-compose down                         # Stop monitoring stack
docker logs prometheus                      # View Prometheus logs
```

### 📊 Monitoring
```bash
curl http://192.168.56.20:9100/metrics      # Verify Node Exporter
stress --cpu 2 --timeout 120               # Generate CPU load
yes > /dev/null                             # Continuous CPU stress
```

### 🌐 Network Analysis
```bash
nmap -sn 192.168.56.0/24                   # Discover active hosts
nmap -sV 192.168.56.20                     # Detect services & versions
sudo nmap -A 192.168.56.20                 # Aggressive OS/service scan
sudo tcpdump -i any                         # Capture live packets
sudo tcpdump -i any port 22                # Capture SSH traffic only
sudo tcpdump -i any -w capture.pcap        # Save capture to file
sudo wireshark                              # Open GUI packet analyzer
sudo iftop                                  # Monitor bandwidth usage
nc -lvnp 4444                              # Create TCP listener
nc 192.168.56.20 4444                      # Connect to listener
```

### 🛡️ Security & Logging
```bash
sudo tail -f /var/log/auth.log             # Monitor auth logs live
sudo fail2ban-client status                # Check Fail2Ban status
sudo tail -f /var/log/suricata/fast.log    # View Suricata IDS alerts
ssh fakeuser@192.168.56.20                 # Simulate failed login
```

### 🤖 Automation
```bash
crontab -e                                 # Edit cron scheduler
chmod +x script.sh                         # Make script executable
./health_check.sh                          # Run health check
./network_scan.sh                          # Run automated Nmap scan
./packet_capture.sh                        # Run packet capture script
```

---

## 📸 Screenshots

>

| Dashboard | Preview |
|---|---|
| Grafana — System Metrics | `assets/grafana-dashboard.png` |
| Prometheus Targets | `assets/prometheus-targets.png` |
| Alertmanager Alerts | `assets/alertmanager.png` |
| Loki Log Viewer | `assets/loki-logs.png` |
| Wireshark Capture | `assets/wireshark.png` |
| Nmap Scan Results | `assets/nmap-scan.png` |
| Suricata IDS Alerts | `assets/suricata-alerts.png` |
| Automation Output | `assets/automation-output.png` |

---

## 🧠 Skills Demonstrated

**Linux & Infrastructure**
`Linux Administration` `System Monitoring` `Service Management` `Infrastructure Troubleshooting`

**Monitoring & Observability**
`Prometheus` `Grafana` `Alertmanager` `Metrics Collection` `Incident Detection`

**Networking & Security**
`Network Analysis` `Packet Inspection` `Nmap Scanning` `Wireshark` `IDS/IPS` `SIEM Fundamentals`

**Automation & DevOps**
`Bash Scripting` `Cron Automation` `Docker` `Self-Healing Infrastructure` `DevOps Fundamentals`

---

## 🚀 Future Improvements

- [ ] Kubernetes monitoring integration
- [ ] Cloud deployment on AWS
- [ ] Terraform infrastructure automation
- [ ] CI/CD pipeline integration
- [ ] Advanced Suricata IDS rule customization
- [ ] Threat intelligence feed integration
- [ ] Advanced SIEM-style security dashboards

---

## 👨‍💻 Author

**Inesh Singh Negi**

*Linux Infrastructure · Network Operations · Security Monitoring · Automation*

---

<div align="center">

⭐ **If you found this project useful, consider leaving a star!**

</div>
