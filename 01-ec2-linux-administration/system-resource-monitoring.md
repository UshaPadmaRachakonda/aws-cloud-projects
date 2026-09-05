# EC2 System Resource Monitoring

## Objective

Monitor CPU, memory, system load, and running processes on a Linux-based Amazon EC2 instance to identify resource-related performance issues.

## 1. Check Memory Usage

```bash
free -h
```

This displays:

- Total memory
- Used memory
- Free memory
- Cache
- Available memory
- Swap usage

The `available` value is particularly useful when evaluating whether the system has sufficient memory for additional workloads.

## 2. Monitor CPU and Memory in Real Time

```bash
top
```

This provides a real-time view of:

- CPU utilization
- Memory utilization
- System load
- Running processes
- Process CPU usage
- Process memory usage

## 3. Check Running Processes

```bash
ps aux
```

This provides a snapshot of currently running processes.

To identify processes consuming the most memory:

```bash
ps aux --sort=-%mem | head
```

To identify processes consuming the most CPU:

```bash
ps aux --sort=-%cpu | head
```

## 4. Check System Uptime and Load

```bash
uptime
```

This shows how long the server has been running and the system load averages.

## 5. Troubleshooting Workflow

```text
Performance Issue
       |
       v
Check Memory
   free -h
       |
       v
Check CPU / Load
   top / uptime
       |
       v
Inspect Processes
     ps aux
       |
       v
Identify Resource-Heavy Process
       |
       v
Investigate Application / Service
       |
       v
Apply Corrective Action
       |
       v
Validate System Health
```

## Operational Considerations

A process should not be stopped only because it is consuming significant CPU or memory.

Before taking action:

- Identify the process and its purpose.
- Determine whether high utilization is expected.
- Check related application logs.
- Verify dependencies.
- Assess the impact before restarting or terminating a service.
- Monitor the system again after any corrective action.
