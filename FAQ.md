# Network Tools — FAQ

Most of what follows is not a missing feature. iOS closes certain doors to every app on the App
Store, and this one would rather say so than pretend.

## Why is there no Wi-Fi signal strength, channel, or list of nearby networks?

Because no App Store app can read them. The public API publishes a network's name, its BSSID and its
security type, and nothing else — there is no signal strength in it, no channel, and no way to scan
for other networks. `CoreWLAN`, which does all of that on a Mac, is not in the iOS SDK at all.

So instead of an invented dBm figure, the Wi-Fi screen measures what can actually be measured: the
round trip to your router, its jitter and loss, graded against thresholds meant for a link to your
own gateway rather than to the internet. The walking survey uses the same measurement to compare one
room with another, which is the question people usually have.

## Why doesn't the LAN scan show each device's MAC address?

The ARP cache — where a device's MAC address would come from — cannot be read from inside the iOS
sandbox. Apple's own developer support says so. An app that shows you one is either on a jailbroken
phone or showing you something else.

The scan identifies devices by the names they answer to instead: Bonjour, reverse mDNS, reverse DNS
and NetBIOS are all asked, and the row says which one answered, so you can judge the name.

The **MAC lookup** tool still works fully — it identifies the vendor behind any address you type or
paste, from a 39,000-entry registry bundled in the app, entirely offline.

## Why can't the scan find a device I know is there?

A host that ignores ping and refuses every port probed cannot be seen from an app, because finding
it would need ARP. Printers asleep, devices with a strict firewall, and some IoT gadgets behave this
way. The scan says so at the bottom of its results rather than leaving you guessing.

## I set up an SSH key on my old phone. Why isn't it on the new one?

By design. Private keys are held in the Keychain marked `WhenUnlockedThisDeviceOnly`, which means
they are never copied into the iCloud Keychain and never restored onto another device. A key that
could travel silently through a backup is a key you have lost track of.

To move one deliberately, open **SSH → keys**, long-press the key and choose **Export**. You can put
a passphrase on it on the way out. On the far end, save it in `~/.ssh/` and `chmod 600` it — ssh
ignores a key file that others can read, and complains about the key rather than the permissions.

## Why does connecting with a passphrase-protected key pause for a moment?

Because the format is meant to be slow. OpenSSH protects a key file with `bcrypt`, run tens of
thousands of times, precisely so that guessing the passphrase is expensive. The pause is that work,
and it happens once per use.

## Why is the SSH host key question asked again?

It is asked once per server, the first time you connect, and the fingerprint you accept is
remembered. If it is asked again for a server you have used, the key has genuinely changed — the
screen shows both fingerprints. That means the server was rebuilt, or something is sitting between
you and it. The app will not guess which; only you can know.

## Is there an iPad version?

Not yet. The app runs on iPhone only for now. Every screen was laid out for a phone, and shipping
them stretched across an iPad would be worse than waiting.

## Why doesn't the app follow the Larger Text setting?

Deliberately, for now. The monospaced tables, the 32-bit binary columns in the IP calculator and the
terminal grid all depend on a character being exactly the width it is; text that resizes would break
the alignment those screens exist for. It is on the list, and it is a redesign rather than a
setting.

## Why does the terminal show different colours from my Mac?

Inside a session the far end chooses the colours — that is your shell's and your programs' doing,
not the app's. Only the frame around the terminal follows the theme you picked in Settings.

## Does the app send anything anywhere?

Only where you point it. The one tool with a destination you did not choose is the speed test, which
needs a far end and uses Cloudflare's public endpoints unless you give it a URL of your own. See
[PRIVACY.md](PRIVACY.md).

## Something else

[Open an issue](https://github.com/pkhorenyan/networktools-support/issues), or email
**pavelkhorenyan@gmail.com**.
