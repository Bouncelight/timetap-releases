# Timetap on a QNAP NAS

> **Not tested yet.** Written from QNAP's documentation. If you try it, please
> [tell us how it went](https://github.com/Bouncelight/timetap-releases/issues) - corrections are welcome.

Needs **Container Station** (QTS 5 or QuTS hero, a model with an Intel, AMD or 64-bit ARM processor). You get the web
page, the iPhone app and [NFC readers](readers.md) join your normal WiFi.

## 1. A folder for Timetap

1. **App Center:** install **Container Station** if it isn't there.
2. **File Station:** in the `Container` shared folder, make a folder `timetap`.

## 2. The application

1. **Container Station** > **Applications** > **Create**.
2. **Application name:** `timetap`. Paste:

```yaml
services:
  timetap:
    image: ghcr.io/bouncelight/timetap:latest
    restart: unless-stopped
    ports:
      - "8088:8080"   # the web page - QTS itself uses 8080, 80 and 443
      - "8443:8443"   # https, once it is set up
    volumes:
      - /share/Container/timetap:/data
    environment:
      TZ: Europe/Oslo
      # Only for https: this NAS's IP address on your network
      # TIMETAP_ADDRESS: 192.168.1.20
```

3. **Validate**, then **Create**. Container Station downloads the image and starts Timetap.

## 3. Log in

**Container Station** > **Containers** > `timetap...` > **Logs**: the first login (**Admin** and a password) is
printed there once. Open `http://<nas-address>:8088` and change the password under **Account**.

## Good to know

* **Data:** `Container/timetap`. Include it in **Hybrid Backup Sync**.
* **Updating:** **Container Station** > **Applications** > `timetap` > the menu (⋯) > **Recreate**, with "pull the
  latest image" ticked.
* If the port is taken, change `8088` to another free port and use that in the address.
