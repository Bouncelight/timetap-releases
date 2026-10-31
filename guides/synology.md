# Timetap on a Synology NAS

> **Not tested yet.** Written from Synology's documentation. If you try it, please
> [tell us how it went](https://github.com/Bouncelight/timetap-releases/issues) - corrections are welcome.

Needs a Synology that runs **Container Manager** (DSM 7.2 or newer, most "plus" models with an Intel or AMD
processor, and some ARM models). You get the web page and the iPhone app; the NFC readers need the
[Raspberry Pi](raspberry-pi.md).

## 1. A folder for Timetap

1. **Package Center:** install **Container Manager** if it isn't there.
2. **File Station:** in the `docker` shared folder, make a folder `timetap`, and inside it a folder `data`.

## 2. The project

1. **Container Manager** > **Project** > **Create**.
2. **Project name:** `timetap`. **Path:** the `docker/timetap` folder.
3. **Source:** *Create docker-compose.yml*, and paste:

```yaml
services:
  timetap:
    image: ghcr.io/bouncelight/timetap:latest
    restart: unless-stopped
    ports:
      - "8088:8080"   # the web page - DSM itself uses 80 and 443
      - "8443:8443"   # https, once it is set up
    volumes:
      - ./data:/data
    environment:
      TZ: Europe/Oslo
      # Only for https: this NAS's IP address on your network
      # TIMETAP_ADDRESS: 192.168.1.20
```

4. **Next** (skip *Web portal settings*), **Done**. Container Manager downloads the image and starts Timetap.

## 3. Log in

**Container Manager** > **Container** > `timetap...` > **Log**: the first login (**Admin** and a password) is printed
there once. Open `http://<nas-address>:8088` and change the password under **Account**.

## Good to know

* **Data:** `docker/timetap/data`. Include it in **Hyper Backup**.
* **Updating:** **Container Manager** > **Project** > `timetap` > **Action** > **Build** (it downloads the newest
  image and restarts), or **Image** > the Timetap image > **Update** when one is offered.
* If the firewall is on: **Control Panel** > **Security** > **Firewall** - allow port 8088 (and 8443 for https).
