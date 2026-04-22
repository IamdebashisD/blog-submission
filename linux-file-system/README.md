# 🧠 Linux File System Investigation

A deep dive into how Linux actually works under the hood — exploring system behavior through its file system instead of commands.

> “Everything is a file” — this investigation proves it.

---
## URI
Click on this 👉: [Everything is a File: Hunting Through the Linux File System](https://linux-file-system-hunting-beginner.hashnode.dev/everything-is-a-file-hunting-through-the-linux-file-system)

## 📌 Overview

This project is a field exploration of key Linux system components like:

- Process internals
- Networking stack
- Authentication systems
- Resource control
- Device handling

Instead of using high-level tools, the focus is on **reading kernel-exposed files** to understand real system behavior.

---

## 🔍 Key Findings

### 1. `/etc/nsswitch.conf`
Controls how Linux resolves names (DNS, users, groups).  
Defines lookup order → `files dns` means local first, then DNS.

---

### 2. `/proc/self`
A dynamic view of the current process.  
Reveals memory layout, limits, and open file descriptors.

---

### 3. `cgroups` (`/sys/fs/cgroup`)
Kernel-level resource control (CPU, memory, PIDs).  
Foundation of Docker & Kubernetes.

---

### 4. `/proc/net`
Live networking data:
- TCP connections
- Interface stats
- Kernel parameters (e.g., `ip_forward`)

---

### 5. `/dev`
Devices exposed as files:
- `/dev/null` → discard output  
- `/dev/urandom` → randomness  
- `/dev/pts` → terminal sessions  

---

### 6. `/etc/passwd` & `/etc/shadow`
Separation of identity and authentication.  
Improves security using restricted access.

---

### 7. `/etc/login.defs`
Defines UID/GID ranges and password policies.

---

### 8. `/proc/mounts`
Actual mounted filesystems (not planned like `/etc/fstab`).  
Useful for understanding system architecture and security.

---

### 9. PAM (`/etc/pam.d/`)
Authentication layer used by login, SSH, sudo.  
Centralized and modular security policies.

---

### 10. `/proc/net/route`
Kernel routing table (in hex).  
Defines how packets leave the system.

---

## 🧩 Key Takeaways

- Linux exposes internal state via files  
- Kernel behavior can be inspected in real time  
- Tools like `netstat`, `ip`, `top` = wrappers over these files  
- Security = file permissions + controlled access  
- Containers = cgroups + namespaces + filesystem isolation  

---

## 🚀 Final Thought

Understanding the Linux file system is the fastest way to understand Linux itself.






