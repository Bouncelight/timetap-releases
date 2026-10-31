# Backups, and starting over on a new server

## Every night, on the server

Timetap saves a copy of everything each night, on the server itself. **IT > Backup & restore** lists them:
**Download backup** for a copy now, **Restore from file…** to put one back.

A backup holds everyone's hours and logins - keep the files private.

## Off the server (do this)

A copy on the server doesn't help if the server dies. **IT > Backup off the server** copies an encrypted backup every
night to a NAS, Jottacloud, or anything [rclone](https://rclone.org) reaches:

1. **Add a destination…** and fill in where it goes.
2. Choose a **passphrase** the first time. **Keep it in a password manager**: it is never shown again, and without it
   the copies can't be opened.
3. **Back up now** to check that it works.

It keeps one copy for each of the last 30 days, then one a month, and opens each again to check it (*verified*).

On Docker you can also back up the data folder itself (Unraid's appdata backup, Synology's Hyper Backup, a Proxmox
backup).

## Starting over on a new server

1. Install Timetap on the new server, as the first time (the [Pi guide](raspberry-pi.md), or Docker).
2. Log in with the new first login.
3. Put the backup back, one of two ways:
   * **IT > Backup & restore** > **Restore from file…**: the backup file (a `.tfbackup` from your NAS or cloud), and
     its passphrase.
   * **IT > Backup off the server** > add the same destination as before > **Restore**, pick a backup, and its
     passphrase.
4. It shows what is in the backup (people, projects, the latest entry); type **RESTORE** to replace everything.

Everyone logs in as before. Readers: if a reader doesn't come back by itself, make a new setup card for it
([readers](readers.md)).
