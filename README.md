# Monitoring-and-Alert-System
Built and enterprise-style Linux home lab using kali and ubuntu featuring prometheus, grafana, loki, nmap, wireshark,, and bash automation for monitoring, alerting, centralized logging, and self healing infrastructure.

<div align="center">

# 🛡️ Linux Network Operations & Security Monitoring Lab

<p align="center">
  <img src="https://img.shields.io/badge/OS-Kali%20Linux%20%26%20Ubuntu-blue?style=for-the-badge&logo=linux&logoColor=white" />
  <img src="https://img.shields.io/badge/Monitoring-Prometheus%20%7C%20Grafana-E6522C?style=for-the-badge&logo=grafana&logoColor=white" />
  <img src="https://img.shields.io/badge/Logging-Loki%20%7C%20Promtail-F5A623?style=for-the-badge&logo=grafana&logoColor=white" />
  <img src="https://img.shields.io/badge/Security-Suricata%20%7C%20Fail2Ban-DC143C?style=for-the-badge" />
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

A fully functional enterprise-style Linux Network Operations & Security Monitoring Home Lab built end-to-end using open-source tools. Simulates the operational workflows of a real-world NOC, SOC, and DevOps infrastructure platform.

---

## 🏗️ Final Architecture

```
                  ┌────────────────────────────┐
                  │       Kali Linux VM        │
                  │   kali-noc (MONITOR NODE)  │
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
                  │   ubuntu-target (TARGET)   │
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
| Monitor Node (`kali-noc`) | Kali Linux |
| Target Node (`ubuntu-target`) | Ubuntu Server 24.04 LTS |
| Network Type | Host-Only (`vboxnet0`) + NAT |
| Monitoring Stack | Prometheus + Grafana + Alertmanager |
| Logging Stack | Loki + Promtail |
| Security Stack | Suricata IDS + Fail2Ban |
| Automation | Bash + Cron |
| Packet Analysis | Wireshark + tcpdump |

**Internal IPs:**
```
kali-noc        →  192.168.56.10   (MONITOR_NODE)
ubuntu-target   →  192.168.56.20   (TARGET_NODE)
```

---

## 📸 Screenshots

> Add your screenshots below. Recommended: Grafana dashboards, Prometheus targets, Alertmanager, Loki logs, Wireshark captures, Nmap results, Suricata alerts, automation outputs.

| | |
|---|---|
| ![Dashboard 1](assets/screenshots/grafana-dashboard.png) | ![Dashboard 2](assets/screenshots/prometheus-targets.png) |
| *Grafana — System Metrics Dashboard* | *Prometheus — Scrape Targets* |
| ![Dashboard 3](assets/screenshots/alertmanager.png) | ![Dashboard 4](assets/screenshots/loki-logs.png) |
| *Alertmanager — Active Alerts* | *Loki — Centralized Log View* |
| ![Dashboard 5](assets/screenshots/wireshark.png) | ![Dashboard 6](assets/screenshots/nmap-scan.png) |
| *Wireshark — Packet Capture* | *Nmap — Service Enumeration* |
| ![Dashboard 7](assets/screenshots/suricata-alerts.png) | ![Dashboard 8](assets/screenshots/automation-output.png) |
| *Suricata — IDS Alerts* | *Automation — Script Output* |

---

## 📂 Project Phases

| Phase | Title |
|---|---|
| 0 | 🏠 Home Lab Setup |
| 1 | 🐧 Linux Administration |
| 2 | 📊 Infrastructure Monitoring Stack |
| 3 | 🚨 Alerting System |
| 4 | 🌐 Network Analysis & Operations |
| 5 | 🛡️ Centralized Logging & Security Monitoring |
| 6 | 🤖 Automation & Self-Healing Infrastructure |

---

## ⚙️ Phase Details

<details>
<summary><b>🏠 Phase 0 — Home Lab Setup</b></summary>

### Goal
Build the virtual enterprise-style network lab environment using VirtualBox.

### Architecture Diagram

> 📸 Add your Phase 0 lab architecture screenshot here
> `![Phase 0 Architecture](assets/architecture/phase0-lab-setup.png)`

---

### VM Specifications

**VM 1 — Kali Linux (`kali-noc`)**

| Resource | Recommended |
|---|---|
| RAM | 6–8 GB |
| CPU | 2–4 Cores |
| Storage | 50 GB |

Purpose: Monitoring, dashboards, packet analysis, automation, scanning, security analysis.

**VM 2 — Ubuntu Server (`ubuntu-target`)**

| Resource | Recommended |
|---|---|
| RAM | 2–4 GB |
| CPU | 2 Cores |
| Storage | 25 GB |

Purpose: Simulate production server, generate logs, host services, generate traffic.

---

### Step 1 — Create Host-Only Network in VirtualBox

```
VirtualBox → Tools → Network → Create Host-Only Network
```

| Setting | Value |
|---|---|
| Network Name | `vboxnet0` |
| IPv4 Address | `192.168.56.1` |
| Network Mask | `255.255.255.0` |
| DHCP | Optional |

**Adapter config for both VMs:**
- Adapter 1 → NAT *(internet access)*
- Adapter 2 → Host-Only `vboxnet0` *(internal lab communication)*

---

### Step 2 — Install Ubuntu Server

Download: [Ubuntu Server 24.04 LTS](https://ubuntu.com/download/server)

During installation, enable: ✅ **OpenSSH Server**

Create user:
```text
username: labadmin
```

---

### Step 3 — Verify Network Connectivity

On Kali — check IP:
```bash
ip a
# Look for 192.168.56.x
```

On Ubuntu — check IP:
```bash
ip a
# Look for 192.168.56.y
```

Test communication from Kali:
```bash
ping 192.168.56.20
```

✅ If ping succeeds — home lab network is operational.

---

### Step 4 — Enable SSH on Ubuntu Server

```bash
sudo apt update
sudo apt install openssh-server -y
sudo systemctl enable ssh
sudo systemctl start ssh
sudo systemctl status ssh
```

SSH from Kali:
```bash
ssh labadmin@192.168.56.20
```

---

### Step 5 — Basic Server Setup (Both VMs)

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl wget git vim htop net-tools unzip -y
```

