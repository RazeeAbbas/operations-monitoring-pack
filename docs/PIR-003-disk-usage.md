# PIR-003: High Disk Usage

## 1. Incident Summary

| Field | Details |
|---|---|
| Incident ID | INC-003 |
| Incident Type | High Disk Usage |
| Severity | SEV-2 High |
| Affected Component | Linux Server |
| Detection Method | Prometheus + Node Exporter |
| Status | Resolved |
| Owner | DevOps Team |

---

## 2. Timeline

| Time | Event |
|---|---|
| 09:00 AM | Disk utilization was operating normally. |
| 09:30 AM | Disk usage started increasing. |
| 10:00 AM | Disk usage exceeded the warning threshold. |
| 10:02 AM | Prometheus triggered the HighDiskUsage alert. |
| 10:05 AM | DevOps engineer acknowledged the alert. |
| 10:10 AM | Disk utilization was checked using `df -h`. |
| 10:15 AM | Large directories and log files were identified. |
| 10:20 AM | Unnecessary files and old logs were cleaned. |
| 10:25 AM | Disk usage returned to an acceptable level. |
| 10:30 AM | Incident was closed. |

---

## 3. Impact

High disk utilization reduced the amount of available
storage on the server.

If disk usage had continued increasing, applications
could have experienced failures when attempting to
write logs, temporary files, or application data.

No permanent data loss occurred.

---

## 4. Root Cause

The disk usage increased because of accumulated log
files and unnecessary files on the server.

The files consumed available disk space and caused
disk utilization to exceed the monitoring threshold.

---

## 5. Detection

Prometheus detected increased filesystem utilization
through Node Exporter.

The HighDiskUsage alert was triggered after disk
usage exceeded the configured threshold.

---

## 6. Investigation

The following commands were used:

```bash
df -h