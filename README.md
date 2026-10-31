# Timetap

Timetap keeps track of working hours and projects for a small workplace. People clock in and out by tapping an NFC
tag on a reader, on a web page, or with the iPhone app. It runs on your own network - a Raspberry Pi in the office or
your own server - and your hours stay there.

**Timetap Lite** is the simple edition: hours, projects, a balance against each person's weekly hours, and
absence (holiday, sick, time off). The full edition adds the Norwegian working-time rules: overtime, the time bank,
holiday planning and approval, sick-leave counters and working-time checks. You choose on the IT page and can switch
at any time.

## Install

| Where | Guide | |
|---|---|---|
| Raspberry Pi | [Raspberry Pi](guides/raspberry-pi.md) | The complete setup, with NFC readers |
| Docker, anywhere | [Docker](guides/docker.md) | Any Linux computer or server with Docker |
| Unraid | [Unraid](guides/unraid.md) | Tested |
| Synology | [Synology](guides/synology.md) | Not tested yet |
| QNAP | [QNAP](guides/qnap.md) | Not tested yet |
| Proxmox | [Proxmox](guides/proxmox.md) | Not tested yet |

NFC readers work with all of them. On a Raspberry Pi they can have their own Timetap WiFi; elsewhere they join your
normal WiFi.

## After installing

* [A secure address (https)](guides/https.md) - `https://yourname.timetap.no`, trusted by every browser and iPhone
* [The NFC readers](guides/readers.md) - set up a new reader from the web page
* [The iPhone app](guides/iphone.md)
* [Updating](guides/updating.md) - from the IT page, one button
* [Backups and starting over on a new server](guides/backups.md)

## What is in this repository

The finished, signed releases (see **Releases**) and these guides. A running Timetap updates itself from here when
someone presses **Install** on its IT page. Each release comes with:

- `timetap-X.Y.Z.tar.gz` - the program (server, web page, reader software)
- `timetap-X.Y.Z.tar.gz.sha256` - its fingerprint
- `timetap-X.Y.Z.tar.gz.sig` - its signature; Timetap refuses a release whose signature doesn't match
- `install.sh` - the one-line installer for a Raspberry Pi, and `docker-compose.yml` for Docker

The Docker image is `ghcr.io/bouncelight/timetap`.

Questions and problems: [open an issue](https://github.com/Bouncelight/timetap-releases/issues), or email
[contact@timetap.no](mailto:contact@timetap.no). Invitation codes for a Timetap address: [code@timetap.no](mailto:code@timetap.no).
