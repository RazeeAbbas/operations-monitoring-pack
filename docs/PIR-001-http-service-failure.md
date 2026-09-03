# PIR-001: HTTP Service Failure

## 1. Incident Summary

| Field | Details |
|---|---|
| Incident ID | INC-001 |
| Incident Type | HTTP Service Failure |
| Severity | SEV-1 Critical |
| Affected Service | Nginx Web Application |
| Detection Method | Prometheus + Blackbox Exporter |
| Status | Resolved |
| Owner | DevOps Team |

---

## 2. Timeline

| Time | Event |
|---|---|
| 10:00 AM | Web application was operating normally. |
| 10:05 AM | Nginx container became unavailable. |
| 10:06 AM | Blackbox Exporter detected HTTP failure. |
| 10:07 AM | Prometheus changed `probe_success` from 1 to 0. |
| 10:08 AM | HTTPFailure alert was triggered. |
| 10:10 AM | DevOps engineer investigated container status. |
| 10:12 AM | Container was found to be stopped. |
| 10:14 AM | Container was restarted. |
| 10:15 AM | HTTP endpoint became available. |
| 10:17 AM | Monitoring confirmed recovery. |
| 10:20 AM | Incident was closed. |

---

## 3. Impact

The monitored web application became unavailable.

Users attempting to access the application would not
receive a successful HTTP response.

The incident affected application availability but did
not result in permanent data loss.

---

## 4. Root Cause

The Nginx web application container stopped unexpectedly.

Because the container was not running, the HTTP endpoint
was unavailable and the Blackbox Exporter health check failed.

---

## 5. Detection

The incident was detected by the HTTP monitoring system.

The Prometheus metric:

`probe_success`

changed from:

`1 = Healthy`

to:

`0 = Failed`

This triggered the HTTPFailure alert.

---

## 6. Investigation

The following commands were used during investigation:

```bash
docker ps
docker ps -a
docker logs monitored-web-app