---

# 4. `commands/02-install-node-exporter.md`

Tes notes indiquent l’installation de Node Exporter avec `sudo apt install prometheus-node-exporter -y`, la vérification du service, puis le port `9100` et l’URL `/metrics`. 【1-074903】

```markdown
# Install Node Exporter on Ubuntu

## Step 1 - Install Node Exporter

```bash
sudo apt install prometheus-node-exporter -y

Node Exporter exposes Linux system metrics.
Step 2 - Check Node Exporter status
Shellsystemctl status prometheus-node-exporter --no-pagerAfficher plus de lignes
Expected result:
Plain TextActive: active (running)Afficher plus de lignes
Step 3 - Check Node Exporter port
Shellss -tulpn | grep 9100Afficher plus de lignes
Expected result:
Plain TextNode Exporter is listening on port 9100.``Afficher plus de lignes
Step 4 - Open raw metrics endpoint
Plain Texthttp://localhost:9100/metricsAfficher plus de lignes
You should see Linux metrics such as:
Plain Textnode_cpu_seconds_totalnode_memory_MemAvailable_bytesnode_filesystem_avail_bytesAfficher plus de lignes

---

# 5. `commands/03-validate-installation.md`

Tes notes valident l’installation avec `/targets`, où deux services sont `UP`, puis avec la requête PromQL `up`. 【1-074903】

```markdown
# Validate Prometheus Installation

## Step 1 - Check Prometheus configuration

```bash
promtool check config /etc/prometheus/prometheus.yml

## Step 2 - Restart Prometheus

```bash
sudo systemctl

## Step 3 - Check Prometheus status

```bash
systemctl status prometheus --no-pager

## Step 4 - Check targets : http://localhost:9090/targets

## Step 5 - Test PromQL query
Open http://localhost:9090 and run : 

```bash
up
