# Incident Response Runbook

## 1. Purpose

This runbook defines the standard process for identifying,
investigating, responding to, escalating, resolving, and closing
operational incidents.

The purpose is to provide a consistent procedure for DevOps engineers
when monitoring alerts indicate a potential infrastructure,
application, or service problem.

---

## 2. Incident Severity Levels

| Severity | Description | Example | Response |
|---|---|---|---|
| SEV-1 Critical | Complete production outage | Website unavailable | Immediate |
| SEV-2 High | Major service degradation | Application very slow | Urgent |
| SEV-3 Warning | Minor operational issue | CPU above threshold | Investigate |
| SEV-4 Informational | Low-impact event | Temporary restart | Monitor |

---

## 3. Incident Response Workflow

Monitoring Alert
        ↓
Alert Acknowledged
        ↓
Incident Verified
        ↓
Severity Determined
        ↓
Investigation
        ↓
Mitigation
        ↓
Recovery Verification
        ↓
Monitoring
        ↓
Incident Closure
        ↓
Post-Incident Review

---

## 4. First Response Checklist

When an alert is received:

- [ ] Acknowledge the alert.
- [ ] Identify the affected service.
- [ ] Check the severity.
- [ ] Open the Grafana dashboard.
- [ ] Check CPU usage.
- [ ] Check memory usage.
- [ ] Check disk usage.
- [ ] Check service/container status.
- [ ] Check application logs.
- [ ] Test the affected service.
- [ ] Determine user impact.
- [ ] Start mitigation.
- [ ] Escalate if required.
- [ ] Verify service recovery.
- [ ] Document the incident.

---

## 5. Linux Investigation Commands

### CPU

```bash
top

ps aux --sort=-%cpu | head
Memory
free -h
ps aux --sort=-%mem | head
Disk
df -h
du -sh /* 2>/dev/null | sort -h
Processes
ps aux
Services
systemctl status SERVICE_NAME
Logs
journalctl -xe
6. Docker Investigation

Check running containers:

docker ps

Check all containers:

docker ps -a

Check container logs:

docker logs CONTAINER_NAME

Check the last 50 log lines:

docker logs --tail 50 CONTAINER_NAME

Check resource usage:

docker stats

Restart a container:

docker restart CONTAINER_NAME
7. Kubernetes Investigation

Check pods:

kubectl get pods

Check detailed pod information:

kubectl describe pod POD_NAME

Check application logs:

kubectl logs POD_NAME

Check logs from the previous crashed container:

kubectl logs POD_NAME --previous

Restart a deployment:

kubectl rollout restart deployment DEPLOYMENT_NAME

Check deployment status:

kubectl rollout status deployment DEPLOYMENT_NAME

---------------------------------------------------------------------------------
Subject: [SEV-1] Incident Alert: Production Web Application Outage

Incident ID: INC-001
Severity: SEV-1 (Critical)
Affected Service: Monitored Web Application (Nginx)
Status: Investigating

Impact:
Users are currently unable to access the web application.

Summary:
Prometheus detected an HTTP probe failure (probe_success == 0). The DevOps team has been notified and is actively investigating the container logs and infrastructure status.

Next Update: In 15 minutes.

-------------------------------------------------------------------------------------------------------------
Subject: UPDATE [SEV-1] Incident INC-001: Production Web Application Outage

Incident ID: INC-001
Status: Identified / Mitigating

Update:
The root cause has been identified as a failed Nginx container. The team is restarting the service and verifying database connection pools.

Next Update: In 15 minutes or upon resolution.
---------------------------------------------------------------------------------------------------------------------------
Subject: RESOLVED [SEV-1] Incident INC-001: Production Web Application Outage

Incident ID: INC-001
Status: Resolved

Resolution Summary:
The web application container was successfully restarted. System metrics indicate response times and HTTP checks have returned to healthy states (probe_success == 1). Total downtime was 12 minutes. A post-incident review (PIR) will follow.