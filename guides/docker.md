# Timetap with Docker

For any Linux computer or server that has Docker with Compose. You get the web page, the iPhone app and
[NFC readers](readers.md) join your normal WiFi (on a [Raspberry Pi](raspberry-pi.md) they can have a WiFi of their own).

Guides for particular systems: [Unraid](unraid.md), [Synology](synology.md), [QNAP](qnap.md), [Proxmox](proxmox.md).

## Install

Make a folder for Timetap and download the compose file into it:

```bash
mkdir timetap && cd timetap
curl -fsSLO https://github.com/Bouncelight/timetap-releases/releases/latest/download/docker-compose.yml
```

Look it over (the comments say what each line does), then start it:

```bash
docker compose up -d
```

The first login is printed once, in the log:

```bash
docker compose logs timetap
```

Open `http://<this computer's address>` and log in as **Admin** with that password. Change it under **Account**.

## The settings in docker-compose.yml

| Setting | What it is |
|---|---|
| `ports: "80:8080"` | The web page, the app and http. If port 80 is taken, use e.g. `"8088:8080"` and open `http://<address>:8088`. |
| `ports: "443:8443"` | https, once IT > Secure address is set up. |
| `./timetap-data:/data` | Everything Timetap keeps: the database, backups and settings. **Back this folder up.** |
| `TZ` | The time zone hours are counted in. |
| `PUID`, `PGID` | Who owns `timetap-data`. Timetap hands the folder to this user and runs as it; 1000 when left out. |
| `TIMETAP_ADDRESS` | This computer's address on your network, e.g. `192.168.1.20`. Only needed for https. |

## Updating

```bash
docker compose pull && docker compose up -d
```

The data folder stays as it is. IT > Software shows which version is running.

## https

On Docker, IT > Secure address offers **your own domain** (at Cloudflare, free) - see [https](https.md). The
`name.timetap.no` addresses are for the Raspberry Pi. If you already run a reverse proxy (Nginx Proxy Manager, Traefik,
Caddy, ...), you can put Timetap behind it instead and leave Timetap's own https off.
