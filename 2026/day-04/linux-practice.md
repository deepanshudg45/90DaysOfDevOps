# Day 04 – Linux Practice: Processes and Services

## Objective
The goal of Day 04 was to **practice Linux fundamentals hands-on** by working with:
- Running processes
- systemd-managed services
- System and service logs

This task focuses on **observation and troubleshooting basics**, not theory.

---

## What I Practiced

### 🔹 Process Inspection
I practiced identifying and monitoring running processes to understand:
- What is running on the system
- How processes consume CPU and memory
- How services map to multiple processes

**Commands used:**
- `ps`
- `ps aux`
- `top`
- `pgrep nginx`

Screenshots of command outputs are attached for reference.

---

### 🔹 Service Inspection (systemd)
I inspected a real system service to understand how Linux manages long-running applications.

**Service inspected:** `nginx`

**Commands used:**
- `systemctl status nginx`
- `systemctl list-units --type=service --state=running`

This helped me understand:
- Service state (active/running)
- Main PID vs worker processes
- How systemd tracks services using cgroups

Screenshots are attached to show actual service status and running services.

---

### 🔹 Log Inspection
I practiced checking logs to understand how Linux records system and service activity.

**Commands used:**
- `journalctl -u docker`
- `tail -n 50 /var/log/auth.log`

From logs, I observed:
- Service startup messages
- Warnings and informational logs
- Authentication events and sudo usage

These commands are critical for real-world troubleshooting.

---

## Mini Troubleshooting Flow Practiced

When a service is not working, I followed this basic flow:

1. **Check if the process exists**
   ```bash
   pgrep <service>
2. **Check service status**
    ```bash
    systemctl status <service>
3. **Check recent logs**
    ```bash
    journalctl -u <service> --since "15 minutes ago"
4. **Check system load**
   ```bash
   top

This approach avoids guesswork and focuses on facts.

## Command Output & Reference

All command executions, outputs, and CLI screenshots from this practice session are documented and explained in detail in the Medium blog linked below.

👉 Medium Blog – Day 04 Linux Practice (Commands, Outputs & Observations):
<https://medium.com/@gahatorideepwork/90daysofdevops-day-04-f0124c807a25>
