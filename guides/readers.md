# The NFC readers

A reader is a small box by the door: people tap their tag to clock in and out, and tap a project tag to switch
project. Readers work with the [Raspberry Pi](raspberry-pi.md) setup: they join the Pi's own Timetap WiFi.

## What a reader is made of

* A **Seeed Studio XIAO ESP32S3** (the small computer).
* A **PN532** NFC board.
* Optionally a **Waveshare 2.13" e-ink display** (V4) that shows names and messages.

**Tags:** NTAG213 or NTAG215, as cards, key fobs or stickers. Card-sized ones read most reliably. Avoid metal cards
and tags stuck on metal: metal blocks NFC.

## Before you start

* The Pi has the **Timetap WiFi** running (the installer offers it; later: the command it printed).
* The server has a **secure address** - see [https](https.md). Browsers only let a web page talk to USB with https.
* **Chrome or Edge** on a computer (not Safari or Firefox), and a USB-C cable that carries data.

## 1. Put the software on the reader

1. **IT > Readers** > **Install the reader software**.
2. Plug the reader into the computer. For a brand-new board, tick **Put MicroPython on it first**.
3. **Install on a reader…**, pick the reader in the list the browser shows, and **Continue**.
4. When it is done, the reader's screen says **Tap a setup card**.

If the reader isn't found or doesn't answer: put it in install mode with the two tiny buttons on the small board, next
to the USB plug - hold **B**, press and let go of **R**, then let go of **B** - and try again.

## 2. A setup card

The setup card tells the new reader the WiFi password and its name.

1. **IT > Readers** > **Set up a new reader**: type a name (e.g. `front door`) and choose which reader writes the card
   (*Written on*: the Pi's own reader, or a reader that already works).
2. **Make a setup card**, then tap a blank card on that reader within two minutes.
3. Tap the card on the new reader. It joins the Timetap WiFi, takes its name and starts.
4. **Wipe a card** afterwards: the card holds the WiFi password.

The new reader shows up on IT > Readers within a few minutes.

## 3. Tags for people and projects

1. Tap a tag on any reader. It shows up on **Admin > Recent taps**.
2. **Pair a tag:** pick the person or project, press **Use** on the tag, then **Pair tag**.

Anyone can have several tags. A lost tag: open the person and remove it.

## Updates

The readers fetch new software from the Pi by themselves after Timetap is updated, and restart. If an update doesn't
work, a reader goes back to its previous software and IT > Readers says *Update failed*.
