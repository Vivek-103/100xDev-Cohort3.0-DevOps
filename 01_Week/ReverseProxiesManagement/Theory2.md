# 🐧 Ubuntu Bash Commands & AWS EC2 Automation — Complete README

---

# 📌 1. Introduction

This guide provides:

* Essential **Bash commands (Ubuntu/Linux)**
* Practical **system administration workflows**
* **AWS EC2 automation using Bash**
* Real-world DevOps usage patterns

---

# 🧠 2. Bash Basics

## 🔹 What is Bash?

**Bash (Bourne Again Shell)** is a command-line interpreter used to interact with Linux systems.

---

## 🔹 Command Syntax

```bash
command [options] [arguments]
```

Example:

```bash
ls -l /home
```

---

# 📂 3. File & Directory Commands

| Command          | Description                  |
| ---------------- | ---------------------------- |
| `pwd`            | Show current directory       |
| `ls`             | List files                   |
| `ls -la`         | Show hidden files            |
| `cd <dir>`       | Change directory             |
| `mkdir <dir>`    | Create directory             |
| `rmdir <dir>`    | Remove empty directory       |
| `rm -rf <dir>`   | Delete directory recursively |
| `cp file1 file2` | Copy file                    |
| `mv file1 file2` | Move/rename                  |
| `touch file.txt` | Create file                  |

---

# 📖 4. File Viewing & Editing

| Command           | Purpose         |
| ----------------- | --------------- |
| `cat file`        | Display content |
| `less file`       | Scroll view     |
| `head -n 10 file` | First 10 lines  |
| `tail -n 10 file` | Last 10 lines   |
| `nano file`       | Edit file       |
| `vim file`        | Advanced editor |

---

# 🔍 5. Search & Filters

| Command             | Use              |
| ------------------- | ---------------- |
| `find / -name file` | Find file        |
| `grep "text" file`  | Search text      |
| `grep -r "text" .`  | Recursive search |
| `locate file`       | Fast search      |

---

# ⚙️ 6. Permissions & Ownership

```bash
chmod 755 file
chmod +x script.sh
chown user:user file
```

| Permission | Meaning |
| ---------- | ------- |
| 7          | rwx     |
| 6          | rw-     |
| 5          | r-x     |

---

# 🔄 7. Process Management

| Command         | Description         |
| --------------- | ------------------- |
| `ps aux`        | List processes      |
| `top`           | Real-time processes |
| `htop`          | Enhanced top        |
| `kill <pid>`    | Kill process        |
| `kill -9 <pid>` | Force kill          |

---

# 📦 8. Package Management (APT)

```bash
sudo apt update
sudo apt upgrade
sudo apt install nginx
sudo apt remove nginx
```

---

# 🌐 9. Networking Commands

| Command           | Use                |
| ----------------- | ------------------ |
| `ifconfig`        | Network info       |
| `ip a`            | IP address         |
| `ping google.com` | Check connectivity |
| `curl url`        | Fetch data         |
| `wget url`        | Download           |

---

# 🧾 10. Disk & Memory

| Command    | Use         |
| ---------- | ----------- |
| `df -h`    | Disk usage  |
| `du -sh *` | Folder size |
| `free -h`  | RAM usage   |

---

# 🔁 11. Pipes & Redirection

```bash
ls | grep txt
echo "Hello" > file.txt
cat file.txt >> file2.txt
```

---

# 🧠 12. Environment Variables

```bash
echo $HOME
export NAME=Vivek
```

---

# 📜 13. Bash Scripting Basics

## Example Script:

```bash
#!/bin/bash

echo "Hello World"
```

Run:

```bash
chmod +x script.sh
./script.sh
```

---

# 🔁 14. Control Flow

```bash
if [ $a -gt 10 ]; then
  echo "Greater"
else
  echo "Smaller"
fi
```

### Loops:

```bash
for i in {1..5}; do
  echo $i
done
```

---

# ☁️ 15. AWS EC2 + Bash Automation

## 🔹 What is EC2?

Amazon EC2 = Virtual Server in cloud.

---

## 🚀 16. Connect to EC2

```bash
ssh -i key.pem ubuntu@your-ip
```

---

## ⚙️ 17. Basic Server Setup Script

```bash
#!/bin/bash

sudo apt update -y
sudo apt upgrade -y

# Install NGINX
sudo apt install nginx -y

# Start service
sudo systemctl start nginx
sudo systemctl enable nginx
```

---

## 📦 18. Deploy Node App via Bash

```bash
#!/bin/bash

# Install Node.js
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs

# Clone repo
git clone https://github.com/your-repo.git
cd your-repo

# Install dependencies
npm install

# Start app
node index.js
```

---

## 🔄 19. Automating with User Data Script

When launching EC2:

Paste script in **User Data**

```bash
#!/bin/bash
apt update -y
apt install docker.io -y
systemctl start docker
docker run -d -p 80:80 nginx
```

---

# 🐳 20. Docker via Bash

```bash
sudo apt install docker.io
sudo docker run hello-world
sudo docker ps
```

---

# 🔐 21. SSH Commands (Quick Recap)

```bash
ssh-keygen
ssh -i key.pem ubuntu@ip
scp file.txt ubuntu@ip:/home/
```

---

# 🧪 22. Logs & Debugging

```bash
journalctl -u nginx
tail -f /var/log/syslog
```

---

# 🔄 23. Cron Jobs (Automation)

```bash
crontab -e
```

Example:

```bash
0 2 * * * /home/backup.sh
```

---

# 📊 24. Real DevOps Workflow Example

```bash
#!/bin/bash

echo "Deploying app..."

git pull origin main
npm install
pm2 restart app

echo "Deployment done!"
```

---

# 🧠 25. Tips & Best Practices

* Always use `sudo` carefully
* Avoid `rm -rf /`
* Use SSH keys instead of passwords
* Monitor logs regularly
* Automate repetitive tasks

---

