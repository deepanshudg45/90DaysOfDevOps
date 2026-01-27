# 1. Core Components of Linux

Linux is a free and open-source operating system known for its stability, security, and flexibility. It is widely used in servers, cloud platforms, development environments, and embedded systems. Linux is designed to handle multiple users and processes efficiently, making it a strong choice for both personal and enterprise use.

At its core, Linux follows a well-structured architecture where each component has a specific role. Understanding these core components helps explain how Linux manages hardware, runs applications, and maintains system reliability.


## 1. Kernel – The Heart of Linux

The kernel is the core of the Linux operating system. It is always running and controls everything in the system.

### What the kernel does:
- Manages CPU scheduling
- Controls memory (RAM)
- Handles processes
- Communicates with hardware using device drivers
- Prevents conflicts between running programs

Linux uses a **monolithic kernel**, which means most services run inside the kernel for better performance.

**Example:**  
When you open a file, the kernel finds the data on disk, loads it into memory, and sends it to the application.


## 2. User Space – Where Applications Run

User space is where normal programs execute.

It includes:
- Applications (vim, docker, chrome)
- Shells (bash, zsh)
- System utilities (ls, ps, top)
- System libraries (glibc)

Programs in user space cannot directly access hardware. They must request the kernel.

**Why this matters:**  
If an application crashes, the kernel remains safe and the system continues running.


## 3. System Libraries – The Middle Layer

System libraries help applications interact with the kernel without knowing its internal details.

### Key points:
- Provide reusable functions
- Reduce developer effort
- Improve portability across Linux systems

The most important system library is **glibc**.

**Example flow:**
printf() → system library → kernel → terminal


## 4. Shell – Communicating with Linux

The shell is a command-line interface, not the operating system itself.

### What the shell does:
- Accepts user commands
- Interprets them
- Sends requests to the kernel

Common shells:
- bash
- zsh
- sh

**Example:**  
Typing `ls` asks the kernel to read directory contents and display them.


## 5. init / systemd – The System Starter

When Linux boots, the kernel starts **systemd**, which runs as **PID 1**.

### systemd responsibilities:
- Starting system services (SSH, Docker, Network)
- Mounting filesystems
- Managing system shutdown and reboot
- Handling logs

Without systemd, the system would boot but no services would start.


## 6. Hardware Layer – Physical Components

This layer includes:
- CPU
- RAM
- Storage devices
- Network interfaces
- Input and output devices

Hardware is accessed only through kernel drivers. Applications never interact with hardware directly.

---

## 7. System Utilities – Admin Tools

System utilities are small programs used to manage and monitor the system.

### Common uses:
- User management
- System monitoring
- Disk and network management
- Software installation

Examples:
- `df` – disk usage
- `ip` – network configuration
- `ps` – process status
- `mount` – filesystem mounting

---

# Applications of Linux Operating System

### 1. Servers and Hosting

### 2. Software Development

### 3. Desktop and Personal Use

### 4. Cybersecurity and Ethical Hacking

### 5. Embedded Systems

---

# 2. How Processes Are Created and Managed

A process is an instance of a running program.

## Process Creation
1. A parent process creates a new process using `fork()`
2. The child process loads a program using `exec()`
3. The kernel assigns:
   - Process ID (PID)
   - Memory
   - CPU time

**Example:**  
The shell creates a process to run the `ls` command.


## Process States

Linux processes can be in the following states:

- **Running (R)** – currently executing on CPU
- **Sleeping (S)** – waiting for input or I/O
- **Stopped (T)** – paused by user or signal
- **Zombie (Z)** – finished execution but not cleaned up
- **Uninterruptible (D)** – waiting for disk I/O

Zombie processes do not consume CPU, but many zombies indicate poor process management.


## Daily Linux Commands (DevOps)

- `systemctl status <service>` – check if a service is running or failing
- `journalctl -xe` – view detailed system and service logs
- `df -h` – check disk space usage
- `free -h` – check memory usage
- `ip a` – check network interfaces and IP addresses

---

# Q3. What systemd Does and Why It Matters

## What systemd Does
systemd is the init system and service manager used by modern Linux distributions.

It:
- Starts services in the correct order
- Restarts failed services
- Manages background tasks
- Collects logs using `journald`


## Why systemd Is Important
- Faster boot times
- Better service dependency handling
- Easier system administration
- Essential for modern cloud servers


## Common systemd Commands

- systemctl status <service>
- systemctl start/stop/restart <service name>
- systemctl enable <service>
- journalctl -xe


## Conclusion

Understanding these core Linux components helps in system administration, cloud computing, and DevOps roles. These concepts form the foundation of how Linux works internally.



