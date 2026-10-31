# Updating Timetap

## Raspberry Pi

**IT > Software** > **Check for updates**. If there is a new version, the page shows what is new; press **Install**.

Timetap downloads the new version, checks its signature, saves a copy of the database and restarts - about a minute,
while the page, readers and app pause. If the new version doesn't start, the previous one comes back by itself. The
readers then fetch their new software on their own.

Nothing is updated by itself: only when someone presses Install. *Check for updates* asks GitHub which versions exist,
only when you press it.

### The Pi's own system

Raspberry Pi OS is updated separately. When security updates are waiting, Timetap shows a notice. Log in to the Pi
(`ssh yourname@timetap.local`) and run:

```bash
sudo apt update && sudo apt full-upgrade -y
```

If the notice then asks for a restart: `sudo reboot`. The readers are offline for that minute.

## Docker

The IT page shows the version; updating is done in Docker:

* **Docker Compose:** `docker compose pull && docker compose up -d`
* **Unraid:** Docker > the Timetap icon > **Check for updates** > **apply update**.
* **Synology, QNAP, Proxmox:** see their guides.

The data folder stays as it is.

## What changed

Each release lists what is new, in plain words: on the IT page before installing, and on the
[Releases](https://github.com/Bouncelight/timetap-releases/releases) page.
