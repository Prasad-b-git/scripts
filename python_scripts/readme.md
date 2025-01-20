# IP Blocking Script for Nginx Access Logs

This Python script monitors Nginx access logs for suspicious activity and blocks IP addresses with excessive failed attempts using `iptables`. The blocked IPs are recorded in a log file for reference and to prevent redundant blocking.

## Features
1. Monitors the Nginx access log file (`/var/log/nginx/access.log`).
2. Identifies IPs with excessive failed login attempts or suspicious activity.
3. Blocks flagged IPs using `iptables`.
4. Maintains a record of blocked IPs in `/etc/nginx/sites-available/blocked_ips.txt`.
5. Prevents redundant blocking by maintaining an in-memory and file-based record of blocked IPs.

---

## Configuration
### Variables
- `LOG_FILE`: Path to the Nginx access log file to monitor. Default: `/var/log/nginx/access.log`.
- `BLOCKED_IPS_FILE`: File to store blocked IPs along with timestamps. Default: `/etc/nginx/sites-available/blocked_ips.txt`.
- `MAX_FAILED_ATTEMPTS`: Maximum allowed failed attempts before blocking an IP. Default: `5`.
- `BLOCK_DURATION`: Duration for which an IP remains blocked (in seconds). Default: `300` seconds.

---

## How It Works
1. **Log Monitoring**:
   - The script continuously monitors the Nginx access log file for suspicious patterns.
   - It tracks IP addresses and their failed attempts.

2. **Blocking Logic**:
   - If an IP exceeds the `MAX_FAILED_ATTEMPTS` threshold, it is blocked using `iptables`.
   - The blocked IP is recorded in `BLOCKED_IPS_FILE` with a timestamp.

3. **Persistence**:
   - Previously blocked IPs are loaded from `BLOCKED_IPS_FILE` at script startup to avoid redundant blocking.

---

## Prerequisites
1. Python 3 installed on the system.
2. Root or sudo privileges (required for managing `iptables` rules).
3. Nginx installed and access logs enabled.
4. The log file (`/var/log/nginx/access.log`) must exist and be accessible to the script.

---

## How to Run
1. Clone or copy the script to your server.
2. Ensure Python dependencies (if any) are installed.
3. Run the script with sudo privileges to allow `iptables` commands:
   ```bash
   sudo python3 ip_blocker.py
   ```

---

## Script Functions
### `load_blocked_ips()`
- Reads `BLOCKED_IPS_FILE` and populates the `BLOCKED_IPS` set to avoid re-blocking IPs that are already blocked.

### `block_ip(ip_address)`
- Blocks the given IP address using the `iptables` command.
- Records the blocked IP and the timestamp in `BLOCKED_IPS_FILE`.
- Skips blocking if the IP is already in the `BLOCKED_IPS` set.

---

## Example Workflow
1. An attacker tries to access your server repeatedly with invalid credentials.
2. Their IP is logged in `/var/log/nginx/access.log`.
3. The script detects the failed attempts and blocks the IP once it exceeds `MAX_FAILED_ATTEMPTS`.
4. The blocked IP is added to `/etc/nginx/sites-available/blocked_ips.txt` with the block timestamp.

---

## Important Notes
- Ensure the script has access to the specified log file and can write to the blocked IPs file.
- Modify `BLOCK_DURATION` and `MAX_FAILED_ATTEMPTS` as per your security requirements.
- Use caution when running the script in production, as blocking legitimate IPs can disrupt service.
- Regularly review `/etc/nginx/sites-available/blocked_ips.txt` to manage blocked IPs.

---

## Troubleshooting
### Common Issues
1. **Permission Denied:** Ensure the script is executed with sudo privileges.
2. **File Not Found:** Verify that the specified `LOG_FILE` and `BLOCKED_IPS_FILE` paths are correct.
3. **iptables Command Errors:** Check if `iptables` is installed and properly configured on your server.

### Logs
- Review Nginx access logs at `/var/log/nginx/access.log` for debugging suspicious activity.
- Check the blocked IPs file at `/etc/nginx/sites-available/blocked_ips.txt` for blocked entries.

---

## Conclusion
This script provides a basic yet effective way to secure your server against brute-force and other unauthorized access attempts. By automating the process of detecting and blocking malicious IPs, it enhances the security of your Nginx web server. Customize the script as needed to fit your specific use case.

