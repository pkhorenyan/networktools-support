# Privacy Policy — Network Tools

**Last updated: 19 August 2026**

Network Tools collects nothing about you. There is no account, no sign-in, no analytics, no
advertising, no tracking, and no third-party SDK of any kind in the app.

This policy is short because there is little to describe. Everything below can be checked against
the app's behaviour.

## Data we collect

**None.** In App Store Connect this app is declared **Data Not Collected**, and the privacy manifest
bundled inside it declares no tracking and no collected data types.

We — the developer — have no server, no database and no logs. Nothing you do in the app is sent
anywhere we can see, because there is nowhere for it to go.

## Data the app stores on your device

All of it stays on the iPhone, and all of it is removed when you delete the app.

| what | where |
|---|---|
| Hosts you have run a tool against, saved SSH and telnet connections, Wake on LAN machines, Wi-Fi survey spots, command snippets, your chosen theme | the app's own preferences, on the device |
| SSH passwords, and private keys — whether generated in the app or imported | the iOS **Keychain**, marked `WhenUnlockedThisDeviceOnly` |
| Files you fetch with `scp` | the app's Documents folder, which is visible to you in the Files app |

`WhenUnlockedThisDeviceOnly` means those secrets are readable only while the phone is unlocked, are
**never** placed in the iCloud Keychain, and are **never** restored onto a different device. That is
also why the app offers an Export command for keys: it is the only way to move one to another
machine, and the file it produces goes wherever you send it.

## Network connections the app makes

Every network request the app makes is one you started, by typing a target and pressing a button.
Where it goes is where you pointed it — a host you named, a server you saved, a subnet on your own
network.

Three tools reach destinations the app chooses rather than you, and it is worth naming them:

- **Speed test.** Throughput cannot be measured without a far end, and there is no server of ours,
  so it uses Cloudflare's public speed endpoints (`speed.cloudflare.com`). The screen says so while
  it runs. You can point the test at a URL of your own instead, and then nothing goes to Cloudflare.
  Cloudflare's handling of that request is governed by their own privacy policy.
- **DNS.** Lookups go to whichever resolver you pick from the list or type in yourself. The
  comparison mode deliberately asks several well-known public resolvers at once so their answers can
  be compared; they are named on screen before you run it.
- **WHOIS.** A lookup starts at IANA and follows the referrals IANA gives to the registry and
  registrar that hold the record. Every server asked is listed in the result.

Nothing else phones home. The MAC vendor database is bundled inside the app and works with no
network at all.

## Local Network access

iOS asks your permission the first time the app looks at the network you are on. The app needs it to
list the devices on your own subnet, measure whether they answer, and see which services they
expose. What it finds is shown to you and stored on your device. It is not transmitted anywhere.

If you refuse the permission, the scanning tools simply find nothing; everything else still works.

## Children

The app is rated 4+ and contains nothing directed at children. It collects no data from anyone, of
any age.

## Changes to this policy

If it ever changes, the new version will appear at this address and the date at the top will move.

## Contact

Questions about this policy: **pavelkhorenyan@gmail.com**, or
[open an issue](https://github.com/pkhorenyan/networktools-support/issues).
