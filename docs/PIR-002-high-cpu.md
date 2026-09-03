# PIR-002: High CPU Usage

## 1. Incident Summary

| Field | Details |
|---|---|
| Incident ID | INC-002 |
| Incident Type | High CPU Usage |
| Severity | SEV-2 High |
| Affected Component | Application Server |
| Detection Method | Prometheus + Node Exporter |
| Status | Resolved |
| Owner | DevOps Team |

---

## 2. Timeline

| Time | Event |
|---|---|
| 02:00 PM | System CPU usage was operating normally. |
| 02:10 PM | CPU usage started increasing. |
| 02:15 PM | CPU usage exceeded the defined threshold. |
| 02:17 PM | Prometheus triggered the HighCPUUsage alert. |
| 02:20 PM | DevOps engineer acknowledged the alert. |
| 02:23 PM | Running processes were inspected. |
| 02:27 PM | A resource-intensive process was identified. |
| 02:30 PM | The process was stopped and application load returned to normal. |
| 02:35 PM | CPU usage returned to an acceptable level. |
| 02:40 PM | Incident was closed. |

---

## 3. Impact

High CPU usage caused increased system resource
consumption.

The application experienced performance degradation
and slower response times.

No permanent data loss occurred.

---

## 4. Root Cause

A resource-intensive application process consumed
an unusually high amount of CPU.

The process caused sustained CPU utilization above
the configured monitoring threshold.

---

## 5. Detection

Prometheus detected high CPU utilization through
Node Exporter metrics.

The HighCPUUsage alert was configured to trigger
when CPU usage remained above the defined threshold.

---

## 6. Investigation

The following commands were used:

```bash
top