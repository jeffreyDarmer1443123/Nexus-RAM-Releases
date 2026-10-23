# Updates

[← Overview](../README.md)

## How updates reach you

1. On start, Nexus RAM asks GitHub whether a newer version exists
   (setting “Check for updates on start”, default: on).
2. If there is one, the hint **“Version X available”** appears.
3. Install: **Settings → About & updates** → **Install and restart** → confirm.
4. The download is shown with progress, verified and installed; Nexus RAM then restarts in the new
   version. Your accounts and settings are kept.

Without the automatic check you can check manually at any time under
**Settings → About & updates → Check for updates**.

Running launches are cancelled before installing; running Roblox clients are not affected.

## How updates are secured

An update is only installed if **all** checks pass:

| Check | Protects against |
| --- | --- |
| Source is `https://github.com` (TLS with certificate verification) | Redirection to foreign servers |
| **Minisign signature** with the public key built into Nexus RAM | Forged or manipulated installers – only updates signed with the publisher’s private key are accepted |
| **SHA-256 checksum** from the update information | Damaged or incomplete downloads |

If the checksum is missing or anything does not match, the update is **not** installed and a message
explains why. Installation runs without administrator rights, for your user account only.

## Update manually

You can download the latest installer from the
[release page](https://github.com/jeffreyDarmer1443123/Nexus-RAM-Releases/releases/latest) at any
time and install it over the existing installation. Data is kept.

Older versions are listed under
[all releases](https://github.com/jeffreyDarmer1443123/Nexus-RAM-Releases/releases). An older version
is never offered automatically; if you install one manually, a database that already comes from a
newer version may be refused (Nexus RAM then leaves it unchanged).
