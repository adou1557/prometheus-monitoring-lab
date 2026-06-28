# Install Prometheus on Ubuntu

## Step 1 - Update the system

```bash
sudo apt update

## Step 2 - Install Prometheus

```bash
sudo apt install prometheus -y

## Step 3 - Check Prometheus status

```bash
systemctl status prometheus --no-pager

## Step 4 - Enable Prometheus at startup

sudo systemctl enable prometheus

## Step 5 - Check Prometheus port

```bash
ss -tulpn | grep 9090

## Step 6 -Open Prometheus Web UI : http://localhost:9090
