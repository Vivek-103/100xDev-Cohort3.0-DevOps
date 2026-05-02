# Domains vs IPs

## localhost

"Localhost" refers to the computer you're currently working on. It's essentially a loopback address that points to the machine itself, allowing it to communicate with itself over a network. In technical terms, the IP address for localhost is usually `127.0.0.1` for IPv4, or `::1` for IPv6.

## ping command

- Try running

```solidity
ping localhost
```

- Now try pinging google

```solidity
ping google.com
```

Notice google points to a different `IP address` .

### **IP (Internet Protocol) Address:**

- An **IP address** is a unique string of numbers that identifies a device on a network, like the internet. Think of it like a **house address**: it's how computers (or any devices on the network) know where to send information.
- For example, `192.168.1.1` is an IP address.
- An **IP address** is essential for routing data on the internet, but it's not the most human-friendly system.

### Domain name

- A **domain name** is the readable, human-friendly address we use to access websites, like `google.com` or `example.org`.
- Domains are a higher-level abstraction that makes it easier for us to remember websites instead of trying to recall a string of numbers (like an IP address).
- For instance, when you type `www.google.com` into your browser, your computer looks up that domain name and finds the corresponding IP address, then connects to the website.

## Domain name vs Phone number



## Limited IP addresses

There are limited number of IP addresses in the world (ipv4 specially). So it’s not very easy for us to get a public IP. Most IPs are blocked by cloud providers or Big companies (JIO)

# Local network, routing (mild hosting)

If you have multiple laptops on the same `wifi router`, you can access one machine from another by using their private IP address. This is a `mild` version of deploying your app on your `local network` (or whats called the intranet)

## Steps to follow

1. Start a node.js process locally on port 3000

```solidity
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello, World!');
});

app.listen(port, () => {
  console.log(`Server is running on http://localhost:${port}`);
});
```
1. Find the IP of your machine on the local network

```solidity
ifconfig or ipconfig
```
## Hosts file

You can override what your domain name resolves to by overriding the hosts file.
vi /etc/hosts
127.0.0.01	harkirat.100xdevs.com

# How to deploy apps (actual hosting)?

1. Renting servers on a cloud
2. Rending compute yourself in datacenters
3. Self hosting (buying a CPU rack in your house)
4. Serverless providers
5. Cloud native options (k8s)


# What is a VM
VMs run on a physical server (called the **host**) but are abstracted through a layer of virtualization software called a **hypervisor** (e.g., VMware, KVM). This hypervisor divides the host machine’s resources (CPU, memory, storage) into separate virtual machines.

Each VM acts like a completely independent machine, even though they share the underlying hardware. You can run different operating systems and applications in different VMs on the same physical server.

VMs are highly flexible and easy to scale. You can quickly spin up, modify, or delete VMs, and you can consolidate multiple workloads on a single server.
The virtualization layer introduces a slight overhead in terms of performance because the hypervisor needs to manage resources and ensure each VM operates independently. However, with modern hypervisors and powerful hardware, this overhead is minimal.

# Bare metal servers

n a bare-metal setup, an operating system (OS) runs directly on the physical hardware without a hypervisor in between. There’s no virtualization layer.

 Since there's no hypervisor, bare-metal systems tend to offer better performance, as the OS can directly access all the server’s resources without sharing them with other instances. This is especially important for high-performance applications like large databases, gaming servers, or mining crypto

With bare-metal, you’re typically limited to the resources (CPU, memory, storage) of the actual physical server. You can't dynamically allocate resources like you can in a VM.

# SSH protocol, password based auth

The **SSH protocol** (Secure Shell) is a cryptographic network protocol that allows secure communication between two systems, typically for remote administration. It’s most commonly used to log into remote servers and execute commands, but it also facilitates secure file transfers and other operations.

### Key Features of SSH:

1. **Encryption**: SSH encrypts the data that’s sent between the client and the server, so even if someone intercepts the connection, they can’t read the data. This makes it much more secure than older protocols like Telnet or FTP, which transmit data in plaintext.
2. **Authentication**: SSH can use two methods of authentication:
    - **Password-based**: You enter a password to authenticate yourself to the remote system.
    - **Public Key-based**: A more secure method, where the client uses a private key to authenticate, and the server checks it against the corresponding public key. This eliminates the need for passwords and provides an extra layer of security.
3. **Integrity**: SSH ensures the integrity of data, meaning that data cannot be tampered with while it’s in transit. If someone tries to alter the data being sent, the connection will be immediately disrupted.

## Password based

While setting up a server, select password based authentication