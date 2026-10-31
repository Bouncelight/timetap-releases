# Backups, and starting over on a new server

## Every night, on the server

Timetap saves a copy of everything each night, on the server itself. **IT > Backup & restore** lists them:
**Download backup** for a copy now, **Restore from file…** to put one back.

A backup holds everyone's hours and logins - keep the files private.

## Off the server (do this)

A copy on the server doesn't help if the server dies. **IT > Backup off the server** copies an encrypted backup every
night to a NAS on your network, or to Jottacloud:

1. **Set passphrase…** first: Timetap makes one for you (or type your own). **Save it in a password manager** - see
   *The passphrase* below.
2. **Add a destination…** and fill in where it goes. Timetap writes a small test file to check it can.
3. **Back up now** to check that everything works.

### What is in each backup

**Every backup is complete**: the whole database - everyone's hours, projects, absences, people and logins, tags,
rules and settings - plus the Timetap WiFi's name and password (so the readers find their network again), and the
Timetap address's secret. To get everything back you only need **one** backup: the newest.

The program itself isn't in it; you install that again (it's free and downloads in a minute).

### Which copies are kept

One copy for **each of the last 30 days**, then **one a month** for older ones. Each copy is opened again after it is
made, to check that it can be restored - the card shows *verified*. Older copies are there in case something went
wrong without anyone noticing (hours deleted by mistake two weeks ago, say).

### The passphrase

The backups are encrypted with your **passphrase** (AES-256): without it, a copy is just noise - to the NAS, to
Jottacloud, and to anyone who gets hold of the file. That is the point, and it is also the catch:

* **Keep it in a password manager**, or written down somewhere safe away from the server. Timetap shows it once, when
  it is set, and never again.
* The server keeps it too, so the nightly copies work - but if the server dies, so does that copy. **You need your
  own copy to restore.**
* **Lost it?** As long as the server works: set a new one (*Change…*) and *Back up now* - the new copies use the new
  passphrase. Copies made with the old one can't be opened without it.
* Changing it doesn't re-encrypt older copies: they still need the passphrase they were made with.

On Docker you can also back up the data folder itself (Unraid's appdata backup, Synology's Hyper Backup, a Proxmox
backup). Those copies aren't encrypted - keep them somewhere private.

## Starting over on a new server

1. Install Timetap on the new server, as the first time (the [Pi guide](raspberry-pi.md), or Docker).
2. Log in with the new first login.
3. Put the backup back - the newest one holds everything - one of two ways:
   * **IT > Backup & restore** > **Restore from file…**: the backup file (a `.tfbackup` from your NAS or cloud), and
     its passphrase.
   * **IT > Backup off the server** > add the same destination as before > **Restore**, pick a backup, and its
     passphrase.
4. It shows what is in the backup (people, projects, the latest entry); type **RESTORE** to replace everything.

Everyone logs in as before. Readers: if a reader doesn't come back by itself, make a new setup card for it
([readers](readers.md)).
