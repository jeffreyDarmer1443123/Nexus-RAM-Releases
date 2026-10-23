# Nexus RAM

Roblox account manager for Windows. Nexus RAM manages your **own** Roblox accounts locally on your
PC, launches games through the official Roblox client – including several accounts one after
another – and arranges the Roblox windows on your monitors. No cloud, no account with the developer,
no telemetry.

This repository contains the **installers, updates and documentation**. The source code is
maintained separately.

**[⬇ Download the latest version](https://github.com/jeffreyDarmer1443123/Nexus-RAM-Releases/releases/latest)**
– file `Nexus.RAM_<version>_x64-setup.exe`

## Quick start

1. Requirements: Windows 10 or 11 (64-bit) and the installed [Roblox Player](https://www.roblox.com/download).
2. Download and run the installer. If Windows SmartScreen warns you, choose
   “More info” → “Run anyway” (explained in the [installation guide](docs/installation.md#windows-smartscreen)).
3. Start Nexus RAM and go through the setup assistant. The interface is in English; German can be
   chosen under **Settings → General → Language**.
4. Under **Accounts → Add account**, add your first account – the easiest way is
   “Sign in through Roblox”.
5. Under **Launcher**, enter a place ID or a Roblox link, select accounts and launch.

## Documentation

| Chapter | Contents |
| --- | --- |
| [Installation](docs/installation.md) | Download, SmartScreen, installation, upgrading from Nexus RAM 0.x, checksums, uninstalling |
| [Getting started](docs/getting-started.md) | Setup assistant, layout of the interface, bringing over data from 0.x |
| [Managing accounts](docs/accounts.md) | All ways to add accounts, statuses, sorting, favorites, multi-select |
| [Groups and launch templates](docs/groups-and-templates.md) | Bundling accounts, saving recurring launches |
| [Launching games](docs/launching-games.md) | Launcher, supported links, launches, several clients at once |
| [Sessions and windows](docs/sessions-and-windows.md) | Running clients, closing, auto-rejoin, anti-AFK, arranging windows |
| [Settings](docs/settings.md) | Every setting with its default and allowed range |
| [Data, backups and security](docs/data-and-security.md) | Storage locations, vault, backups, snapshots, privacy, network destinations |
| [Updates](docs/updates.md) | How updates are checked and installed safely |
| [Troubleshooting and FAQ](docs/troubleshooting.md) | Common messages, causes and solutions |
| [Changelog](CHANGELOG.md) | What changed in which version |

## Important notes

- Only manage accounts that **belong to you**. Session values (`.ROBLOSECURITY`) are like passwords –
  never share them.
- Roblox does **not officially** support several clients at the same time. Nexus RAM makes it
  possible by closing the handle to `ROBLOX_singletonEvent` in the client it launched itself
  (can be turned off). This may conflict with the Roblox terms of use; use at your own risk.
- Nexus RAM does not read browser data and does not bypass CAPTCHAs or two-step verification.
