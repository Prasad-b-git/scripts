# Resource Usage Monitoring Script

This shell script monitors system resource usage, including CPU, memory, and disk usage, and sends email alerts when any of the specified thresholds are exceeded. The script is designed to help system administrators stay informed about potential resource bottlenecks on their servers.

## Features
- **CPU Monitoring**: Alerts when CPU usage exceeds a defined threshold.
- **Memory Monitoring**: Alerts when memory usage exceeds a defined threshold.
- **Disk Monitoring**: Alerts when disk usage for any partition exceeds a defined threshold.
- **Email Notifications**: Sends email alerts to a specified email address with details about the resource usage.
- **Logging**: Logs normal operation (when no thresholds are exceeded) to a log file.

## Configuration
The script includes configurable thresholds and settings:

- `CPU_THRESHOLD`: Maximum allowed CPU usage percentage (default: 50%).
- `MEM_THRESHOLD`: Maximum allowed memory usage percentage (default: 30%).
- `DISK_THRESHOLD`: Maximum allowed disk usage percentage (default: 30%).
- `EMAIL`: The email address to send alerts to (default: `prasadsb240801@gmail.com`).

## Prerequisites
1. Ensure `mailx` is installed for sending email alerts.
   ```bash
   sudo apt-get install mailutils
   ```
2. Configure your email settings for `mailx` (e.g., SMTP server) based on your system's requirements.

## Script Details
### CPU Usage Monitoring
- Extracts CPU usage using the `top` command.
- Compares the usage against `CPU_THRESHOLD`.
- Adds a warning to the alert message if the threshold is exceeded.

### Memory Usage Monitoring
- Calculates memory usage percentage using the `free` command.
- Compares the usage against `MEM_THRESHOLD`.
- Adds a warning to the alert message if the threshold is exceeded.

### Disk Usage Monitoring
- Checks disk usage for all mounted partitions using the `df` command.
- Excludes system directories like `/sys`, `/proc`, `/dev`, `/run`, and `/tmp`.
- Compares usage for each partition against `DISK_THRESHOLD`.
- Adds a warning to the alert message if any partition exceeds the threshold.

### Email Alerts
- Sends an email with the subject `Resource Usage Alert` and the alert message detailing the exceeded thresholds.

### Logging
- If no thresholds are exceeded, logs the date and message `No resource thresholds exceeded.` to `/var/log/resource_monitor.log`.

## How to Use
1. Copy the script to your server and make it executable:
   ```bash
   chmod +x resource_monitor.sh
   ```
2. Run the script manually:
   ```bash
   ./resource_monitor.sh
   ```
3. (Optional) Schedule the script to run periodically using `cron`:
   ```bash
   crontab -e
   ```
   Add an entry to run the script every 5 minutes (adjust as needed):
   ```
   */5 * * * * /path/to/resource_monitor.sh
   ```

## Example Output
### Email Alert
Subject: `Resource Usage Alert`

Body:
```
Warning: CPU usage has reached 75%.
Warning: Memory usage has reached 65%.
Warning: Disk usage on /home has reached 80%.
```

### Log Entry (if no alerts)
```
2025-01-20: No resource thresholds exceeded.
```

## Notes
- Update the email address in the `EMAIL` variable to your own.
- Ensure the script has the necessary permissions to execute and access the required files.
- The script assumes a Linux environment and may require modifications for other operating systems.

## Troubleshooting
- If email alerts are not received:
  - Check the `mailx` configuration and logs.
  - Verify network connectivity to the SMTP server.
- If disk usage is not reported correctly, ensure the `df` command outputs the expected format.

## License
This script is open-source and can be modified and distributed as needed. Attribution is appreciated.