Install test services on Ubuntu:
```bash
sudo apt install nginx -y
```

Test from Kali:
```bash
curl http://192.168.56.20
```

✅ If web page appears — target server is operational.

</details>

---

<details>
<summary><b>🐧 Phase 1 — Linux Administration</b></summary>

### Goal
Prepare stable Linux infrastructure for monitoring and operations.

### Architecture Diagram

> 📸 Add your Phase 1 architecture screenshot here
> `![Phase 1 Architecture](assets/architecture/phase1-linux-admin.png)`

<div align="center">

*Linux Administration Layer — kali-noc (MONITOR NODE) connected via SSH to ubuntu-target (TARGET NODE)*

</div>

---

### Step 1 — System Updates

```bash
sudo apt update && sudo apt upgrade -y
```

---

### Step 2 — Install Essential Tools

```bash
sudo apt install curl wget git net-tools htop unzip vim -y
```

---

### Step 3 — Create Project Structure

```bash
mkdir -p ~/monitoring-lab
mkdir -p ~/monitoring-lab/prometheus
mkdir -p ~/monitoring-lab/grafana
mkdir -p ~/monitoring-lab/alertmanager
mkdir -p ~/automation-lab/scripts
mkdir -p ~/automation-lab/logs
mkdir -p ~/automation-lab/reports
```

---

### Step 4 — Key Linux Commands Reference

```bash
# Service management
systemctl status nginx
systemctl enable nginx
systemctl start nginx
systemctl restart nginx

# Process monitoring
ps aux
htop
top

# Network inspection
ss -tulnp          # Show listening ports
netstat -tulnp     # Alternative
ip a               # Show interfaces

# Log monitoring
journalctl -u nginx -f
tail -f /var/log/auth.log
tail -f /var/log/syslog

# File operations
grep "Failed" /var/log/auth.log
awk '{print $1}' /var/log/auth.log
```

---

