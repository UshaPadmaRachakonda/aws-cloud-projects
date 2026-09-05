# EC2 & Linux Administration

This project demonstrates practical Linux server administration, monitoring, and troubleshooting in an AWS EC2 environment.

## Skills Demonstrated

- AWS EC2 administration
- Linux server monitoring
- Disk and filesystem analysis
- CPU and memory monitoring
- Process monitoring
- Log investigation
- Service troubleshooting
- Resource utilization analysis

## Linux Monitoring Commands

### Check Disk Usage

```bash
df -h
```

Displays filesystem capacity, used space, available space, and disk utilization percentage.

### Investigate Directory Usage

```bash
du -h --max-depth=1 /home/ubuntu | sort -hr
```

Helps identify directories consuming large amounts of disk space.

### Check Memory

```bash
free -h
```

Displays total, used, available, and cached system memory.

### Monitor CPU and Processes

```bash
top
```

Used to inspect CPU usage, memory consumption, system load, and running processes.

### Inspect Running Processes

```bash
ps aux
```

Provides detailed information about currently running processes.

### Check a Linux Service

```bash
systemctl status <service-name>
```

Used to verify whether a system service is running correctly.

### Inspect Application Logs

```bash
tail -n 100 <log-file>
```

Displays recent log entries for troubleshooting application or system issues.

## Troubleshooting Workflow

A typical server investigation follows this process:

1. Check overall disk utilization.
2. Identify directories consuming excessive storage.
3. Check available memory and CPU utilization.
4. Inspect running processes.
5. Verify application and system services.
6. Analyze recent logs for errors.
7. Take corrective action based on the identified issue.

## Security Note

All commands and examples in this project use generic or sanitized environments. No production IP addresses, credentials, customer data, or confidential infrastructure information are included.
