# The NFC readers

A reader is a small box you can put wherever it's needed - by the door, at your desk, in the workshop: people tap
their tag to clock in and out, and tap a project tag to switch project. Readers work with every kind of Timetap server. On a [Raspberry Pi](raspberry-pi.md) with the *Timetap WiFi* they get a
network of their own; otherwise - Docker, or a Pi without a USB WiFi adapter - they join your normal WiFi (2.4 GHz).

## What a reader is made of

* A **Seeed Studio XIAO ESP32S3** (the small computer).
* A **PN532** NFC board.
* Optionally a **Waveshare 2.13" e-ink display** (V4) that shows names and messages.

**Tags:** NTAG213 or NTAG215, as cards, key fobs or stickers. Card-sized ones read most reliably. Avoid metal cards
and tags stuck on metal: metal blocks NFC.

## Before you start

* The server has a **secure address** - see [https](https.md). Browsers only let a web page talk to USB with https.
* **Chrome, Chromium or Edge** on a computer - Linux, Mac or Windows (not Safari or Firefox) - and a USB-C cable that
  carries data. On Linux your user may need to be in the `dialout` group to reach the USB port
  (`sudo usermod -aG dialout $USER`, then log out and in).
* Readers on your **normal WiFi** (not the Timetap WiFi): IT > Readers > *Where readers may connect from* must include
  that network (on Docker it does from the start: every local network).

## 1. Install and set up the reader over USB

1. **IT > Readers** > **Install the reader software**.
2. Plug the reader into the computer. For a brand-new board, tick **Put MicroPython on it first**.
3. Keep **Set it up too** ticked and give it a name (e.g. `front-door`):
   * On a Pi with the Timetap WiFi, that's all - it joins the Timetap WiFi.
   * Otherwise, type the **WiFi** it joins and its password, and **this server's address** and http **port** as the
     reader will reach it (e.g. `192.168.1.20` and `80`, or `8088` on Unraid).
4. **Install on a reader…**, pick the reader in the list the browser shows, and **Continue**.
5. The reader restarts, joins the WiFi and shows up on IT > Readers within a minute or two.

If the reader isn't found or doesn't answer: put it in install mode with the two tiny buttons on the small board, next
to the USB plug - hold **B**, press and let go of **R**, then let go of **B** - and try again.

## 2. Or: a setup card

On a Pi with the Timetap WiFi, once one reader works, the next ones can also be set up with a **setup card** - handy
when the new reader is far from a computer. Install the software without *Set it up too*; the reader's screen then says **Tap a setup card**.

1. **IT > Readers** > **Set up a new reader**: type a name and choose which reader writes the card (*Written on*: the
   Pi's own reader, or a reader that already works).
2. **Make a setup card**, then tap a blank card on that reader within two minutes.
3. Tap the card on the new reader. It joins the WiFi, takes its name and starts.
4. **Wipe a card** afterwards: the card holds the WiFi password.

## 3. Tags for people and projects

1. Tap a tag on any reader. It shows up on **Admin > Recent taps**.
2. **Pair a tag:** pick the person or project, press **Use** on the tag, then **Pair tag**.

Anyone can have several tags. A lost tag: open the person and remove it.

## Updates

The readers fetch new software from the server by themselves after Timetap is updated, and restart. If an update doesn't
work, a reader goes back to its previous software and IT > Readers says *Update failed*.