### Screenshots

> 📸 Add Phase 1 screenshots here
> - SSH session to ubuntu-target
> - htop output
> - systemctl service status

</details>

---

<details>
<summary><b>📊 Phase 2 — Infrastructure Monitoring Stack</b></summary>

### Goal
Build a production-style infrastructure monitoring platform.

**Flow:**
```
ubuntu-target → Node Exporter → Prometheus → Grafana
```

### Architecture Diagram

> 📸 Add your Phase 2 architecture screenshot here
> `![Phase 2 Architecture](assets/architecture/phase2-monitoring-stack.png)`

<div align="center">

*Complete Monitoring & Metrics Workflow — Node Exporter (Port 9100) → Prometheus → Grafana → User/Admin*

</div>

---

### Step 1 — Install Docker on Kali Linux

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install docker.io docker-compose -y
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
```

Verify:
```bash
docker --version
```

---

### Step 2 — Install Node Exporter on Ubuntu Server

```bash
# Download
wget https://github.com/prometheus/node_exporter/releases/latest/download/node_exporter-1.9.1.linux-amd64.tar.gz

# Extract
tar -xvf node_exporter-1.9.1.linux-amd64.tar.gz

# Move binary
sudo mv node_exporter-1.9.1.linux-amd64/node_exporter /usr/local/bin/

# Create dedicated user
sudo useradd -rs /bin/false node_exporter
```

Create systemd service:
```bash
sudo nano /etc/systemd/system/node_exporter.service
```

```ini
[Unit]
Description=Node Exporter
After=network.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target
```

Start and enable:
```bash
sudo systemctl daemon-reload
sudo systemctl enable node_exporter
sudo systemctl start node_exporter
sudo systemctl status node_exporter
```

Verify from Kali:
```bash
curl http://192.168.56.20:9100/metrics
```

---

### Step 3 — Docker Compose (Prometheus + Grafana)

```bash
cd ~/monitoring-lab
nano docker-compose.yml
```

```yaml
version: '3'

services:
  prometheus:
    image: prom/prometheus
    container_name: prometheus
    ports:
      - "9090:9090"
    volumes:
      - ./prometheus/prometheus.yml:/etc/prometheus/prometheus.yml
      - ./prometheus/alerts.yml:/etc/prometheus/alerts.yml
    restart: unless-stopped

  grafana:
    image: grafana/grafana
    container_name: grafana
    ports:
      - "3000:3000"
    restart: unless-stopped
```

---

### Step 4 — Prometheus Configuration

```bash
nano ~/monitoring-lab/prometheus/prometheus.yml
```

```yaml
global:
  scrape_interval: 5s

scrape_configs:
  - job_name: 'ubuntu-server'
    static_configs:
      - targets: ['192.168.56.20:9100']
```

---

### Step 5 — Start Monitoring Stack

```bash
cd ~/monitoring-lab
docker-compose up -d
docker ps
```

Access:
```
Prometheus  →  http://localhost:9090
Grafana     →  http://localhost:3000   (admin / admin)
```

In Grafana: Add Prometheus datasource → URL: `http://prometheus:9090`

Import Node Exporter Full dashboard:
```
Dashboards → Import → ID: 1860
```

---

### Step 6 — Test Monitoring

Generate CPU load on Ubuntu:
```bash
yes > /dev/null
# Watch Grafana CPU spike live
# Stop with CTRL+C
```

---

### Screenshots

> 📸 Add Phase 2 screenshots here
> - Grafana CPU/RAM/Disk dashboard
> - Prometheus targets showing `ubuntu-server = UP`
> - Node Exporter metrics output

</details>

---

<details>
<summary><b>🚨 Phase 3 — Alerting System</b></summary>

### Goal
Create a real-time incident detection and alerting pipeline.

**Flow:**
```
Prometheus → Alert Rules → Alertmanager → Telegram Bot
```

### Architecture Diagram

> 📸 Add your Phase 3 architecture screenshot here
> `![Phase 3 Architecture](assets/architecture/phase3-alerting.png)`

<div align="center">

