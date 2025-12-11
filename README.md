 🛰️ NetWatch — Lightweight System & Service Monitoring for Linux

NetWatch is a modular, Bash-based monitoring framework designed to keep critical Linux systems healthy and responsive. It continuously tracks CPU load, memory and swap usage, disk capacity, directory integrity, remote server availability, and local services—while automatically logging results and sending email alerts when problems occur.

NetWatch is simple, fast, and dependency-light, making it ideal for personal servers, homelabs, development machines, and lightweight production environments.



 🚀 Key Features

* CPU, Memory, and Disk Monitoring
  Periodically scans system resource usage with configurable warning/critical thresholds.

* Service & Process Watchdog
  Detects crashed services using `pgrep` and can automatically restart them using `systemctl`, `service`, or `/etc/init.d`.

* Remote Server Checks
  Supports both ping and TCP port checks using `nc` (with fallback support). Alerts you if any server becomes unreachable.

* Directory Integrity Tracking
  Uses MD5 hashes to detect unexpected file modifications or additions within important directories.

* Smart Interval System (Timers)
  Each check uses independent timers to avoid overloading the system and prevent repeated notifications.

* Email Alerting (with Throttling)
  Sends warnings and critical alerts to your configured email address. Supports custom email commands or standard `mail`.

* Readable System Summary Output
  Running `./netwatch.sh all` prints a clean health overview of your entire system.

* Config-Driven Architecture
  Everything is controlled via:

  * `netwatch.conf` — thresholds, intervals, email settings
  * `server.list` — servers/IPs to monitor
  * `proc.list` — processes or services to track
  * `dir.list` — directories to checksum for integrity



 🧩 How It Works

NetWatch is built around one core script: **`netwatch.sh`**, which can be executed directly or sourced by smaller wrapper scripts. Each module (CPU, memory, disk, etc.) generates cached output, logs events with timestamps, and triggers alerts only when needed.

The project follows a clean directory layout:

```
~/netwatch/
  ├── config/
  │     ├── netwatch.conf
  │     ├── server.list
  │     ├── proc.list
  │     └── dir.list
  ├── cache/
  ├── timers/
  ├── logs/
  └── netwatch.sh
```

This keeps monitoring state, cached snapshots, and logs neatly separated.

---

 📄 Example Summary Output

```
 NETWATCH SUMMARY 
CPU:
CPU usage sample (calculated): 7%

MEMORY:
Output of free -m -t
...

DISK:
Output of df -h
...

SERVERS:
192.168.1.10:22

SERVICES:
service nginx not running

Logs: ~/netwatch/logs/netwatch.log



Perfect for users who want control without complexity.

---
