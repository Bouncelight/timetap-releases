# Timetap on Unraid

Tested. You get the web page and the iPhone app; the NFC readers need the [Raspberry Pi](raspberry-pi.md).

Timetap isn't in Unraid's **Apps** yet, so the template goes on the server with one command first. After that it is
installed like any other app.

## 1. Add the template

On Unraid's web page, click the terminal icon (`>_`, top right) and paste:

```bash
mkdir -p /boot/config/plugins/dockerMan/templates-user && curl -fsSL -o /boot/config/plugins/dockerMan/templates-user/my-timetap.xml https://raw.githubusercontent.com/Bouncelight/timetap-releases/main/unraid/timetap.xml
```

Close the terminal.

## 2. Install

1. **Docker** > **Add Container**.
2. **Template:** pick **timetap** under *User templates*. Everything is filled in.
3. Change the port only if 8088 is taken. **Apply**.

## 3. Log in

Click the Timetap icon on the Docker page > **Logs**. The first login (**Admin** and a password) is printed there once.
Click the icon > **WebUI**, or open `http://<unraid-address>:8088`. Change the password under **Account**.

## Good to know

* **Data:** `/mnt/user/appdata/timetap` - the database, backups and settings. Include it in your appdata backups.
* **Updating:** Docker > the Timetap icon > **Check for updates**, then **apply update**. The data stays.
* **https:** fill in *This server's address* (Unraid's IP address) in the template, then see [https](https.md).
* The files belong to PUID 99 / PGID 100, Unraid's usual for appdata (under *Show more settings*).