*Home Monitoring Workflow — ubuntu-target metrics → Prometheus (rule evaluation) → Alertmanager → Telegram Alerts*

</div>

---

### Step 1 — Create Telegram Bot

1. Open Telegram → Search `BotFather`
2. Send `/newbot` and follow prompts
3. Save your `BOT_TOKEN` (e.g. `123456789:ABCxxxxxxxx`)

Get Chat ID — open in browser:
```
https://api.telegram.org/bot<BOT_TOKEN>/getUpdates
```
Save the `chat.id` value.

---

### Step 2 — Update Docker Compose (Add Alertmanager)

```bash
nano ~/monitoring-lab/docker-compose.yml
```

Full `docker-compose.yml`:
```yaml
version: '3'

services:
  prometheus:
    image: prom/prometheus
    container_name: prometheus
    ports:
      - "9090:9090"
    volumes:
      - ./prometheus/prometheus.yml:/etc/prometheus/prometheus.yml
      - ./prometheus/alerts.yml:/etc/prometheus/alerts.yml
    restart: unless-stopped

  grafana:
    image: grafana/grafana
    container_name: grafana
    ports:
      - "3000:3000"
    restart: unless-stopped

  alertmanager:
    image: prom/alertmanager
    container_name: alertmanager
    ports:
      - "9093:9093"
    volumes:
      - ./alertmanager/alertmanager.yml:/etc/alertmanager/alertmanager.yml
    restart: unless-stopped
```

---

### Step 3 — Configure Alertmanager

```bash
nano ~/monitoring-lab/alertmanager/alertmanager.yml
```

```yaml
route:
  receiver: telegram

receivers:
  - name: telegram
    telegram_configs:
      - bot_token: "YOUR_BOT_TOKEN"
        chat_id: YOUR_CHAT_ID
        api_url: "https://api.telegram.org"
```

---

### Step 4 — Create Prometheus Alert Rules

```bash
nano ~/monitoring-lab/prometheus/alerts.yml
```

```yaml
groups:
  - name: linux-alerts

    rules:

      - alert: HighCPUUsage
        expr: 100 - (avg by(instance)(rate(node_cpu_seconds_total{mode="idle"}[2m])) * 100) > 80
        for: 1m
        labels:
          severity: critical
        annotations:
          summary: "High CPU Usage on {{ $labels.instance }}"

      - alert: ServerDown
        expr: up == 0
        for: 1m
        labels:
          severity: critical
        annotations:
          summary: "Server Down: {{ $labels.instance }}"

      - alert: HighMemoryUsage
        expr: (1 - (node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes)) * 100 > 80
        for: 1m
        labels:
          severity: warning
        annotations:
          summary: "High Memory Usage on {{ $labels.instance }}"

      - alert: HighDiskUsage
        expr: (node_filesystem_avail_bytes * 100 / node_filesystem_size_bytes) < 10
        for: 1m
        labels:
          severity: warning
        annotations:
          summary: "Low Disk Space on {{ $labels.instance }}"
```

---

### Step 5 — Update prometheus.yml

```yaml
global:
  scrape_interval: 5s

rule_files:
  - "alerts.yml"

alerting:
  alertmanagers:
    - static_configs:
        - targets:
          - alertmanager:9093

scrape_configs:
  - job_name: 'ubuntu-server'
    static_configs:
      - targets: ['192.168.56.20:9100']
```

---

### Step 6 — Restart Stack & Test

```bash
cd ~/monitoring-lab
docker-compose down
docker-compose up -d
docker ps
```

Verify Alertmanager:
```
http://localhost:9093
```

Trigger CPU alert on Ubuntu:
```bash
sudo apt install stress -y
stress --cpu 2 --timeout 120
```

Test Server Down alert:
```bash
sudo systemctl stop node_exporter
# Wait ~1 minute for ServerDown alert
sudo systemctl start node_exporter
```

Verify alert in Prometheus:
```
http://localhost:9090/alerts
# HighCPUUsage → FIRING
```

---

### Screenshots

