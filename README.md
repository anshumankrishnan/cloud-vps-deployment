🚀 FINAL README.md (FULL DETAILED VERSION)

```markdown
# 🛠️ Production Server Incident Recovery (DevOps Project)

---

## 📌 Project Overview

This project simulates a real-world **DevOps Production Environment** where a Linux server is:

- Deployed on AWS EC2 (Ubuntu 22.04)
- Running containerized applications using Docker
- Configured with Nginx reverse proxy
- Intentionally broken to simulate real production incidents
- Debugged and recovered using Linux troubleshooting techniques
- Secured using firewall and intrusion prevention tools
- Monitored using Netdata
- Backed up using automated scripts

---

## 🎯 Project Objective

The main goal of this project is to simulate a **real production incident environment** and demonstrate:

- Linux system administration
- Docker troubleshooting
- Nginx debugging and recovery
- Infrastructure failure analysis
- Security hardening
- Monitoring setup
- Backup and recovery strategies

---

## ☁️ Cloud Environment

- AWS EC2 (Free Tier)
- Ubuntu Server 22.04 LTS
- t2.micro instance

---

## 🛠️ Tools & Technologies Used

| Tool | Purpose |
|------|--------|
| AWS EC2 | Cloud server hosting |
| Ubuntu Linux | Operating system |
| Docker | Container runtime |
| Docker Compose | Multi-container orchestration |
| Nginx | Web server & reverse proxy |
| Netdata | System monitoring |
| Fail2Ban | Intrusion prevention |
| UFW Firewall | Network security |
| Git & GitHub | Version control |
| Bash Scripts | Automation |

---

## 🏗️ System Architecture

```

Internet
↓
AWS EC2 (Ubuntu Server)
↓
Nginx Reverse Proxy
↓
Docker Containers
├── Nginx App Container (Port 3000)
└── Redis Container

````

---

## 🚀 Deployment Steps

### 🟢 1. AWS EC2 Setup
- Ubuntu 22.04 instance launched
- Security group configured (SSH, HTTP, HTTPS, 3000, 19999)

---

### 🟢 2. Docker Installation

```bash
curl -fsSL https://get.docker.com | sh
sudo apt install docker-compose -y
````

---

### 🟢 3. Application Deployment

Created `docker-compose.yml`:

```yaml
services:
  app:
    image: nginx
    ports:
      - "3000:80"

  redis:
    image: redis
```

---

### 🟢 4. Start Services

```bash
docker compose up -d
```

---

### 🟢 5. Verify Running Containers

```bash
docker ps
```

---

### 🟢 6. Access Application

```
http://<EC2-PUBLIC-IP>:3000
```

---

## 🔥 Incident Simulation (Breaking Production System)

The following failures were intentionally introduced:

### ❌ Container Failure

```bash
docker stop <container_id>
```

### ❌ Disk Space Exhaustion

```bash
fallocate -l 5G largefile.img
```

### ❌ Log Flooding

```bash
yes "ERROR" >> spam.log
```

### ❌ Broken Nginx Configuration

Added invalid configuration in Nginx file.

---

## 🧪 Troubleshooting & Recovery

### 🔍 System Diagnosis

```bash
htop
df -h
systemctl --failed
```

---

### 🐳 Docker Debugging

```bash
docker ps -a
docker logs <container_id>
docker inspect <container_id>
```

---

### 🔧 Fix Docker Services

```bash
docker compose up -d
```

---

### 🌐 Fix Nginx Configuration

```bash
sudo nginx -t
sudo systemctl restart nginx
```

Correct configuration:

```nginx
server {
    listen 80;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

---

### 🧹 Cleanup System

```bash
rm spam.log
rm largefile.img
docker system prune -a
```

---

## 📊 Monitoring Setup

Installed Netdata for real-time monitoring:

```bash
bash <(curl -Ss https://my-netdata.io/kickstart.sh)
```

Access dashboard:

```
http://<EC2-PUBLIC-IP>:19999
```

---

## 🔐 Security Hardening

### Firewall Configuration

```bash
sudo ufw allow OpenSSH
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable
```

---

### Fail2Ban Installation

```bash
sudo apt install fail2ban -y
```

---

### Disable Root Login

```bash
PermitRootLogin no
```

Restart SSH:

```bash
sudo systemctl restart ssh
```

---

## 💾 Backup Strategy

### Backup Script

```bash
#!/bin/bash
DATE=$(date +%Y-%m-%d-%H-%M)
tar -czf backup-$DATE.tar.gz production-app
```

---

### Run Backup

```bash
chmod +x backup.sh
./backup.sh
```

---

## 📸 Screenshots Included

* AWS EC2 Dashboard
* Running Docker Containers
* Broken System State
* Recovery Process
* Netdata Monitoring Dashboard
* Final Working Application

---

## 🧠 Key Learnings

* AWS EC2 instance management
* Linux system troubleshooting
* Docker container lifecycle
* Nginx reverse proxy configuration
* Production incident debugging
* Security hardening techniques
* Real-world DevOps workflows

---

## 📌 Project Outcome

✔ Server deployed successfully
✔ Application containerized and running
✔ Incident simulation completed
✔ System recovered successfully
✔ Monitoring enabled
✔ Security configured
✔ Backup system implemented

---

## 👨‍💻 Author

**Anshuman Krishnan**
DevOps & Cloud Computing Enthusiast

---

## 🏁 Conclusion

This project demonstrates a complete **production-grade DevOps workflow**, including deployment, failure simulation, debugging, recovery, monitoring, and security hardening on a cloud-based Linux server.
 

 
