# Installation

[← Overview](../README.md)

## System requirements

| | |
| --- | --- |
| Operating system | Windows 10 or Windows 11, 64-bit |
| Roblox | Installed Roblox Player ([roblox.com/download](https://www.roblox.com/download)). You can manage accounts without Roblox, but launching requires it. |
| Permissions | No administrator rights needed – Nexus RAM is installed for your Windows user only. |
| Disk space | about 250 MB (the installer includes the WebView2 runtime so nothing has to be downloaded) |
| Internet | For signing in, launching games, profile pictures and updates |

## Download

Open the [latest version](https://github.com/jeffreyDarmer1443123/Nexus-RAM-Releases/releases/latest)
and download the right file under **Assets**:

| File | Purpose |
| --- | --- |
| `Nexus.RAM_<version>_x64-setup.exe` | **Recommended.** Regular installer. |
| `Nexus.RAM_<version>_x64_de-DE.msi` / `…_en-US.msi` | Alternative in MSI format (e.g. for software deployment). |
| `*.sig` | Signatures for automatic updates – not meant to be downloaded. |
| `latest.json` | Update information for installed versions. |
| `SHA256SUMS.txt` | Checksums of all files (see [Verify the download](#verify-the-download-optional)). |

## Windows SmartScreen

When you run the installer for the first time, Windows often shows
**“Windows protected your PC”**. This happens because the installer is not signed with a paid
code-signing certificate – not because anything harmful was found.

1. Click **“More info”**.
2. Choose **“Run anyway”**.

If you want to be sure, check the checksum first (next section).

## Verify the download (optional)

Every release contains `SHA256SUMS.txt`. Compare the value of your downloaded file with the line in
that file. In PowerShell:

```powershell
Get-FileHash "$env:USERPROFILE\Downloads\Nexus.RAM_1.0.1_x64-setup.exe" -Algorithm SHA256
```

The printed value (upper/lower case does not matter) must match the entry in `SHA256SUMS.txt`. If it
differs, do not run the file and download it again.

## Install

1. Run `Nexus.RAM_<version>_x64-setup.exe`. The installer appears in the language of your Windows
   (German or English).
2. Follow the assistant.
3. On the last page you can start Nexus RAM right away. Afterwards you find it in the Start menu.

Installation folder: `%LOCALAPPDATA%\Nexus RAM`

> The app starts in **English**. You can switch to German under **Settings → General → Language**,
> then click **Save**. An existing installation keeps the language you chose before.

## Upgrading from Nexus RAM 0.x

If the older version **Nexus RAM 0.x** is installed:

- The installer **replaces the old program** (same product name, same installation folder).
  Windows may ask whether the existing version should be uninstalled first – that is fine.
- If you are offered to **delete app data, do not tick it.** Otherwise your old accounts are lost
  before you could bring them over.
- Your old data stays in `%APPDATA%\com.nexusram.app`. Nexus RAM only reads it there and brings it
  over on request – see [Bringing over data from Nexus RAM 0.x](getting-started.md#bringing-over-data-from-nexus-ram-0x).

## Uninstall

1. **Windows Settings → Apps → Installed apps → Nexus RAM → Uninstall**.
2. If you also want to delete all accounts and settings, remove these folders afterwards (if they
   still exist):

| Folder | Contents |
| --- | --- |
| `%APPDATA%\com.nexusram2.app` | Database, encrypted sessions, vault key, logs, snapshots |
| `%LOCALAPPDATA%\com.nexusram2.app` | Interface cache |

> `com.nexusram2.app` is the internal identifier of Nexus RAM 1.x. The folder
> `%APPDATA%\com.nexusram.app` (without “2”) belongs to the old version 0.x.

Tip: Create an encrypted backup first under **Settings → Data & security → Create backup** in case
you need the accounts again later.