> 📸 Add Phase 3 screenshots here
> - Prometheus alerts page showing FIRING state
> - Alertmanager UI
> - Telegram bot receiving alert notification

</details>

---

<details>
<summary><b>🌐 Phase 4 — Network Analysis & Operations</b></summary>

### Goal
Build a professional network analysis and packet inspection environment.

### Architecture Diagram

> 📸 Add your Phase 4 architecture screenshot here
> `![Phase 4 Architecture](assets/architecture/phase4-network-analysis.png)`

<div align="center">

*Network Analysis Architecture — kali-noc using Nmap / tcpdump / Wireshark / curl to scan and capture traffic from ubuntu-target*

</div>

---

### Step 1 — Install Network Analysis Tools

```bash
sudo apt update
sudo apt install -y \
  nmap \
  wireshark \
  tcpdump \
  iftop \
  netcat-openbsd \
  dnsutils \
  traceroute \
  net-tools
```

Verify:
```bash
nmap --version
tcpdump --version
wireshark --version
```

---

### Step 2 — Network Reconnaissance with Nmap

Discover active hosts:
```bash
nmap -sn 192.168.56.0/24
```

Service and version detection:
```bash
nmap -sV 192.168.56.20
```

OS fingerprinting:
```bash
sudo nmap -O 192.168.56.20
```

Full port scan (all 65535 ports):
```bash
nmap -p- 192.168.56.20
```

Aggressive scan (OS + services + scripts + traceroute):
```bash
sudo nmap -A 192.168.56.20
```

Save results to file:
```bash
nmap -sV 192.168.56.20 -oN ~/scan_results.txt
```

Expected output:
```
22/tcp   open  ssh
80/tcp   open  http
9100/tcp open  node_exporter
```

---

### Step 3 — Packet Capture with tcpdump

Capture all traffic:
```bash
sudo tcpdump -i any
```

Capture HTTP traffic only:
```bash
sudo tcpdump -i any port 80
```

Capture SSH traffic only:
```bash
sudo tcpdump -i any port 22
```

Save packets to file:
```bash
sudo tcpdump -i any -w ~/capture.pcap
# Stop with CTRL+C
```

---

### Step 4 — Generate Test Traffic

On Ubuntu (start HTTP server):
```bash
python3 -m http.server 8080
```

From Kali (generate traffic):
```bash
curl http://192.168.56.20:8080
```

Capture simultaneously:
```bash
sudo tcpdump -i any port 8080 -w ~/http_capture.pcap
```

---

### Step 5 — Traffic Analysis with Wireshark

Launch Wireshark:
```bash
sudo wireshark
```

Select interface: `eth0` or `enp0s3` or host-only adapter.

Key display filters:

| Filter | Purpose |
|---|---|
| `http` | HTTP web traffic |
| `dns` | DNS query traffic |
| `tcp.port == 22` | SSH encrypted traffic |
| `icmp` | Ping / ICMP traffic |
| `ip.addr == 192.168.56.20` | All traffic to/from target |

---

### Step 6 — Live Bandwidth Monitoring

```bash
sudo iftop
```

---

### Step 7 — Manual Network Testing with Netcat

Create TCP listener on Ubuntu:
```bash
nc -lvnp 4444
```

Connect from Kali:
```bash
nc 192.168.56.20 4444
```

---

### Screenshots

> 📸 Add Phase 4 screenshots here
> - Nmap scan results showing open ports
> - tcpdump live capture output
> - Wireshark packet capture with filters applied
> - iftop bandwidth view

</details>

---

<details>
<summary><b>🛡️ Phase 5 — Centralized Logging & Security Monitoring</b></summary>

### Goal
Build a mini-SIEM with centralized log aggregation and security dashboards.

**Flow:**
```
ubuntu-target logs → Promtail → Loki → Grafana
```

### Architecture Diagram

> 📸 Add your Phase 5 architecture screenshot here
> `![Phase 5 Architecture](assets/architecture/phase5-logging.png)`

<div align="center">

*Centralized Logging Pipeline — ubuntu-target (syslog / auth.log / nginx logs) → Promtail → Loki → Grafana dashboards*

