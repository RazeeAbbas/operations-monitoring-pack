| Alert         | Severity | Threshold / Condition        | Owner                  | First Action                         |
| ------------- | -------- | ---------------------------- | ---------------------- | ------------------------------------ |
| High CPU      | Warning  | CPU > 80% for 5 min          | DevOps                 | Check processes and traffic          |
| High Memory   | Warning  | Memory > 85% for 5 min       | DevOps                 | Find memory-consuming processes      |
| High Disk     | Critical | Disk > 90%                   | DevOps                 | Find large files/logs and free space |
| Service Down  | Critical | `up == 0` for 1 min          | DevOps/App Team        | Check service/container status       |
| HTTP Failure  | Critical | `probe_success == 0`         | DevOps/App Team        | Test endpoint and application logs   |
| Pod Restart   | Warning  | Restarts increase repeatedly | DevOps/Kubernetes Team | Check pod events and logs            |
| Slow Response | Warning  | Response > 2 sec for 5 min   | DevOps/App Team        | Check app, CPU, DB and network       |
