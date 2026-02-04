# Day-05 Linux Troubleshooting Runbook

## Target service / process

* **Service:** docker
* **Main process:** dockerd (PID 358)
* **Environment:** Ubuntu 24.04.1 LTS on WSL2

---

## Environment basics

### uname

```bash
uname -a
Linux LAPTOP-BVJ1PIP 6.6.87.2-microsoft-standard-WSL2 x86_64 GNU/Linux
```

**Observation:** Running on WSL2 kernel; behavior differs slightly from bare-metal Linux (IO, networking).

### OS release

```bash
lsb_release -a
cat /etc/os-release
```

**Observation:** Ubuntu 24.04.1 LTS (Noble). Supported and stable.

---

## Filesystem sanity

```bash
mkdir /tmp/runbook-demo
cp /etc/hosts /tmp/runbook-demo/hosts-copy-file
ls -l /tmp/runbook-demo
```

**Observation:** Filesystem writable, permissions normal, no IO errors.

---

## Snapshot: CPU & Memory

### top

```bash
top
```

**Observation:**

* Load average ~0.02
* dockerd using ~0.3% CPU
* Plenty of idle CPU

### Process usage

```bash
ps -o pid,pcpu,pmem,comm -p $(pidof dockerd)
```

**Observation:** dockerd ~0.9% memory, negligible CPU.

### Memory availability

```bash
free -h
```

**Observation:**

* 7.5Gi total RAM
* ~6.8Gi available
* Swap unused → no memory pressure

---

## Snapshot: Disk & IO

### Disk usage

```bash
df -h
```

**Observation:**

* Root filesystem ~1% used
* Host Windows disk mounted at /mnt/c ~78% used (not critical for Linux FS)
* Snap mounts show 100% usage (normal for snapfs)

### Log directory size

```bash
sudo du -sh /var/log
```

**Observation:** ~384MB logs. Acceptable, but rotation should be monitored.

### IO stats

```bash
iostat
vmstat 1 5
dstat -cdnm
```

**Observation:**

* IO wait ~0%
* CPU mostly idle
* No disk contention or swap activity

---

## Snapshot: Network

### Listening sockets

```bash
sudo ss -lx | grep docker
```

**Observation:**

* dockerd listening only on Unix sockets
* No exposed TCP ports (good security posture)

### Docker API health

```bash
curl --unix-socket /var/run/docker.sock http://localhost/_ping
```

**Observation:** Docker API responds with `OK`.

---

## Logs reviewed

### Docker service logs

```bash
journalctl -u docker -n 50
```

**Observation:**

* Successful startup
* Repeated warnings about CDI setup and containerd events
* No crash loop

### System logs

```bash
tail -n 50 /var/log/syslog
```

**Observation:**

* Frequent WSL-related warnings (Windows agent connectivity)
* Not directly related to docker health

---

## Quick findings

* System is healthy and idle
* dockerd resource usage is normal
* Disk, memory, and IO show no pressure
* Docker warnings are known WSL/CDI related and non-fatal

---

## If this worsens (next steps)

1. **Containment**

   ```bash
   systemctl restart docker
   ```

2. **Deeper diagnostics**

   ```bash
   docker stats
   dockerd --debug
   ```

3. **Root cause analysis**

   * Inspect container logs
   * Enable higher log verbosity
   * Capture `strace` on dockerd if CPU spikes

---

**Status:** Runbook complete and reusable for on-call troubleshooting.