</div>

---

### Step 1 — Add Loki to Docker Compose

```bash
nano ~/monitoring-lab/docker-compose.yml
```

Add to services:
```yaml
  loki:
    image: grafana/loki:latest
    container_name: loki
    ports:
      - "3100:3100"
    command: -config.file=/etc/loki/local-config.yaml
    restart: unless-stopped
```

---

### Step 2 — Install Promtail on Ubuntu Server

```bash
# Download
wget https://github.com/grafana/loki/releases/latest/download/promtail-linux-amd64.zip

# Install unzip
sudo apt install unzip -y

# Extract and install
unzip promtail-linux-amd64.zip
chmod +x promtail-linux-amd64
sudo mv promtail-linux-amd64 /usr/local/bin/promtail
```

---

### Step 3 — Configure Promtail

```bash
sudo nano /etc/promtail-config.yml
```

```yaml
server:
  http_listen_port: 9080

positions:
  filename: /tmp/positions.yaml

clients:
  - url: http://192.168.56.10:3100/loki/api/v1/push

scrape_configs:
  - job_name: system_logs
    static_configs:
      - targets:
          - localhost
        labels:
          job: varlogs
          host: ubuntu-server
          __path__: /var/log/*.log

  - job_name: auth_logs
    static_configs:
      - targets:
          - localhost
        labels:
          job: auth
          host: ubuntu-server
          __path__: /var/log/auth.log
```

---

### Step 4 — Create Promtail Systemd Service

```bash
sudo nano /etc/systemd/system/promtail.service
```

```ini
[Unit]
Description=Promtail Service
After=network.target

[Service]
Type=simple
ExecStart=/usr/local/bin/promtail -config.file=/etc/promtail-config.yml

[Install]
WantedBy=multi-user.target
```

Start Promtail:
```bash
sudo systemctl daemon-reload
sudo systemctl enable promtail
sudo systemctl start promtail
sudo systemctl status promtail
```

---

### Step 5 — Restart Docker Stack & Connect Loki to Grafana

```bash
cd ~/monitoring-lab
docker-compose down
docker-compose up -d
```

In Grafana (`http://localhost:3000`):
```
Settings → Data Sources → Add data source → Loki
URL: http://loki:3100
Save & Test
```

---

### Step 6 — Loki Query Reference

Explore logs in Grafana → Explore → Select Loki datasource.

| Query | Purpose |
|---|---|
| `{job="auth"}` | All authentication logs |
| `{job="auth"} \|= "Failed password"` | Failed SSH login attempts |
| `{job="auth"} \|= "Accepted password"` | Successful SSH logins |
| `{job="auth"} \|= "sudo"` | Sudo usage events |
| `{job="auth"} \|= "ssh"` | All SSH activity |
| `{job="varlogs"} \|= "error"` | Nginx / service errors |

---

### Step 7 — Generate Security Events for Testing

Simulate failed SSH logins from Kali:
```bash
ssh fakeuser@192.168.56.20
# Enter wrong password 5+ times
```

Monitor logs live on Ubuntu:
```bash
sudo tail -f /var/log/auth.log
```

---

### Step 8 — Install Fail2Ban on Ubuntu Server

```bash
sudo apt install fail2ban -y
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
sudo systemctl status fail2ban
```

Verify protection:
```bash
sudo fail2ban-client status
sudo fail2ban-client status sshd
```

---

### Step 9 — Security Dashboard Panels

Create dashboards in Grafana for:

| Panel | Loki Query |
|---|---|
| Failed SSH Logins (Line Chart) | `{job="auth"} \|= "Failed password"` |
| Successful Logins (Bar Chart) | `{job="auth"} \|= "Accepted password"` |
| Sudo Usage | `{job="auth"} \|= "sudo"` |
| Service Errors | `{job="varlogs"} \|= "error"` |
| All SSH Events | `{job="auth"} \|= "ssh"` |

---

### Screenshots

> 📸 Add Phase 5 screenshots here
> - Grafana Loki explorer showing auth logs
> - Security dashboard with SSH failure charts
> - Fail2Ban client status output
> - Live auth.log tail with failed password entries

