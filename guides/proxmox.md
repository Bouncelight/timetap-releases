# Timetap on Proxmox VE

> **Not tested yet.** Written from Proxmox's documentation. If you try it, please
> [tell us how it went](https://github.com/Bouncelight/timetap-releases/issues) - corrections are welcome.

Timetap runs in a small Debian container (LXC) with Docker inside it. You get the web page, the iPhone app and
[NFC readers](readers.md) join your normal WiFi.

## 1. The container

1. Proxmox's web page > your node > **local** storage > **CT Templates** > **Templates**: download **debian-13-standard**
   (or 12).
2. **Create CT** (top right):
   * **Hostname:** `timetap`, a root password.
   * **Unprivileged container** and **Nesting** ticked (Docker needs nesting).
   * **Template:** the Debian one. **Disk:** 8 GB. **CPU:** 1 core. **Memory:** 1024 MB.
   * **Network:** DHCP, or a fixed address (easier to find later).
3. **Finish**, then select the container > **Start**.

## 2. Docker and Timetap

Select the container > **Console**, log in as `root`, and paste these one at a time:

```bash
apt-get update && apt-get install -y curl
```

```bash
curl -fsSL https://get.docker.com | sh
```

```bash
mkdir -p /opt/timetap && cd /opt/timetap && curl -fsSLO https://github.com/Bouncelight/timetap-releases/releases/latest/download/docker-compose.yml && docker compose up -d
```

```bash
docker compose logs timetap
```

The last one shows the first login (**Admin** and a password), printed once.

## 3. Log in

Open `http://<container-address>` (shown with `hostname -I` in the console). Change the password under **Account**.

## Good to know

* **Data:** `/opt/timetap/timetap-data` inside the container. A Proxmox backup of the container (**Backup** >
  **Backup now**, or a scheduled job) includes it.
* **Updating:** in the console, `cd /opt/timetap && docker compose pull && docker compose up -d`.
* More about the settings: [Docker](docker.md).
