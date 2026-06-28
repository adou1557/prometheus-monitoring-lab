# Prometheus Monitoring Lab on Ubuntu

## Objective

This lab demonstrates how to install, configure, and validate a basic monitoring stack on Ubuntu using **Prometheus** and **Node Exporter**.

The primary objective is to understand how Prometheus collects and stores metrics from a Linux system, while Node Exporter exposes operating system and hardware metrics through a dedicated endpoint.

By completing this lab, you will learn how to:

- Install Prometheus on Ubuntu
- Install and configure Node Exporter
- Verify that monitoring services are running correctly
- Explore metrics through the Prometheus web interface
- Execute basic PromQL queries
- Understand the Prometheus pull-based monitoring model

---

## Architecture Overview

```text
+------------------+
|   Ubuntu Server  |
+------------------+
          |
          | Exposes system metrics
          | Port 9100
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
          | Web UI & API
          | Port 9090
          v
+------------------+
| Prometheus UI    |
+------------------+
```

---

## Components

### Prometheus

Prometheus is an open-source monitoring and alerting toolkit designed for collecting and storing time-series metrics.

Key features:

- Time-series database
- PromQL query language
- Service discovery support
- Alerting integration
- Web-based user interface

Default access:

```text
http://localhost:9090
```

---

### Node Exporter

Node Exporter is a Prometheus exporter that exposes hardware and operating system metrics from Linux systems.

Common metrics include:

- CPU utilization
- Memory usage
- Disk usage
- Filesystem statistics
- Network activity
- System load

Default metrics endpoint:

```text
http://localhost:9100/metrics
```

---

## Monitoring Workflow

```text
Linux Host
     |
     | System Metrics
     v
Node Exporter
     |
     | HTTP /metrics
     v
Prometheus
     |
     | Stores Metrics
     v
Time-Series Database
     |
     | PromQL Queries
     v
Dashboards and Alerts
```

---

## Learning Outcomes

After completing this lab, you should be able to:

- Explain the role of Prometheus and Node Exporter
- Understand how metric scraping works
- Verify service availability using Linux commands
- Query metrics using PromQL
- Navigate the Prometheus web interface
- Interpret basic infrastructure metrics

---

## Technologies Used

- Ubuntu Server
- Prometheus
- Node Exporter
- PromQL
- Systemd
- Linux Networking Tools

---

## Expected Result

At the end of the lab:

- Prometheus is running on port **9090**
- Node Exporter is running on port **9100**
- Prometheus successfully scrapes Node Exporter metrics
- Metrics can be queried through the Prometheus Web UI
- Basic monitoring of CPU, memory, and disk resources is operational
