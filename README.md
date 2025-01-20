# Scripts Repository

Welcome to the **Scripts Repository**! This repository contains useful Python and shell scripts for monitoring and security purposes.

## Table of Contents
- [About the Repository](#about-the-repository)
- [Scripts](#scripts)
  - [Python Scripts](#python-scripts)
  - [Shell Scripts](#shell-scripts)
- [How to Use](#how-to-use)
- [License](#license)

---

## About the Repository

This repository is designed to host practical scripts for system administration and monitoring. Each script is organized into its respective folder for ease of access.

---

## Scripts

### Python Scripts
The Python scripts can be found in the `python_scripts` folder:
- **Nginx Access Log Monitoring Script**:
  - Monitors Nginx access logs for repeated failed attempts.
  - Automatically blocks malicious IP addresses using `iptables`.

For more details about this script, visit the [Python Scripts README](python_scripts/README.md).

---

### Shell Scripts
The Shell scripts can be found in the `shell_scripts` folder:
- **Resource Monitoring Script**:
  - Monitors CPU, memory, and disk usage.
  - Sends email alerts if usage exceeds predefined thresholds.

For more details about this script, visit the [Shell Scripts README](shell_scripts/README.md).

---

## How to Use

### Cloning the Repository
To get started, clone this repository:
```bash
git clone https://github.com/Prasad-b-git/scripts.git
cd scripts
