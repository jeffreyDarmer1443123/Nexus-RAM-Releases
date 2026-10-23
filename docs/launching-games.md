# Launching games

[← Overview](../README.md)

Nexus RAM launches Roblox the same way as the “Play” button on roblox.com: using the stored session,
it requests a short-lived sign-in ticket from Roblox and hands it to the **official Roblox client**.
Each launched client is uniquely assigned to its account by process ID and start time.

## Where can I launch?

| Place | How |
| --- | --- |
| **Launcher** | Full launch form, launch templates and launches |
| **Overview → Quick launch** | Compact form |
| **Accounts** | Select accounts → right-click → **Launch** or `Ctrl+L` |
| **Groups** | **Launch group** or **Launch template** |
| **Launch templates** | **Launch** next to the template |

## The launch form

| Field | Meaning |
| --- | --- |
| **Game** | Place ID or Roblox link (see below). Nexus RAM checks the input right away and shows the game name. |
| **Server ID** (optional) | GUID of a specific server to join exactly that one. Only together with a plain place ID. |
| **Accounts** | Selection with filter field, “Select all” and “Ready only”. Accounts without a session or with a running client are skipped. |
| **Launch interval (s)** | Fallback value only – see [Launch order](#launch-order-and-launch-interval). Default from the settings. |
| **Parallel launches** | How many launches are prepared at the same time (1–10). Applies to launches, not to running clients. |
| **Enable auto-rejoin for these launches** | Only visible when auto-rejoin is turned on in the settings. The launched sessions are watched ([Auto-rejoin](sessions-and-windows.md#auto-rejoin)). |

The **“Launch N”** button creates one launch per account.

### Supported input in the “Game” field

| Input | Example |
| --- | --- |
| Place ID | `1818` |
| Game link | `https://www.roblox.com/games/1818/Classic-Crossroads` |
| Link with language path | `https://www.roblox.com/de/games/1818/…` |
| Start link | `https://www.roblox.com/games/start?placeId=920587237` |
| Private server | `https://www.roblox.com/games/1818/…?privateServerLinkCode=…` |
| Share link of a server | `https://www.roblox.com/share?code=…&type=Server` |
| Specific server | `https://www.roblox.com/games/1818/…?gameInstanceId=<GUID>` |

Only place IDs and links to `https://www.roblox.com` (also `roblox.com` and `web.roblox.com`) are
allowed. Other addresses, `http://`, profile links or share links for profiles are rejected.

## Launches

Every launch appears under **Launches** (Launcher, Overview) with a progress bar:

| State | Meaning |
| --- | --- |
| Waiting | Waiting for a free launch slot |
| Preparing | Checking account and Roblox installation |
| Signing in | Requesting the sign-in ticket from Roblox |
| Starting | Roblox is started and the new process is detected |
| Running | Client is running and assigned to the account |
| Failed | Launch not possible – the message gives the reason, possibly with a diagnostic code |
| Cancelled | Cancelled by you |
| Not supported | Launch not possible this way (e.g. second client verifiably blocked) |

- Cancel single launches with **✕**, all of them with **Cancel all** (also via the
  notification-area icon → **Alle Starts abbrechen** / cancel all launches).
- **Clear finished** tidies up the list.
- On network errors, Nexus RAM retries automatically (number in the settings, default
  1 retry). Expired sessions or confirmation requests from Roblox are **not** retried – the account
  gets the matching status.
- **When a launch fails**, the remaining launches continue by default; in the settings you can choose
  “Cancel remaining launches” instead.

## Launch order and launch interval

Clients are launched **one after another** so that every new process can be uniquely assigned to its
account. The waiting time between two launches is **negotiated automatically**:

1. Roblox starts and creates the object `ROBLOX_singletonEvent`.
2. Nexus RAM closes the handle to it in the client it just launched
   (setting “Allow multiple clients”, default: on).
3. **As soon as that has succeeded, the next account launches right away** (after a 0.25 s safety
   margin).

The **launch interval** (default 8 s) is only the fallback: it applies if the event could not be
found or closed, or if “Allow multiple clients” is turned off. Nexus RAM searches for the event at
most as long as the launch interval would take – so no launch is slower than with a fixed interval.

## Several clients at the same time

Roblox does **not officially** support several clients at the same time. Normally a new client
closes the running one. Nexus RAM makes several clients possible by closing the handle to
`ROBLOX_singletonEvent` **in the client it launched itself** after each launch:

- Only `RobloxPlayerBeta.exe` processes launched by Nexus RAM are touched, and only exactly this one
  handle. Other programs and other Roblox clients remain untouched.
- Can be turned off under **Settings → Launcher → Allow multiple clients**. Without this feature,
  Roblox usually closes the previously running client.
- Interfering with the Roblox process may conflict with the Roblox terms of use. Use at your own
  risk.

**Probe (optional):** With **Settings → Launcher → Allow a probe for parallel clients** (default: off),
Nexus RAM watches for a few seconds on the next second launch whether both clients keep running and
remembers the result for the installed Roblox version. If it is proven that Roblox does not allow a
second client, Nexus RAM does not launch further clients in a batch that would close the running
one. After a Roblox update, this is checked again.

## Other clients

Roblox clients that were not launched by Nexus RAM (e.g. via the website) appear as **other**
clients. They are shown but never assigned to an account, never force-quit and not touched by
anti-AFK or auto-rejoin.
