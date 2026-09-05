# EC2 Disk Usage Monitoring and Troubleshooting

## Objective

Monitor disk utilization on a Linux-based Amazon EC2 instance and identify directories or files responsible for high storage consumption.

## 1. Check Filesystem Usage

```bash
df -h
```

This command provides a high-level view of filesystem utilization.

Important values to review:

- Total filesystem size
- Used storage
- Available storage
- Disk utilization percentage
- Mounted filesystem

## 2. Identify Large Directories

If disk utilization is higher than expected, investigate directory-level usage:

```bash
du -h --max-depth=1 /home/ubuntu | sort -hr
```

This sorts directories by size and helps identify which locations are consuming the most storage.

For another directory:

```bash
du -h --max-depth=1 /path/to/directory | sort -hr
```

## 3. Check Large Files

Large files can be identified using:

```bash
find /home/ubuntu -type f -size +500M -exec ls -lh {} \;
```

This can help locate:

- Large log files
- Cached files
- Temporary files
- Application-generated data
- Old artifacts

## 4. Check Log Storage

```bash
du -sh /var/log/*
```

Application-specific logs can also be inspected:

```bash
ls -lh /path/to/logs/
```

Recent entries can be reviewed with:

```bash
tail -n 100 <log-file>
```

## 5. Troubleshooting Workflow

```text
High Disk Usage Detected
        |
        v
     df -h
        |
        v
Identify Large Directories
        |
        v
du + sort
        |
        v
Identify Large Files / Logs
        |
        v
Determine Root Cause
        |
        v
Apply Safe Corrective Action
        |
        v
Recheck Disk Usage
```

## 6. Validation

After corrective action, disk utilization should be checked again:

```bash
df -h
```

The objective is to confirm that storage utilization has returned to an acceptable level and that required applications and services continue to operate normally.

## Operational Considerations

Files should not be deleted simply because they consume significant storage.

Before cleanup:

- Determine what created the file.
- Verify whether the application still requires it.
- Check whether logs need to be retained.
- Consider log rotation or archival.
- Verify that removing data will not affect running services.
- Recheck the system after any change.

## Security

All examples are sanitized and do not contain production IP addresses, hostnames, credentials, customer information, or confidential infrastructure details.
