# Prometheus Monitoring Lab on Ubuntu

## Objective

This lab explains how to install and validate a basic monitoring stack on Ubuntu using Prometheus and Node Exporter.

The goal is to understand how Prometheus collects metrics from a Linux system and how Node Exporter exposes system metrics such as CPU, memory and disk usage.

## Architecture

```text
Ubuntu Server
    |
    | exposes metrics on port 9100
    v
Node Exporter
    |
    | scraped by Prometheus
    v
Prometheus
    |
    | exposes Web UI on port 9090
    v
Prometheus Web Interface