</details>

---

<details>
<summary><b>🤖 Phase 6 — Automation & Self-Healing Infrastructure</b></summary>

### Goal
Automate infrastructure operations and enable self-healing services.

**Flow:**
```
Cron Scheduler → Bash Scripts → Service Recovery / Scan Results / Alert Notifications
```

### Architecture Diagram

> 📸 Add your Phase 6 architecture screenshot here
> `![Phase 6 Architecture](assets/architecture/phase6-automation.png)`

<div align="center">

*Infrastructure Automation Flow — Cron Scheduler → Automation Scripts (Health Checks / Auto Restart / Backup / Nmap Scans) → Monitor Node & Target Node*

</div>

---

### Step 1 — Setup Passwordless SSH (Required for Automation)

On Kali — generate SSH key:
```bash
ssh-keygen
# Press Enter for all defaults
```

Copy key to Ubuntu:
```bash
ssh-copy-id labadmin@192.168.56.20
```

On Ubuntu — allow passwordless sudo for nginx restart:
```bash
sudo visudo
```

Add this line:
```text
labadmin ALL=(ALL) NOPASSWD: /bin/systemctl restart nginx
```

---

### Step 2 — Create Project Structure

```bash
mkdir -p ~/automation-lab/scripts
mkdir -p ~/automation-lab/logs
mkdir -p ~/automation-lab/reports
```

---

### Step 3 — Script: Service Health Monitor (Self-Healing)

```bash
nano ~/automation-lab/scripts/service_monitor.sh
```

```bash
#!/bin/bash

REMOTE_USER="labadmin"
REMOTE_HOST="192.168.56.20"
SERVICE="nginx"
LOGFILE=~/automation-lab/logs/service_monitor.log

STATUS=$(ssh $REMOTE_USER@$REMOTE_HOST "systemctl is-active $SERVICE")

if [ "$STATUS" != "active" ]
then
    echo "$(date) - $SERVICE was DOWN on $REMOTE_HOST. Restarting..." >> $LOGFILE
    ssh $REMOTE_USER@$REMOTE_HOST "sudo systemctl restart $SERVICE"
    echo "$(date) - $SERVICE restarted successfully on $REMOTE_HOST." >> $LOGFILE
else
    echo "$(date) - $SERVICE healthy on $REMOTE_HOST." >> $LOGFILE
fi
```

Make executable:
```bash
chmod +x ~/automation-lab/scripts/service_monitor.sh
```

Test — stop nginx on Ubuntu:
```bash
sudo systemctl stop nginx
```

Run from Kali:
```bash
~/automation-lab/scripts/service_monitor.sh
```

Verify recovery:
```bash
cat ~/automation-lab/logs/service_monitor.log
```

Expected:
```
Mon May 26 12:00:00 - nginx was DOWN on 192.168.56.20. Restarting...
Mon May 26 12:00:02 - nginx restarted successfully on 192.168.56.20.
```

---

### Step 4 — Script: Automated Nmap Network Scan

```bash
nano ~/automation-lab/scripts/network_scan.sh
```

```bash
#!/bin/bash

DATE=$(date +"%Y-%m-%d_%H-%M")
TARGET="192.168.56.20"
LOGFILE=~/automation-lab/logs/network_scan.log
OUTPUT=~/automation-lab/reports/scan_$DATE.txt

echo "$(date) - Starting Nmap scan on $TARGET..." >> $LOGFILE
nmap -sV $TARGET > $OUTPUT
echo "$(date) - Scan completed. Saved to $OUTPUT" >> $LOGFILE
```

```bash
chmod +x ~/automation-lab/scripts/network_scan.sh
```

---

### Step 5 — Script: Automated Packet Capture

```bash
nano ~/automation-lab/scripts/packet_capture.sh
```

```bash
#!/bin/bash

DATE=$(date +"%Y-%m-%d_%H-%M")
LOGFILE=~/automation-lab/logs/packet_capture.log
OUTPUT=~/automation-lab/reports/capture_$DATE.pcap

sudo tcpdump -i any -w $OUTPUT -c 100
echo "$(date) - Packet capture saved to $OUTPUT" >> $LOGFILE
```

