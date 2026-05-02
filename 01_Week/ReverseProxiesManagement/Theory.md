# Reverse Proxies Management and Deployment — Theory Guide

---

## 📌 1. What is a Reverse Proxy?

A **reverse proxy** is a server that sits between clients (users) and backend servers, forwarding client requests to appropriate backend services and returning responses.

### 🔁 Flow:

Client → Reverse Proxy → Backend Server → Reverse Proxy → Client

### 📊 Key Difference:

| Type          | Direction         | Purpose       |
| ------------- | ----------------- | ------------- |
| Forward Proxy | Client → Internet | Hides client  |
| Reverse Proxy | Internet → Server | Hides backend |

---

## ⚙️ 2. Why Use Reverse Proxies?

### 🔹 Core Benefits:

* **Load Balancing** → Distribute traffic across servers
* **Security** → Hide backend IPs
* **SSL Termination** → Handle HTTPS centrally
* **Caching** → Improve performance
* **Compression** → Reduce bandwidth
* **Routing** → Direct requests based on URL/path

---

## 🧠 3. Popular Reverse Proxy Tools

* **NGINX**
* **HAProxy**
* **Apache HTTP Server**
* **Traefik**
* **Caddy**

---

## 🔧 4. Architecture of Reverse Proxy

### Basic Setup:

```
Client → Reverse Proxy → App Servers (Node.js / Django / Java)
```

### Advanced Setup:

```
Client
   ↓
Load Balancer
   ↓
Reverse Proxy Layer
   ↓
Microservices (API / DB / Cache)
```

---

## 🚀 5. NGINX Reverse Proxy Configuration

### Install NGINX:

```bash
sudo apt update
sudo apt install nginx
```

### Basic Config:

```nginx
server {
    listen 80;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

### Reload:

```bash
sudo systemctl restart nginx
```

---

## ⚖️ 6. Load Balancing in Reverse Proxy

### Types:

* Round Robin (default)
* Least Connections
* IP Hash

### Example:

```nginx
upstream backend {
    server 192.168.1.10;
    server 192.168.1.11;
}

server {
    location / {
        proxy_pass http://backend;
    }
}
```

---

## 🔐 7. SSL Termination

### Purpose:

* Offload HTTPS from backend servers

### Setup:

```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx
```

---

## ⚡ 8. Caching & Performance

```nginx
proxy_cache_path /data/nginx/cache levels=1:2 keys_zone=my_cache:10m;

location / {
    proxy_cache my_cache;
    proxy_pass http://backend;
}
```

---

## 🛡️ 9. Security Features

* Rate limiting
* IP blocking
* WAF integration
* Headers protection

```nginx
limit_req_zone $binary_remote_addr zone=limit:10m rate=10r/s;
```

---

## 🧩 10. Reverse Proxy in Microservices

* API Gateway pattern
* Service discovery integration
* Container environments (Docker + Kubernetes)

---

## 🐳 11. Deployment with Docker

### Dockerfile:

```Dockerfile
FROM nginx
COPY nginx.conf /etc/nginx/nginx.conf
```

### Run:

```bash
docker build -t reverse-proxy .
docker run -p 80:80 reverse-proxy
```

---

## ☸️ 12. Kubernetes Ingress (Reverse Proxy)

* Acts as reverse proxy inside cluster
* Managed via Ingress Controller

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
```

---

# ☁️ AWS Overview

## 📌 What is AWS?

**Amazon Web Services (AWS)** is a cloud platform providing computing, storage, networking, and deployment services.

---

## 🧰 Core AWS Services

### 1. Compute

* EC2 (Virtual Servers)
* Lambda (Serverless)

### 2. Storage

* S3 (Object Storage)
* EBS (Block Storage)

### 3. Networking

* VPC (Virtual Private Cloud)
* Route 53 (DNS)

### 4. Deployment

* Elastic Beanstalk
* ECS / EKS

---

## 💡 Key Functions

* On-demand scalability
* Pay-as-you-go pricing
* Global infrastructure
* High availability

---

## 🖥️ Renting Servers (EC2)

### Steps:

1. Go to AWS Console
2. Launch EC2 instance
3. Choose:

   * OS (Ubuntu/Linux)
   * Instance type (t2.micro)
4. Configure security group (open ports 22, 80)
5. Download key pair (.pem)

---

## 💰 Pricing Concept

* Pay per hour/second
* Free tier available
* Reserved vs On-demand pricing

---

# 🔑 SSH (Secure Shell) — Complete Guide

## 📌 What is SSH?

SSH is a protocol used to securely connect to remote machines over a network.

---

## 🔐 Key Concepts

### 1. SSH Keys

* Public key → Server
* Private key → Local machine

### Generate Keys:

```bash
ssh-keygen -t rsa -b 4096
```

---

## 🔌 Connect to Server

```bash
ssh -i key.pem ubuntu@your-ip
```

---

## 📂 File Transfer

### SCP:

```bash
scp file.txt ubuntu@ip:/home/
```

### Rsync:

```bash
rsync -avz file ubuntu@ip:/home/
```

---

## ⚙️ SSH Config File

```bash
~/.ssh/config
```

Example:

```
Host myserver
    HostName 192.168.1.10
    User ubuntu
    IdentityFile key.pem
```

---

## 🔒 Security Best Practices

* Disable password login
* Use SSH keys only
* Change default port (22)
* Use fail2ban
* Limit users

---

## 🧠 SSH Agent

```bash
eval "$(ssh-agent -s)"
ssh-add key.pem
```

---

## 🔄 Port Forwarding

### Local:

```bash
ssh -L 8080:localhost:80 user@host
```

### Remote:

```bash
ssh -R 8080:localhost:80 user@host
```

---

## 🧪 Debugging SSH

```bash
ssh -v user@host
```

---

# ✅ Summary

This guide covered:

* Reverse Proxy fundamentals & deployment
* NGINX configuration and scaling
* Docker & Kubernetes integration
* AWS basics and EC2 setup
* Complete SSH usage and security

---
