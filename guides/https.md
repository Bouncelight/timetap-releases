# A secure address (https)

Timetap works on plain http on your own network from the start. A secure address - `https://yourname.timetap.no` -
is trusted by every browser and iPhone with nothing to install on them. It is needed for installing reader software
from the web page, and makes the iPhone app and logins safer. Set it up on **IT > Secure address**.

The address only works on your own network (it points at the server's local address); Timetap isn't put on the
internet.

## A Timetap address (Raspberry Pi)

The simple way: no account, no domain.

1. **IT > Secure address** > **A Timetap address**.
2. Type a name - it becomes `name.timetap.no`. The page says whether it is free.
3. Type your **invitation code** and click **Get this address**. A code works once, for one name. If you didn't get
   one with your Timetap, email [code@timetap.no](mailto:code@timetap.no) and say which name you'd like.
4. Click **Get the certificate**. It takes about a minute.
5. **Test from this computer**, then **Send everyone to the secure address**.

After that the server renews the certificate by itself, and keeps the name pointed at it if its address changes. The
server keeps only the secret for its own name; it is in the backup, so a restored server keeps the name. A name that
isn't used for six months is released.

## Your own domain (Raspberry Pi and Docker)

If you have a domain, its DNS can be at Cloudflare (free):

1. **Cloudflare:** add your domain, on the Free plan. At the company you bought the domain from, switch to Cloudflare's
   two name servers and wait until Cloudflare says *Active*.
2. **Cloudflare:** My Profile > **API Tokens** > **Create Token** > template **Edit zone DNS** > your domain >
   **Create Token**. Copy it.
3. **IT > Secure address** > **Your own domain**: a name under your domain (e.g. `timetap.yourcompany.no`), the
   token, **Save**, then **Get the certificate**.
4. **Test from this computer**, then **Send everyone to the secure address**.

On Docker, set `TIMETAP_ADDRESS` to the server's address on your network first (see [Docker](docker.md)), and open
the https port (443, or the one you mapped to 8443).

## Good to know

* The readers keep plain http on the Timetap WiFi; they don't need https.
* If an address stops working right after you moved it, your computer may remember the old answer for up to half an
  hour. Waiting fixes it.
