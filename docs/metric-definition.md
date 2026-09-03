# Monitoring Metric Definitions

## CPU Usage

Metric:
node_cpu_seconds_total

Purpose:
Measures CPU usage of the monitored system.

Warning Threshold:
Above 80% for 2 minutes.

Reason:
Sustained high CPU usage may indicate overloaded applications,
high user traffic, inefficient processes, or insufficient resources.


## Memory Usage

Metrics:
node_memory_MemAvailable_bytes
node_memory_MemTotal_bytes

Purpose:
Measures available and total system memory.

Threshold:
Above 85% usage for 2 minutes.

Reason:
High memory consumption may cause application slowdown,
process termination, or system instability.


## Disk Usage

Metrics:
node_filesystem_avail_bytes
node_filesystem_size_bytes

Purpose:
Measures filesystem capacity and available disk space.

Threshold:
Above 85%.

Reason:
A full disk may prevent applications from writing files,
logs, database data, or temporary information.


## Service Availability

Metric:
up

Purpose:
Determines whether Prometheus can successfully scrape
a monitored service.

Values:

1 = UP
0 = DOWN


## HTTP Availability

Metric:
probe_success

Purpose:
Checks whether an HTTP endpoint responds successfully.

Values:

1 = Healthy
0 = Failed


## HTTP Response Time

Metric:
probe_duration_seconds

Purpose:
Measures how long the HTTP request takes.

Threshold:
Above 2 seconds.

Reason:
Slow response times can indicate overloaded servers,
database problems, network latency, or application issues.


## Container CPU

Metric:
container_cpu_usage_seconds_total

Purpose:
Measures CPU consumption of Docker containers.


## Container Memory

Metric:
container_memory_usage_bytes

Purpose:
Measures memory usage of Docker containers.


## Kubernetes Pod Restarts

Metric:
kube_pod_container_status_restarts_total

Purpose:
Tracks the number of times Kubernetes containers restart.

Possible Causes:

- Application crash
- Out-of-memory error
- Failed health check
- Configuration problem
- Dependency failure