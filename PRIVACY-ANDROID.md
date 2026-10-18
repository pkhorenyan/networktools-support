# Privacy Policy — Network Tools for Android

**Last updated: 18 October 2026**

Network Tools collects nothing about you. There is no account, no sign-in, no analytics, no
advertising, no tracking, and no third-party SDK of any kind in the app.

This is the policy for the Android app (package `com.pkd.nettools`). The iPhone app has its own,
[PRIVACY.md](PRIVACY.md). Everything below can be checked against the app's behaviour.

## Data we collect

**None.** In Google Play's Data safety section this app is declared as collecting no data and
sharing no data.

We — the developer — have no server, no database and no logs. Nothing you do in the app is sent
anywhere we can see, because there is nowhere for it to go.

## Data the app stores on your phone

All of it stays on the phone, and all of it is removed when you uninstall the app.

| what | where |
|---|---|
| Hosts you have run a tool against, saved SSH and telnet connections, known SSH host keys, Wake on LAN machines, Wi-Fi survey spots, command snippets, your settings | the app's own private storage |
| SSH passwords, and private keys — whether generated in the app or imported | the app's private storage, encrypted with a key held in the Android Keystore that never leaves the phone; excluded from Android's backup and device transfer |
| Files you fetch with `scp`, and packet recordings you choose to save | the `Download/Network Tools` folder, visible to you in the Files app |
| A packet recording while it is being made | the app's private cache, until you save or share it or start another |

Android may include the app's settings and saved hosts in your own Google backup, as it does for
any app. Passwords and keys are never part of it.

## Network connections the app makes

Every network request the app makes is one you started, by typing a target and pressing a button.
Where it goes is where you pointed it — a host you named, a server you saved, a subnet on your own
network.

A few tools reach destinations the app chooses rather than you, and they are named here:

- **Speed test.** Throughput cannot be measured without a far end, and there is no server of ours,
  so it uses Cloudflare's public speed endpoints (`speed.cloudflare.com`). The screen says so while
  it runs. You can point the test at a URL of your own instead, and then nothing goes to Cloudflare.
- **DNS.** Lookups go to whichever resolver you pick or type in yourself. The comparison mode asks
  several well-known public resolvers at once so their answers can be compared; they are named on
  screen before you run it.
- **WHOIS.** A lookup starts at IANA and follows the referrals IANA gives to the registry and
  registrar that hold the record. Every server asked is listed in the result.
- **Wi-Fi network checks.** When you run them, the app asks Cloudflare's captive-portal address
  (`cp.cloudflare.com`) whether the network lets traffic through, and opens a connection — nothing is
  sent over it — to cloudflare.com, github.com, one.one.one.one, imap.gmail.com and smtp.gmail.com
  to see which ports the network allows. The hosts are listed on screen.

The organisations behind those addresses see the request as they would from any app, under their
own privacy policies. Nothing else phones home. The MAC vendor database is bundled inside the app and
works with no network at all.

## Permissions, and what each one is for

- **Local network** (Android 17 and later). Lets the app find and measure devices on the network
  you are on — LAN scan, Wake on LAN, SSH or ping to a local address. What it finds is shown to you
  and stored on your phone. Refuse it, and those tools find nothing; everything else works.
- **Location.** Android shows nearby Wi-Fi networks and mobile cells only to apps holding precise
  location, so two views ask for it: Wi-Fi's channel view and the Cellular tool's cell list. **The
  app never reads your position**, and nothing they show leaves the phone. Everything else in those
  tools works without it.
- **Usage access** (switched on by you in Android's settings). Lets App traffic's *Data used* view
  read how many bytes each app on the phone has moved, from Android's own network statistics. It
  reads nothing else about how you use your apps, and the figures stay on the phone.
- **Notifications.** A long scan, an SSH or telnet session, a port forward or a file transfer keeps
  running while you use other apps; its notification shows what is running, with a Stop or
  Disconnect button.

## App traffic and the VPN it uses

App traffic shows what each app on your phone connects to and looks up. To see that, it uses
Android's VPN service — but **the VPN ends on your phone itself**. Nothing is sent to a VPN server,
ours or anyone's.

- In **Everything** mode, the apps' internet connections pass through Network Tools, which carries
  each one on to the destination the other app chose, over the network you are already on. It reads
  only what says where a connection goes — the address, the name in the TLS or QUIC handshake or the
  HTTP `Host` line — and counts its bytes. **It does not decrypt, alter, block or redirect anything.**
  Traffic to your local network is not routed through it.
- In **Lookups only** mode, only DNS lookups pass through it, and each goes unchanged to your
  network's own DNS servers.
- What it sees stays in the app's memory and is gone when you clear it or close the app. Nothing of
  it is sent anywhere.
- **Recording packets** is off unless you switch it on before starting. When on, the packets that
  pass are written to a file in the app's private cache, which leaves it only if you tap Save (to
  your Download folder) or Share. The next recording replaces it.
- It starts only when you tap Start watching, shows a notification while it runs, and stops when you
  tap Stop.

## Children

Network Tools is a professional tool for adults and is not directed at children. It collects no
data from anyone, of any age.

## Changes to this policy

If it ever changes, the new version will appear at this address and the date at the top will move.

## Contact

Questions about this policy: **pavelkhorenyan@gmail.com**, or
[open an issue](https://github.com/pkhorenyan/networktools-support/issues).