```bash
chmod +x ~/automation-lab/scripts/packet_capture.sh
```

---

### Step 6 — Script: Log Cleanup

```bash
nano ~/automation-lab/scripts/log_cleanup.sh
```

```bash
#!/bin/bash

LOGFILE=~/automation-lab/logs/cleanup.log

find ~/automation-lab/logs -type f -mtime +7 -delete
echo "$(date) - Old logs cleaned." >> $LOGFILE
```

```bash
chmod +x ~/automation-lab/scripts/log_cleanup.sh
```

---

### Step 7 — Schedule All Tasks with Cron

```bash
crontab -e
```

```bash
# Health check every 5 minutes
*/5 * * * * ~/automation-lab/scripts/service_monitor.sh

# Daily Nmap scan at 8:00 AM
0 8 * * * ~/automation-lab/scripts/network_scan.sh

# Daily packet capture at 9:00 AM
0 9 * * * ~/automation-lab/scripts/packet_capture.sh

# Weekly log cleanup every Sunday at midnight
0 0 * * 0 ~/automation-lab/scripts/log_cleanup.sh
```

---

### Step 8 — Send Automation Logs to Loki

```bash
sudo nano /etc/promtail-config.yml
```

Add this job:
```yaml
  - job_name: automation_logs
    static_configs:
      - targets:
          - localhost
        labels:
          job: automation
          host: kali-linux
          __path__: /home/kali/automation-lab/logs/*.log
```

Restart Promtail:
```bash
sudo systemctl restart promtail
```

---

### Step 9 — Automation Dashboard Panels in Grafana

Open: `http://localhost:3000` → Create New Dashboard

| Panel | Loki Query | Purpose |
|---|---|---|
| Service Restart Events | `{job="automation"} \|= "restarted"` | Auto-healing activity |
| Network Scan History | `{job="automation"} \|= "Nmap scan"` | Scan execution tracking |
| Disk Cleanup Events | `{job="automation"} \|= "logs cleaned"` | Storage maintenance |
| Packet Capture Events | `{job="automation"} \|= "Packet capture"` | PCAP generation history |
| Failed Services | `{job="automation"} \|= "DOWN"` | Infrastructure failures |
| Health Status | `{job="automation"} \|= "healthy"` | System health trends |

---

### Screenshots

> 📸 Add Phase 6 screenshots here
> - Crontab configuration
> - service_monitor.sh log output showing auto-recovery
> - Grafana automation dashboard
> - network_scan.sh report output

</details>

---

## 🛠️ Tool Reference

| Tool | Purpose |
|---|---|
| Prometheus | Metrics collection & storage |
| Grafana | Dashboard visualization |
| Alertmanager | Alert routing & Telegram notifications |
| Node Exporter | Linux system metrics exporter |
| Loki | Centralized log aggregation |
| Promtail | Log shipping agent |
| Suricata | Intrusion Detection System |
| Fail2Ban | Brute-force attack prevention |
| Nmap | Network scanning & service discovery |
| Wireshark | GUI packet analysis |
| tcpdump | CLI packet capture |
| Docker Compose | Containerized service deployment |
| Bash + Cron | Scripting & scheduled automation |
| Netcat | Manual TCP/UDP network testing |

---

## 🧠 Skills Demonstrated

`Linux Administration` · `Infrastructure Monitoring` · `Prometheus` · `Grafana` · `Docker`
`Network Analysis` · `Packet Inspection` · `TCP/IP` · `Nmap` · `Wireshark` · `tcpdump`
`Centralized Logging` · `Loki` · `SIEM Fundamentals` · `Intrusion Detection` · `Fail2Ban`
`Bash Scripting` · `Cron Automation` · `Self-Healing Infrastructure` · `DevOps` · `SRE`

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

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://linkedin.com/in/inesh-singh-negi)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/Inesh1)

---

<div align="center">

⭐ **If this project helped you, consider leaving a star!**

</div>
