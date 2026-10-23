# Getting started

[← Overview](../README.md)

> **Language:** Nexus RAM starts in German. Switch to English under
> **Einstellungen → Allgemein → Sprache → English** and click **Speichern**. All labels in this
> documentation refer to the English interface.

## Setup assistant

On first start, an assistant guides you through five steps. **Skip** ends it at any time; everything
can be done later in the settings.

| Step | What happens |
| --- | --- |
| **Security** | Short rules: own accounts only, never share session values, no CAPTCHA bypassing, multiple clients are not officially supported by Roblox. |
| **Roblox** | Nexus RAM checks whether the Roblox Player is installed and shows the detected version. |
| **Data** | Shows the data folder. As long as no account exists, you can choose another folder here (Nexus RAM restarts afterwards). |
| **Migration** | If Nexus RAM finds data from version 0.x, you can bring it over here (see below). |
| **First account** | Opens the “Add account” dialog directly – or click “Get started”. |

## Layout of the interface

**Sidebar (left)** – the sections, also reachable with `Ctrl+1` … `Ctrl+8`:

| Section | Purpose |
| --- | --- |
| Overview | Key figures, quick launch, accounts that need attention, running clients, launches, recent events |
| Accounts | Manage, add and launch all accounts |
| Groups | Combine accounts into groups |
| Launcher | Launch games, launch templates, launches |
| Sessions | Running Roblox clients, closing, auto-rejoin |
| Windows | Arrange Roblox windows, save layouts |
| Activity | Log of all events |
| Settings | All options, backups, updates |

The sidebar can be collapsed with the icon at the bottom left.

**Top bar:**

- **Search field** (`Ctrl+K`) – searches username, display name, alias and notes as well as the exact
  user ID, and jumps to the account list.
- **Live strip** – shows the profile pictures of all running clients launched by Nexus RAM; hovering
  shows name, uptime and memory. A click brings that account’s Roblox window to the front. Next to
  it you see how many **other** Roblox clients are running (not launched by Nexus RAM).
- **Launches** – while launches are running, a hint with their number.
- **CPU / RAM** – load of your PC.

## Bringing over data from Nexus RAM 0.x

Nexus RAM 1.x has its own database. Data of the old version 0.x is **not** taken over automatically,
only on request – either in the setup assistant or later under
**Settings → Data & security → Data from Nexus RAM 0.x**.

1. **Look for data** – shows what was found: number of accounts, sessions, groups, templates and
   layouts. A copy is read for this; the old data is not changed.
2. **Bring over data** – after confirming, the following is taken over: accounts (including alias,
   notes, favorites, order), sessions, groups, launch templates, window layouts, saved window
   positions, the latest events and the settings.

Good to know:

- Beforehand, the old files are copied completely into the `migration` subfolder of the data folder
  and the new database is backed up. The originals in `%APPDATA%\com.nexusram.app` remain unchanged.
- **Close the old app first.** If it is still running, Nexus RAM tells you, so no changes get lost.
- Accounts that already exist (same Roblox user ID) remain unchanged and are skipped. Running the
  migration a second time is therefore harmless.
- Sessions are bound to your **Windows user account**. If the old data comes from another Windows
  account or PC, everything except the sessions is brought over; add the sessions again afterwards.
- Encrypted backups from 0.x (`.nxbackup`) can also be read via
  [Import backup](data-and-security.md#import-a-backup).

## Next steps

- [Add accounts](accounts.md)
- [Launch a game](launching-games.md)
