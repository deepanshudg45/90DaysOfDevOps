# Linux Cheat Sheet – Day 3

A practical Linux command reference focused on **process management**,  
**file system operations**, and **network troubleshooting**.

---

## 🧠 Process Management

### Process Monitoring & Inspection

| Command | Explanation |
|------|------|
| `ps aux` | Displays all running processes with CPU, memory usage, and owner details |
| `top` | Shows real-time process activity and system resource usage |
| `htop` | Interactive and more readable version of `top` (if installed) |
| `pstree` | Displays running processes in a parent-child tree format |


### Process Control

| Command | Explanation |
|------|------|
| `kill <PID>` | Sends a termination signal to gracefully stop a process |
| `kill -9 <PID>` | Forcefully kills a process that does not respond |
| `pkill <name>` | Terminates processes by name instead of PID |
| `nice -n 10 cmd` | Starts a process with lower CPU priority |
| `renice -n 5 <PID>` | Changes priority of an already running process |
| `nohup cmd &` | Runs a command in background even after logout |


### Service Management (systemd)

| Command | Explanation |
|------|------|
| `systemctl status <service>` | Shows current state and health of a service |
| `systemctl start <service>` | Starts a stopped service |
| `systemctl restart <service>` | Restarts a service to apply changes |
| `systemctl enable <service>` | Enables service to start on system boot |
| `journalctl -u <service>` | Displays logs for a specific service |

---

## 📁 File System

### File & Directory Management

| Command | Explanation |
|------|------|
| `ls -lah` | Lists files with permissions, size, and hidden files |
| `cd <path>` | Changes the current working directory |
| `pwd` | Prints the full path of the current directory |
| `mkdir <dir>` | Creates a new directory |
| `touch <file>` | Creates an empty file or updates timestamp |
| `cp <src> <dst>` | Copies files or directories |
| `mv <src> <dst>` | Moves or renames files or directories |
| `rm -rf <dir>` | Deletes files or directories recursively (dangerous) |


### File Content Viewing & Search

| Command | Explanation |
|------|------|
| `cat <file>` | Displays file contents directly to the terminal |
| `less <file>` | Views large files safely with scroll support |
| `head -n 10 <file>` | Shows the first lines of a file |
| `tail -f <file>` | Continuously displays new file entries (logs) |
| `grep "text" <file>` | Searches for matching text inside files |
| `find <path> -name "*.log"` | Finds files by name and path |
| `awk '{print $1}' <file>` | Extracts columns from text |
| `sed 's/old/new/g' <file>` | Performs text substitution |


### Permissions & Ownership

| Command | Explanation |
|------|------|
| `chmod 644 <file>` | Changes file permission mode |
| `chown user:group <file>` | Changes file owner and group |


### Disk Usage & Monitoring

| Command | Explanation |
|------|------|
| `df -h` | Shows disk space usage by filesystem |
| `du -sh <dir>` | Displays total size of a directory |
| `lsof` | Lists open files and associated processes |

---

## 🌐 Networking Commands

| Command | Explanation |
|------|------|
| `ping <host>` | Tests basic network connectivity |
| `ip addr` | Displays IP addresses and interfaces |
| `ip route` | Shows system routing table |
| `curl <url>` | Sends HTTP requests to test APIs or services |
| `ss -tulnp` | Displays listening ports and services |
| `dig <domain>` | Performs DNS lookups |
| `traceroute <host>` | Shows network path to destination |
| `tcpdump -i eth0` | Captures live network traffic |
| `nmap <host>` | Scans open ports on a target |
| `nc -zv <host> <port>` | Checks if a TCP port is reachable |

---

## 📝 Notes
- Prefer `ip` and `ss` over deprecated tools like `ifconfig` and `netstat`
- Avoid `kill -9` unless the process is unresponsive
- These commands are **daily-use tools in production environments**

---

🎯 **Goal:** Build confidence and muscle memory with core Linux commands.
