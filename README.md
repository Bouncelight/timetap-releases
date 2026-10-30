# Timetap releases

Timetap is a small time-tracking server for a workplace: people clock in and out with NFC tags on readers, on a web
page, or with the iPhone app. It runs on a Raspberry Pi on the company's own network.

This repository only holds the finished, signed releases (see **Releases** on the right). A running Timetap updates
itself from here when someone presses **Install** on its IT page. Each release comes with:

- `timetap-X.Y.Z.tar.gz` - the program (server, web page, reader software)
- `timetap-X.Y.Z.tar.gz.sha256` - its fingerprint
- `timetap-X.Y.Z.tar.gz.sig` - its Ed25519 signature; Timetap refuses a release whose signature doesn't match

Installing a new Pi with one line is coming here soon.
