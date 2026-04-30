# 🌐 NGINX — Complete Deep Dive (Theory + Practical + Production Guide)

---

# 📌 1. What is NGINX?

**NGINX** (pronounced *“engine-x”*) is a high-performance:

* Web Server
* Reverse Proxy
* Load Balancer
* API Gateway

Originally created by Igor Sysoev, it is designed to handle **high concurrency with low resource usage**.

---

# ⚡ 2. Why NGINX is So Powerful

### 🔥 Key Strengths:

* Event-driven architecture (non-blocking)
* Handles thousands of concurrent connections
* Low memory footprint
* High throughput

---

# 🧠 3. NGINX Architecture

## 🔹 Event-Driven Model

Unlike traditional servers (like Apache), NGINX uses:

* **Asynchronous, non-blocking I/O**
* **Worker processes** instead of threads

### 🧩 Components:

* **Master Process**

  * Reads config
  * Manages workers
* **Worker Processes**

  * Handle requests
  * Event loop-based

---

## 🔄 Flow of Request

```text
Client → NGINX → (Static OR Proxy) → Backend → Response → Client
```

---

# 📂 4. NGINX Installation

### Ubuntu:

```bash
sudo apt update
sudo apt install nginx
```

### Start:

```bash
sudo systemctl start nginx
```

### Enable:

```bash
sudo systemctl enable nginx
```

### Check:

```bash
nginx -v
```

---

# 📁 5. Directory Structure

| Path                          | Purpose        |
| ----------------------------- | -------------- |
| `/etc/nginx/nginx.conf`       | Main config    |
| `/etc/nginx/sites-available/` | Virtual hosts  |
| `/etc/nginx/sites-enabled/`   | Active configs |
| `/var/www/html`               | Default root   |
| `/var/log/nginx/`             | Logs           |

---

# ⚙️ 6. NGINX Configuration Basics

## 🔹 Main Config Structure

```nginx
events {}

http {
    server {
        listen 80;

        location / {
            root /var/www/html;
            index index.html;
        }
    }
}
```

---

## 🔹 Key Blocks

| Block      | Purpose             |
| ---------- | ------------------- |
| `events`   | Connection settings |
| `http`     | Web traffic         |
| `server`   | Virtual host        |
| `location` | Route handling      |

---

# 🌍 7. Serving Static Content

```nginx
server {
    listen 80;
    server_name example.com;

    location / {
        root /var/www/html;
        index index.html;
    }
}
```

---

# 🔁 8. Reverse Proxy

## 🔹 Concept

Forward requests to backend server.

```nginx
server {
    listen 80;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

---

## 🔹 Important Headers

```nginx
proxy_set_header Host $host;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
```

---

# ⚖️ 9. Load Balancing

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

## 🔹 Algorithms:

* Round Robin (default)
* Least Connections
* IP Hash

---

# 🔐 10. SSL / HTTPS Setup

Using Certbot:

```bash
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx
```

---

## 🔹 Manual SSL Config

```nginx
server {
    listen 443 ssl;

    ssl_certificate /path/fullchain.pem;
    ssl_certificate_key /path/privkey.pem;
}
```

---

# ⚡ 11. Caching

```nginx
proxy_cache_path /cache levels=1:2 keys_zone=my_cache:10m;

location / {
    proxy_cache my_cache;
    proxy_pass http://backend;
}
```

---

# 🛡️ 12. Security Features

## 🔹 Rate Limiting

```nginx
limit_req_zone $binary_remote_addr zone=limit:10m rate=10r/s;

location / {
    limit_req zone=limit;
}
```

---

## 🔹 Block IP

```nginx
deny 192.168.1.1;
```

---

## 🔹 Hide Server Info

```nginx
server_tokens off;
```

---

# 🧩 13. Virtual Hosts (Multiple Websites)

```nginx
server {
    listen 80;
    server_name site1.com;
}

server {
    listen 80;
    server_name site2.com;
}
```

---

# 🔄 14. URL Rewriting

```nginx
rewrite ^/old$ /new permanent;
```

---

# 📡 15. Compression (GZIP)

```nginx
gzip on;
gzip_types text/plain application/json;
```

---

# 🧠 16. Logging

## 🔹 Access Log:

```bash
/var/log/nginx/access.log
```

## 🔹 Error Log:

```bash
/var/log/nginx/error.log
```

---

# 🐳 17. NGINX with Docker

```Dockerfile
FROM nginx
COPY nginx.conf /etc/nginx/nginx.conf
```

Run:

```bash
docker build -t nginx-custom .
docker run -p 80:80 nginx-custom
```

---

# ☸️ 18. NGINX in Kubernetes

* Used via **Ingress Controller**
* Acts as cluster reverse proxy

---

# 🚀 19. Performance Tuning

```nginx
worker_processes auto;

events {
    worker_connections 1024;
}
```

---

## 🔹 Optimization Tips:

* Enable caching
* Use gzip
* Tune worker connections
* Use CDN

---

# 🔥 20. Real Production Architecture

```text
User
 ↓
Cloudflare (CDN)
 ↓
NGINX (Reverse Proxy + SSL)
 ↓
App Server (Node.js)
 ↓
Database (MongoDB)
```

---

# 🧪 21. Testing Config

```bash
nginx -t
```

Reload:

```bash
sudo systemctl reload nginx
```

---

# 🔄 22. Zero Downtime Reload

```bash
nginx -s reload
```

---

# ⚠️ 23. Common Errors

| Error           | Cause            |
| --------------- | ---------------- |
| 502 Bad Gateway | Backend down     |
| 403 Forbidden   | Permission issue |
| 404 Not Found   | Wrong path       |

---

# 🧠 24. Interview Questions

### Q1: Why NGINX over Apache?

* Event-driven vs thread-based
* Better performance under load

### Q2: What is upstream?

* Backend server pool

### Q3: What is reverse proxy?

* Forward requests to backend

---

# 📊 25. NGINX vs Apache

| Feature      | NGINX        | Apache       |
| ------------ | ------------ | ------------ |
| Architecture | Event-driven | Thread-based |
| Performance  | High         | Moderate     |
| Static files | Faster       | Slower       |

---

# 🧰 26. Advanced Use Cases

* API Gateway
* Microservices routing
* WebSocket handling
* Rate limiting APIs

---

# 🔐 27. Best Practices

* Use HTTPS everywhere
* Enable caching
* Monitor logs
* Secure headers
* Use load balancing

---

