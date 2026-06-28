# 7. `notes/architecture.md`

# Architecture Notes

## High-Level Architecture

```text
+------------------+
|   Ubuntu Server  |
+------------------+
          |
          | Metrics exposed (port 9100)
          v
+------------------+
|  Node Exporter   |
+------------------+
          |
          | Scraped by Prometheus
          v
+------------------+
|   Prometheus     |
+------------------+
          |
          | Web UI (port 9090)
          v
+------------------+
|    Browser       |
+------------------+
```

---

## Components Overview

### Node Exporter

Node Exporter exposes hardware and operating system metrics from Linux hosts.

Examples of exported metrics include:

- CPU usage
- Memory utilization
- Disk usage
- Filesystem statistics
- Network activity

By default, Node Exporter exposes metrics on:

```text
http://localhost:9100/metrics
```

---

### Prometheus

Prometheus collects, stores, and queries metrics from monitored targets.

It periodically scrapes metrics exposed by exporters and applications.

The Prometheus web interface is available on:

```text
http://localhost:9090
```

---

## Configuration

Prometheus uses a configuration file named:

```text
prometheus.yml
```

This file defines:

- Scrape targets
- Scrape intervals
- Jobs
- Alerting configuration (optional)

Example monitored targets in this lab:

```text
localhost:9090   # Prometheus
localhost:9100   # Node Exporter
```

---

## Pull Model

Prometheus uses a **pull-based monitoring model**.

### How it works

1. Targets expose metrics through an HTTP endpoint.
2. Prometheus periodically connects to these endpoints.
3. Metrics are collected ("scraped").
4. The collected data is stored in the Prometheus time-series database.

### Benefits

- Simple architecture
- Centralized monitoring
- Easy service discovery
- Better control over metric collection

---

## Monitoring Flow

```text
Node Exporter
      |
      | Exposes metrics
      v
/metrics endpoint
      |
      | Scraped by Prometheus
      v
Prometheus Database
      |
      | Queried using PromQL
      v
Dashboards and Alerts
```

---

## Security Perspective

Monitoring is an important part of operational and security visibility.

### Why it matters

- Detect infrastructure issues quickly
- Identify resource exhaustion
- Monitor service availability
- Support incident response activities

### Potential Risks

If a target becomes unreachable:

- Metrics are no longer collected
- Dashboards may show incomplete data
- Alerts may become unreliable
- Operational visibility is reduced

This can affect both system availability and security monitoring capabilities.

---

## Key Takeaways

- **Node Exporter** exposes Linux system metrics.
- **Prometheus** collects and stores metrics.
- **Prometheus uses a pull model** to scrape targets.
- **`prometheus.yml`** defines what Prometheus monitors.
- Monitoring improves infrastructure visibility and operational awareness.
