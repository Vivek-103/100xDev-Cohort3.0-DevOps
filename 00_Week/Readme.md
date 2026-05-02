# 🐧 Bash Guide (Linux & Windows)

A complete guide to understanding and using **Bash (Bourne Again Shell)** across Linux and Windows environments — from basics to advanced scripting.

---

## 📌 What is Bash?

**Bash (Bourne Again Shell)** is a command-line shell and scripting language used for:

* Interacting with the operating system
* Automating tasks
* Managing files and processes

It is the default shell in most Linux distributions.

---

## 🖥️ Bash on Linux

### 🔹 Opening Bash

Bash is the default terminal in most Linux systems.

```bash
echo "Hello, World!"
```

---

### 🔹 Basic Commands

| Command | Description             |
| ------- | ----------------------- |
| `pwd`   | Print current directory |
| `ls`    | List files              |
| `cd`    | Change directory        |
| `mkdir` | Create directory        |
| `rm`    | Remove files            |
| `cp`    | Copy files              |
| `mv`    | Move/rename files       |
| `cat`   | Display file content    |

---

### 🔹 File Permissions

```bash
chmod +x script.sh
```

---

### 🔹 Environment Variables

```bash
echo $HOME
export NAME="Vivek"
```

---

## 🪟 Bash on Windows

Bash is not native to Windows, but you can use it via:

* **Windows Subsystem for Linux (WSL)**
* **Git Bash**
* **Cygwin**

---

### 🔹 Using WSL

```bash
wsl
```

Install Ubuntu:

```bash
wsl --install
```

---

### 🔹 Using Git Bash

Right-click → "Git Bash Here"

---

## 🧠 Bash Scripting Basics

### 🔹 Create a Script

```bash
#!/bin/bash
echo "Hello, Bash!"
```

Save as `script.sh`

Run:

```bash
chmod +x script.sh
./script.sh
```

---

### 🔹 Variables

```bash
name="Vivek"
echo "Hello $name"
```

---

### 🔹 Conditionals

```bash
if [ $name == "Vivek" ]; then
  echo "Welcome!"
fi
```

---

### 🔹 Loops

```bash
for i in 1 2 3
do
  echo $i
done
```

---

## 🚀 Advanced Bash Topics

### 🔹 Functions

```bash
greet() {
  echo "Hello $1"
}

greet Vivek
```

---

### 🔹 Command Substitution

```bash
current_date=$(date)
echo $current_date
```

---

### 🔹 Pipes & Redirection

```bash
ls -l | grep ".txt"
echo "Hello" > file.txt
```

---

### 🔹 Process Management

```bash
ps
kill <pid>
top
```

---

### 🔹 Cron Jobs (Automation)

```bash
crontab -e
```

Example:

```bash
0 9 * * * /path/to/script.sh
```

---

## ⚡ Advanced Tools & Enhancements

### 🔹 Shell Improvements

* **Zsh** – more features than Bash
* **Oh My Zsh** – customization & plugins

---

### 🔹 Terminal Multiplexing

* **tmux** – split terminals, sessions

---

### 🔹 Package Managers

* `apt` (Ubuntu)
* `yum` (RHEL/CentOS)
* `pacman` (Arch)

---

## 🧪 Debugging Bash Scripts

```bash
bash -x script.sh
```

---

## 📚 Best Practices

* Use meaningful variable names
* Always quote variables: `"${var}"`
* Handle errors properly
* Keep scripts modular

---

## 🎯 Summary

* Bash is essential for Linux and DevOps workflows
* On Windows, use WSL or Git Bash
* Start with commands → move to scripting → master automation

--

