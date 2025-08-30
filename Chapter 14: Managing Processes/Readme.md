# ⚙️ Managing Processes 

Linux treats every task as a **process**. Managing processes ensures efficient use of system resources and stability.

## 📌 Process Types

* **Foreground Process** → Runs in the terminal until completed.
* **Background Process** → Runs in the background with `&`.
* **Daemon** → Background service (e.g., `sshd`).
* **Zombie Process** → Finished execution but still in process table.
* **Orphan Process** → Parent terminated, adopted by `init/systemd`.

## 🔄 Process Lifecycle

1. Created (fork/exec)
2. Running
3. Waiting (I/O, resources)
4. Terminated (exit)

## 📊 Monitoring Processes

* `ps aux` → Show all processes.
* `top` / `htop` → Real-time monitoring.
* `pstree` → Hierarchical process tree.
* `pgrep name` → Find PID by process name.

---

##  Viewing Processes

### `ps` (Process Status)

The `ps` command shows information about active processes.

```bash
# Show processes for the current user
ps

# Show all processes with full details
ps -ef

# Show processes in a tree structure
ps -ejH
```

Example output:

```
UID   PID  PPID  C STIME TTY          TIME CMD
root     1     0  0 Aug28 ?        00:00:04 systemd
root     2     0  0 Aug28 ?        00:00:00 kthreadd
```

---

### `top` (Real-time Process Monitoring)

`top` displays running processes dynamically.

```bash
top
```

Inside `top`:

* `k` → Kill a process
* `r` → Renice (change priority)
* `q` → Quit

---

### `htop` (Enhanced top)

If installed, `htop` gives a more user-friendly interface.

```bash
htop
```

---


## ⏱️ Job Control

* Run process in background: `command &`
* Bring to foreground: `fg %1`
* Resume background job: `bg %1`
* List jobs: `jobs`

## 📉 Priorities & Scheduling

* `nice -n 10 command` → Start process with priority.
* `renice -n 5 -p PID` → Change priority of running process.

---

##  Controlling Processes

### Starting a Process

```bash
# Run a program in the foreground
firefox

# Run a program in the background
firefox &
```

### Checking Background Jobs

```bash
jobs
```

### Bringing Job to Foreground

```bash
fg %1
```

### Sending Job to Background

```bash
bg %1
```

---

## ❌ Killing Processes

* `kill -9 PID` → Force kill.
* `pkill processname` → Kill by name.
* `killall processname` → Kill all instances.

---

## 🛠️ Systemd & Services

* `systemctl start service` → Start service.
* `systemctl stop service` → Stop service.
* `systemctl restart service` → Restart service.
* `systemctl status service` → Service status.

---

##  Killing Processes

### `kill`

Kill a process by PID.

```bash
# Find PID
ps -ef | grep firefox

# Kill process with PID
kill 1234

# Force kill
kill -9 1234
```

### `pkill`

Kill by process name.

```bash
pkill firefox
```

### `killall`

Kill all instances of a process.

```bash
killall firefox
```

---

##  Process Priorities

Each process has a **priority** that determines CPU scheduling.

### `nice` (Start process with priority)

```bash
# Start process with lower priority (10)
nice -n 10 firefox
```

### `renice` (Change priority of running process)

```bash
# Change priority of PID 1234 to -5
renice -5 -p 1234
```

---

##  Daemons and Services

System services are managed via **systemd**.

```bash
# List all services
systemctl list-units --type=service

# Start a service
sudo systemctl start ssh

# Stop a service
sudo systemctl stop ssh

# Enable service to start on boot
sudo systemctl enable ssh
```

---

##  Monitoring Resource Usage

### `top` or `htop`

Check CPU and memory usage.

### `pidstat`

Monitor statistics per process.

```bash
pidstat 1
```

### `pmap`

Show memory usage of a process.

```bash
pmap 1234
```

---

##  Example Workflow

1. Start a process in the background:

   ```bash
   sleep 500 &
   ```

2. Check running processes:

   ```bash
   ps -ef | grep sleep
   ```

3. Kill the process:

   ```bash
   kill -9 <PID>
   ```

4. Verify it’s gone:

   ```bash
   ps -ef | grep sleep
   ```

---
