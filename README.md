# OSS Audit — Git
### Open Source Software Capstone Project | VITyarthi

---

**Student Name:** Abhay Raj  
**Registration Number:** 24BAI10391
**Chosen Software:** Git (Version Control System)  
**Course:** Open Source Software (NGMC)

---

## About This Project

This repository holds the five shell scripts I submitted for the **Open Source Audit** capstone project. Each script reflects hands-on Linux and shell scripting practice, while tying back to the philosophy and ecosystem of **Git** — the open-source version control system Linus Torvalds built in 2005.

---

## Repository Structure

```
oss-audit-[rollnumber]/
│
├── README.md                          ← This file
│
└── scripts/
    ├── script1_system_identity.sh     ← Script 1: System Identity Report
    ├── script2_package_inspector.sh   ← Script 2: FOSS Package Inspector
    ├── script3_disk_auditor.sh        ← Script 3: Disk and Permission Auditor
    ├── script4_log_analyzer.sh        ← Script 4: Log File Analyzer
    └── script5_manifesto_generator.sh ← Script 5: Open Source Manifesto Generator
```

---

## Environment Setup

### Requirements

- A Linux system (Ubuntu 20.04+ / Debian / RHEL / Fedora / any modern distro)
- Bash shell (version 4.0 or higher — standard on all modern Linux)
- Git installed (`sudo apt install git` or `sudo dnf install git`)
- Basic utilities: `uname`, `whoami`, `du`, `df`, `ls`, `grep` (come pre-installed on virtually all Linux systems)

### Check your Bash version

```bash
bash --version
```

### Make all scripts executable

Once you've cloned the repo, run this once to grant execute permissions:

```bash
chmod +x scripts/*.sh
```

---

## Scripts — Description and Usage

---

### Script 1: System Identity Report

**File:** `scripts/script1_system_identity.sh`

**What it does:**  
Prints a formatted welcome screen with the Linux distro name, kernel version, currently logged-in user, home directory, system uptime, date/time, and the open-source license covering the OS.

**Key concepts:** Variables, `echo`, command substitution `$()`, `/etc/os-release` parsing, output formatting.

**Run it:**

```bash
bash scripts/script1_system_identity.sh
```

**Expected output:**  
A neatly formatted system identity report in the terminal.

---

### Script 2: FOSS Package Inspector

**File:** `scripts/script2_package_inspector.sh`

**What it does:**  
Checks whether `git` (or any other specified package) is installed. Prints version, license, and summary info. A `case` statement adds a short philosophy note for each recognised open-source package.

**Key concepts:** `if-then-else`, `case` statement, `dpkg`/`rpm` queries, pipe with `grep`.

**Run it:**

```bash
bash scripts/script2_package_inspector.sh
```

**To inspect a different package**, just change the `PACKAGE` variable at the top of the script:

```bash
PACKAGE="vlc"    # or firefox, python3, mysql, etc.
```

---

### Script 3: Disk and Permission Auditor

**File:** `scripts/script3_disk_auditor.sh`

**What it does:**  
Iterates over a set of key system directories (`/etc`, `/var/log`, `/home`, `/usr/bin`, `/tmp`, and Git's doc directory) and reports permissions, owner, group, and disk usage for each. Also checks for Git's global and system-level config files.

**Key concepts:** `for` loop, array iteration, `ls -ld`, `du -sh`, `awk`, `cut`, conditional directory checks.

**Run it:**

```bash
bash scripts/script3_disk_auditor.sh
```

**Note:** Directories like `/var/log` may need `sudo` for accurate sizes:

```bash
sudo bash scripts/script3_disk_auditor.sh
```

---

### Script 4: Log File Analyzer

**File:** `scripts/script4_log_analyzer.sh`

**What it does:**  
Takes a log file path and an optional keyword as arguments. Reads through the file line by line, counts how many lines match the keyword (case-insensitive), and prints a summary along with the last 5 matching lines. There's also a retry prompt if the file isn't found.

**Key concepts:** `while read` loop, `if-then`, counter variables, `$1`/`$2` arguments, `grep`, `tail`, retry loop.

**Run it:**

```bash
# Default keyword is "error"
bash scripts/script4_log_analyzer.sh /var/log/syslog

# Custom keyword
bash scripts/script4_log_analyzer.sh /var/log/syslog "warning"

# On systems using journald (no /var/log/syslog):
bash scripts/script4_log_analyzer.sh /var/log/kern.log

# Quick test with a sample log file:
echo -e "INFO: system started\nERROR: disk full\nWARNING: low memory\nERROR: connection refused" > /tmp/test.log
bash scripts/script4_log_analyzer.sh /tmp/test.log error
```

---

### Script 5: Open Source Manifesto Generator

**File:** `scripts/script5_manifesto_generator.sh`

**What it does:**  
Asks three interactive questions and then builds a personalised open-source philosophy statement from the answers. The result is saved to `manifesto_<username>.txt` and also printed to the terminal.

**Key concepts:** `read` for user input, string concatenation, file redirection (`>` and `>>`), `date`, input validation with `while`.

**Run it:**

```bash
bash scripts/script5_manifesto_generator.sh
```

Answer the three prompts — your manifesto will be saved as `manifesto_<yourusername>.txt` in the current directory.

---

## Dependencies

| Dependency | Purpose | Pre-installed? |
|------------|---------|----------------|
| `bash` | Run all scripts | Yes (all Linux) |
| `git` | Script 2 package check | Install if needed |
| `uname` | Kernel version (Script 1) | Yes |
| `whoami` | Username (Scripts 1, 5) | Yes |
| `dpkg` / `rpm` | Package info (Script 2) | Depends on distro |
| `du`, `ls`, `df` | Disk/permission info (Script 3) | Yes |
| `grep`, `tail` | Log analysis (Script 4) | Yes |
| `date` | Timestamp (Script 5) | Yes |

---

## Tested On

- Ubuntu 22.04 LTS (bash 5.1)
- Debian 11 (bash 5.1)
- Fedora 39 (bash 5.2)

---

## Academic Integrity

All scripts are my own original work, written, tested, and documented independently as part of the VITyarthi OSS Capstone Project.

---

*"Every tool you will use in your career was shaped by people who chose to build in the open and share their work freely."*  
— VITyarthi OSS Course
