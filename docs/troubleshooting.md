# Troubleshooting and FAQ

[← Overview](../README.md)

Error messages in Nexus RAM name the cause and – for technical errors – a **diagnostic code** (e.g.
`E_NETWORK`, list [below](#diagnostic-codes)). All events are also listed in the **Activity**
section.

> **Note on language:** Error messages and activity entries are currently always shown in **German**,
> even with the English interface. This page quotes the German text (as it appears in the app) with an
> English translation.

## Common problems

### Windows blocks the installer (“Windows protected your PC”)
The installer is not signed with a code-signing certificate. “More info” → “Run anyway”. Details:
[Installation](installation.md#windows-smartscreen).

### Roblox Player not found
*„Roblox ist nicht installiert oder der Protokollhandler wurde nicht gefunden.“* (Roblox is not
installed or the protocol handler was not found.)

Nexus RAM finds the Roblox Player via its registration in Windows.
1. Install the Roblox Player from [roblox.com/download](https://www.roblox.com/download) and start it
   once normally.
2. Restart Nexus RAM or use **Settings → Data & security → Clear cache**.

A third-party bootstrapper registered as the Roblox handler is used unchanged.

### Status “Session expired” (`E_SESSION_EXPIRED`)
Roblox ended the session – e.g. through “Log out of all sessions”, a password change or long
inactivity. Right-click the account → **Add session** and sign in again.

### Status “Check required” (`E_CHALLENGE_REQUIRED`)
Roblox requires an interactive confirmation (e.g. CAPTCHA). Nexus RAM does not bypass such checks.
Sign in again via **Add session → Sign in through Roblox**.

### “Rate limited” (`E_RATE_LIMITED`)
Roblox temporarily limits requests. Wait a few minutes; bulk imports and session checks stop by
themselves in this case.

### The second client closes the first one
- Check **Settings → Launcher → Allow multiple clients** (must be on).
- In the **Activity** section, look for warnings such as
  *„ROBLOX_singletonEvent konnte nicht geschlossen werden“* (could not be closed) or
  *„ROBLOX_singletonEvent nicht gefunden“* (not found) – they name the PID and the reason.
- Roblox updates can change the behavior. Roblox does not officially support several clients; there
  is no guarantee.

### “The game client does not support this parallel execution” (`E_UNSUPPORTED`)
*„Der Spielclient unterstützt diese parallele Ausführung nicht.“* – For the installed Roblox version
it was proven (by a probe) that no second client is possible. Launch a single account (it then
replaces the running client) or close the running client first. After a Roblox update this is
checked again.

### Roblox was called but no game client process was detected (`E_PROCESS`)
*„Roblox wurde aufgerufen, aber es wurde kein Spielclient-Prozess erkannt.“* – Roblox refused the
launch or is installing an update. Wait a moment and launch again. Check whether Roblox starts
normally from the website.

### A client is already running for this account
*„Für diesen Account läuft bereits ein … Client.“* – Nexus RAM launches at most one client per
account. Close it first under **Sessions**.

### Launches take as long as the launch interval
Normally the next account launches as soon as the previous one is ready. If every launch takes as
long as the configured launch interval, `ROBLOX_singletonEvent` could not be closed (see Activity) or
“Allow multiple clients” is off. See
[Launch order](launching-games.md#launch-order-and-launch-interval).

### Anti-AFK does not jump
Anti-AFK waits until you have not used mouse or keyboard for at least 2 seconds and are not holding
a key. It only acts on clients launched by Nexus RAM.

### Auto-rejoin does not relaunch
- Is auto-rejoin turned on in the settings **and** is the session marked as watched?
- Did you close the client yourself through Nexus RAM? Then no rejoin is intended.
- At the top of the **Sessions** section: is the rejoin paused or abandoned? The reason is shown
  next to it; **Resume** continues it.

### Sessions can no longer be read after changing PC or Windows account
The vault key is bound to your Windows account. Transfer accounts with a
[backup including sessions](data-and-security.md#create-a-backup).

### The migration finds no data from Nexus RAM 0.x
Nexus RAM looks in `%APPDATA%\com.nexusram.app` (also when 0.x redirected its data to another
folder from there). If the old data was deleted when uninstalling, use a `.nxbackup` backup from 0.x
via **Import backup**.

### No update notice
Check “Check for updates on start” and your internet connection, or check manually under
**Settings → About & updates**. See [Updates](updates.md).

### Nexus RAM does not start
If *„Nexus RAM konnte nicht starten“* (Nexus RAM could not start) appears, the reason is in the
message. Log files are in `%APPDATA%\com.nexusram2.app\logs`. Only one instance runs at a time: a
second start brings the existing window to the front – also check the notification area.

## Reporting problems

**Settings → Data & security → Export diagnostics** creates a JSON file without session values,
passwords or tokens. It contains the version, Roblox installation, settings, recent events and a log
excerpt and helps with troubleshooting.

## FAQ

**Is this allowed?**
Nexus RAM uses Roblox’s official paths (sign-in page, sign-in ticket, official client). Several
clients at the same time and simulated input (anti-AFK) are not officially supported by Roblox and
may conflict with the terms of use. Both can be turned off; anti-AFK is off by default. Use at your
own risk.

**Does Nexus RAM store my passwords?**
No. Only session values are stored, encrypted in the vault. With “Sign-ins from file”, passwords are
only used for pre-filling and are not stored.

**Does Nexus RAM need administrator rights?**
No – neither for installing nor for running.

**Is any data sent to the developer?**
No. See [Privacy and network destinations](data-and-security.md#privacy).

**Can I use Nexus RAM on several PCs?**
Yes, each installation has its own data. You can transfer it with an encrypted backup.

**Can I use Nexus RAM 0.x and 1.x side by side?**
Both share the product name and installation folder; the 1.x installer replaces 0.x. The data is
kept separately; the old data can be brought over.

## Diagnostic codes

| Code | Meaning |
| --- | --- |
| `E_VALIDATION` | Invalid input |
| `E_NOT_FOUND` | Something was not found |
| `E_CONFLICT` | Conflicts with the current state (e.g. account already saved, client already running) |
| `E_NETWORK` | Connection problem |
| `E_REJECTED` | Roblox rejected the request |
| `E_RATE_LIMITED` | Roblox limits requests |
| `E_SESSION_EXPIRED` | Session expired or invalid |
| `E_CHALLENGE_REQUIRED` | Roblox requires a security check |
| `E_NO_SESSION` | No session stored for the account |
| `E_ROBLOX_NOT_INSTALLED` | Roblox Player not found |
| `E_UNSUPPORTED` | Operation not possible this way (e.g. second client blocked) |
| `E_CANCELLED` | Cancelled |
| `E_PROCESS` | Problem with a Roblox process or window |
| `E_BACKUP_AUTH` | Backup damaged, modified or wrong passphrase |
| `E_BACKUP` | Other backup error |
| `E_UPDATE` | Update could not be checked or installed |
| `E_SECRET_STORE` | Problem with the vault |
| `E_DATABASE` | Database error |
| `E_IO` / `E_PERMISSION` | File or access problem |
| `E_TIMEOUT` | Timeout |
| `E_MIGRATION` | Data migration failed |
| `E_INTERNAL` | Unexpected error – please export diagnostics |
