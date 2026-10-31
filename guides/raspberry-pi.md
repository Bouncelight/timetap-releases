# Timetap on a Raspberry Pi

The Pi is the complete Timetap: the web page, the iPhone app's server, and its own WiFi for the NFC readers.

## What you need

* A **Raspberry Pi** that runs 64-bit Raspberry Pi OS: a Pi Zero 2 W, Pi 3, Pi 4 or Pi 5. A Pi Zero 2 W is plenty.
* A **microSD card** (16 GB or more) and a good power supply (5 V, 2.5 A for a Pi Zero 2 W).
* For NFC readers: a **USB WiFi adapter** that can be an access point on 2.4 GHz. The Pi's own WiFi stays on your
  network, and the adapter runs the Timetap WiFi the readers join. Without readers you don't need it.
* A computer with [Raspberry Pi Imager](https://www.raspberrypi.com/software/).

## 1. Put Raspberry Pi OS on the card

In Raspberry Pi Imager:

1. **Device:** your Pi. **Operating system:** Raspberry Pi OS (other) > **Raspberry Pi OS Lite (64-bit)**.
2. **Storage:** the microSD card.
3. **Edit settings** when it asks:
   * Host name: `timetap` - the address becomes `http://timetap.local`.
   * A user name and password of your choice (for logging in to the Pi itself, not Timetap).
   * Your WiFi name and password (or skip it and plug in a network cable).
   * Time zone and keyboard.
   * Under **Services**: turn on **SSH** with password login.
4. Write the card, put it in the Pi and switch it on. The first start takes a few minutes.

## 2. Install Timetap

Log in to the Pi from your computer. On a Mac, open Terminal; on Windows, PowerShell. Use the user name you chose:

```bash
ssh yourname@timetap.local
```

Then paste this line on the Pi and press Enter:

```bash
curl -fsSL https://github.com/Bouncelight/timetap-releases/releases/latest/download/install.sh | sudo bash
```

It installs what Timetap needs, downloads the latest release and checks its signature, and starts Timetap. It takes
5-10 minutes on a Pi Zero 2 W. If a USB WiFi adapter is plugged in, it offers to set up the **Timetap WiFi** for the
readers: answer `y` and choose a name and password for it (or do it later with the command it prints).

At the end it shows the address and the first login:

```
 Open:      http://timetap.local
 Log in:    Admin
 Password:  ...
```

**The password is shown only once.** Write it down, log in, and change it under **Account**.

## 3. Next steps

* **Admin:** add people and projects. Each person gets a login, and a tag if you use readers.
* **IT > Edition:** Timetap or Timetap Lite.
* **IT > Secure address:** [https](https.md), needed for the iPhone app outside the office and for installing readers.
* **IT > Backup off the server:** an encrypted copy on a NAS or in the cloud - see [Backups](backups.md).
* **IT > Readers:** [the NFC readers](readers.md).

Updates come from **IT > Software** - see [Updating](updating.md).

## If something goes wrong

* `timetap.local` isn't found: use the Pi's IP address instead (your router lists it), or wait a minute after it
  starts. On a Mac, Chrome may need permission: System Settings > Privacy & Security > Local Network.
* The installer stops with a message: it says what went wrong. Running it again is safe; on a Pi that already has
  Timetap it changes nothing.
* The server's own log: `journalctl -u timetap -n 50` on the Pi.
