# Data, backups and security

[← Overview](../README.md)

All functions in this chapter are found under **Settings → Data & security**.

## Where is my data stored?

Default data folder: `%APPDATA%\com.nexusram2.app` (button **Open folder**)

| File / folder | Contents |
| --- | --- |
| `nexus-ram-2.db` (+ `-wal`, `-shm`) | Database: accounts, groups, templates, layouts, settings, activity |
| `vault.key` | Vault key, bound to your user account by Windows |
| `logs\` | Log files (without session values, passwords or tokens) |
| `snapshots\` | [Automatic snapshots](#automatic-snapshots) of the database |
| `migration\` | Copies of the old data from Nexus RAM 0.x, if brought over |

**Change the data folder:** only while **no account** is stored yet (setup assistant or **Change**
next to the path). Nexus RAM restarts afterwards. Network drives, system folders and drive roots
(e.g. `C:\`) are not allowed.

## How are sessions protected?

- Session values are stored only in the **vault**: encrypted with AES-256-GCM, each entry
  inseparably bound to its account.
- The key for it is bound to your Windows user account with **Windows DPAPI**. On another PC or under
  another Windows account the sessions therefore cannot be decrypted – use a
  [backup with sessions](#create-a-backup) for that.
- Stored sessions are **never** shown again, never written to the log and only sent to the Roblox
  API.
- The vault status shows how the key is protected and how many sessions are stored.

**Limit:** Malware running under your Windows account can in principle access anything you can
decrypt yourself – this applies to every application. Keep Windows and your antivirus up to date.

## Create a backup

**Create backup** saves an encrypted file (`.nxbackup`) with accounts, groups, launch templates,
window layouts and settings.

1. Choose a **location**.
2. Enter a **passphrase** (at least 12 characters) and repeat it. Without the passphrase the backup
   cannot be read – a forgotten passphrase cannot be recovered.
3. Optionally **Include stored sessions** – then also confirm the risk. Anyone who has the file
   **and** the passphrase can sign in with these accounts.
4. **Create backup**.

Encryption: Argon2id (key derivation from the passphrase) + AES-256-GCM.

## Import a backup

1. **Import backup** → choose the file, enter the passphrase.
2. Choose the **mode**:
   - **Merge** – existing accounts stay, new ones are added.
   - **Replace** – all current data is replaced by the backup. The current state is backed up
     automatically first. No clients may be running and no launches may be active.
3. **Import**.

Wrong passphrases and modified or damaged files are detected – nothing changes in that case.
Backups from **Nexus RAM 0.x** can be imported as well.

## Automatic snapshots

Before every import in “Replace” mode, before every restore and before every data migration, Nexus
RAM backs up the database automatically. **Back up now** creates a snapshot yourself. The
**10 most recent** snapshots are kept.

**Restore** replaces the current state with the chosen snapshot – the current state is backed up
first. No clients may be running and no launches may be active.

> Snapshots are stored in the same data folder and protect against mistakes, not against losing the
> PC. That is what the [backup](#create-a-backup) is for.

## Maintenance

| Function | Effect |
| --- | --- |
| **Check integrity** | Checks the database and whether all stored sessions can be decrypted |
| **Clear cache** | Deletes cached profile pictures, game names, finished launches and the Roblox detection |
| **Export diagnostics** | Saves a JSON file for troubleshooting: version, Roblox installation, settings, recent events, log excerpt – **without** session values, passwords or tokens |

## Privacy

- No telemetry, no analytics, no account with the developer. Your data only leaves the PC towards
  Roblox (for the app’s functions) and GitHub (only for the update check, without user data).
- Nexus RAM does not read browser data or passwords of other programs.

## Network destinations

Nexus RAM connects exclusively to these addresses (also listed under
**Settings → About & updates**):

| Destination | Purpose |
| --- | --- |
| `users.roblox.com`, `auth.roblox.com`, `games.roblox.com`, `thumbnails.roblox.com`, `apis.roblox.com` | Roblox API: profiles, session checks, sign-in ticket, game names, profile pictures, share links, OAuth |
| `*.rbxcdn.com` | Profile pictures (display only) |
| `www.roblox.com` | The own sign-in window |
| `github.com` (+ `objects.githubusercontent.com`) | Update check and download, signed |
| `127.0.0.1` | Local OAuth callback only |

All connections use HTTPS with certificate verification (except the local callback).
