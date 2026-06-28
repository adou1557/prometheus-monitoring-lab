# Check Services

Verify that Prometheus and Node Exporter are running correctly and listening on their expected ports.

---

## Check Prometheus Status

### Command

```bash
systemctl status prometheus --no-pager
```

### What to Look For

A healthy service should display:

```text
Active: active (running)
```

### Purpose

This command confirms that the Prometheus service is currently running and managed by `systemd`.

---

## Check Node Exporter Status

### Command

```bash
systemctl status prometheus-node-exporter --no-pager
```

### What to Look For

A healthy service should display:

```text
Active: active (running)
```

### Purpose

This command verifies that Node Exporter is running and exposing system metrics.

---

## Check Listening Ports

### Command

```bash
ss -tulpn | grep -E '9090|9100'
```

### Purpose

Displays processes listening on the Prometheus and Node Exporter ports.

### Example Output

```text
tcp   LISTEN  0  4096  *:9090  *:*
tcp   LISTEN  0  4096  *:9100  *:*
```

---

## Port Reference

| Port | Service | Purpose |
|--------|----------|----------|
| `9090` | Prometheus | Web interface, API, and query engine |
| `9100` | Node Exporter | Linux system metrics endpoint |

---

## Verification Workflow

Run the commands in the following order:

```bash
systemctl status prometheus --no-pager
```

```bash
systemctl status prometheus-node-exporter --no-pager
```

```bash
ss -tulpn | grep -E '9090|9100'
```

---

## Expected Result

✅ Prometheus service is running

✅ Node Exporter service is running

✅ Port `9090` is listening

✅ Port `9100` is listening

If all checks succeed, the monitoring stack is functioning correctly and ready for metric collection.

---

## Troubleshooting

### Prometheus Not Running

Check logs:

```bash
journalctl -u prometheus -n 50
```

Restart the service:

```bash
sudo systemctl restart prometheus
```

---

### Node Exporter Not Running

Check logs:

```bash
journalctl -u prometheus-node-exporter -n 50
```

Restart the service:

```bash
sudo systemctl restart prometheus-node-exporter
```

---

## Next Step

Open the Prometheus web interface:

```text
http://localhost:9090
```

Verify that the Node Exporter target is reachable:

```text
Status → Targets
```

The target should appear with the status:

```text
UP
```
