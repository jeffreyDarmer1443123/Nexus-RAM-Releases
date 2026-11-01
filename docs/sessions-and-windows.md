# Sessions and windows

[← Overview](../README.md)

## Sessions

The **Sessions** section shows all running Roblox clients in two tables:

- **Launched by Nexus RAM** – with account, game, PID, uptime, CPU and memory.
- **Other Roblox clients** – not launched by Nexus RAM, not assigned to any account. You can
  [manage](#managing-other-clients) them in Nexus RAM.

The values update continuously (interval under Settings → Launcher → Process monitoring). Your own
sessions are still recognized as your own after Nexus RAM restarts, as long as the client keeps
running.

### Actions

| Action | Where | Effect |
| --- | --- | --- |
| Focus | Icon in the row | Brings the Roblox window to the front |
| Minimize | Icon in the row | Minimizes the window |
| Restore | “Actions” menu (“⋯”) | Restores a minimized window |
| Manage in Nexus RAM / Stop managing | “Actions” menu (other clients only) | See [Managing other clients](#managing-other-clients) |
| Enable/Disable auto-rejoin | “⋯” menu (own sessions only, when auto-rejoin is turned on) | Watch the session, see below |
| Problem tag | Next to the account name | “Connection lost” or “Not responding”, see [Problem detection](#problem-detection) |
| Close | “⋯” menu, or select + **Close selection** | Ends Roblox regularly (see below) |
| Force quit | “⋯” menu (own sessions only) | Ends the process immediately – unsaved game progress may be lost |
| Anti-AFK for all | Top right (when anti-AFK is on) | Resets the anti-AFK timer of all own and managed clients, see [Anti-AFK](#anti-afk) |
| Minimize all | Top right | Minimizes all own Roblox windows |

**Close** first sends Roblox the normal request to quit. If the client is still running after
5 seconds (Roblox sometimes stays in the background), exactly this process is ended. The message
tells you how many were closed regularly and how many were ended. You are asked before closing
(can be turned off under Settings → Launcher → “Confirm closing sessions”). Other clients can be
closed but never force-quit.

## Managing other clients

Roblox clients you started yourself – for example from the browser – appear under **Other Roblox
clients**. You can include them in Nexus RAM without assigning an account:

1. Open the **Actions** menu (“⋯”) of the client and choose **Manage in Nexus RAM**.
2. Confirm the dialog. Nexus RAM then
   - removes the lock that prevents further Roblox clients (`ROBLOX_singletonEvent`), so more
     accounts can run next to it. This only happens when **Allow multiple clients** is on
     (Settings → Launcher); otherwise the message offers to open the settings. The lock cannot be
     restored.
   - includes the client in [anti-AFK](#anti-afk).
3. The row now shows the tag **Managed**.

**Stop managing** in the same menu only ends anti-AFK; the lock stays removed.

Good to know:

- Managed clients are never force-quit by Nexus RAM. Problem detection, saved window positions and
  auto-rejoin stay limited to clients launched by Nexus RAM.
- The selection survives a restart of Nexus RAM as long as the same client keeps running. When the
  client ends, it is removed automatically.
- Up to 32 clients can be managed at the same time.

## Auto-rejoin

Auto-rejoin launches an account again when its client ends **unexpectedly** – for example after a
disconnect.

**Turn on:** Settings → Launcher → **Auto-rejoin**. After that it only applies to sessions you mark
as **watched**:

- when launching: tick “Enable auto-rejoin for these launches”, or
- later: Sessions → “⋯” menu → **Enable auto-rejoin**.

Watched sessions carry the “Auto-rejoin” tag.

| Behavior | What happens |
| --- | --- |
| **Ask** (default) | The message “Watched session ended – Join again?” appears with a **Join again** button. |
| **Automatic** | After a waiting time, the account is relaunched automatically. The waiting time starts at the configured value (default 15 s) and doubles with each attempt, up to 10 minutes. After the maximum number of attempts (default 3), auto-rejoin gives up. |

The same target is launched again – the same game, the same server or private server.

Auto-rejoin does **not** trigger when you close the client yourself through Nexus RAM. It **pauses**
automatically when a relaunch would be pointless: expired session, confirmation request from Roblox,
rate limit, missing session, Roblox not installed or launch not supported. Running, paused or
abandoned rejoins are shown at the top of the Sessions section, where you can **cancel** or
**resume** them.

## Problem detection

A client that lost its connection usually stays open and just shows Roblox’s error dialog – the
process does not end, so auto-rejoin alone would not notice it. Nexus RAM therefore checks every
5 seconds whether a client it launched is stuck:

| Problem | How it is detected | Tag at the session |
| --- | --- | --- |
| **Lost connection** | From the log file Roblox writes for each client (`%LOCALAPPDATA%\Roblox\logs`, read-only). A disconnect counts only when Roblox logs an error code (e.g. 277) and no new join follows within 20 seconds. Teleports, leaving the game normally and text written by games are ignored. | “Connection lost” with the error code |
| **Frozen** | Windows reports the Roblox window as “not responding” without a break for the configured time (default 90 s). | “Not responding” |

**What happens then:**

- Always: the tag in the Sessions section, an entry in the activity log and – if enabled – a
  notification.
- **Session watched by auto-rejoin** with behavior **Automatic**, attempts left and another client
  allowed: the stuck client is ended and auto-rejoin relaunches it.
- **Otherwise** – for example with behavior **Ask** – the client keeps running. Reconnect in Roblox’s own dialog (the tag disappears by
  itself) or use “⋯” → **Force quit** and launch the account again.

Good to know:

- Nexus RAM only reads the log files; it does not access the Roblox process itself. Log contents
  are neither stored nor sent anywhere.
- A log file is only assigned to a session when the match is unique (time in the file name ↔ client
  start). If two clients start within about 5 seconds of each other, those sessions are not checked
  for lost connections; freeze detection still works.
- Turn off or adjust: Settings → Launcher → **Problem detection**.

## Anti-AFK

Roblox kicks idle players after about 20 minutes. Anti-AFK prevents this by regularly triggering a
jump (space bar) in each of **your own** Roblox windows and in clients you
[manage](#managing-other-clients).

- Turn on: Settings → Launcher → **Anti-AFK** (default: off).
- Interval: default 120 s per window (10–1800 s).
- It only triggers when you have not used mouse or keyboard for at least 2 seconds and are not
  holding a key. If a jump is due while you are busy, it follows as soon as you have been idle for
  2 seconds. Afterwards your previous window is brought back to the front; minimized Roblox
  windows are minimized again.
- Each window has its own timer, which starts when the window appears. To bring all clients onto
  one schedule, click **Anti-AFK for all** in the Sessions section: every client jumps once, one
  after another, as soon as you leave mouse and keyboard alone for 2 seconds. From then on they all
  jump together in each interval.
- Other Roblox clients that you have not managed, and other programs, never receive input.
- Anti-AFK skips windows that do not respond and tries again on the next pass.
- Simulated input may conflict with the Roblox terms of use.

## Arranging windows

The **Windows** section lists all open Roblox windows (your own and others; minimized ones are
marked). Per window: **Focus**, **Minimize** or **Restore**.

**Arrange:**

1. Select windows (tick boxes) – without a selection, **all** Roblox windows are arranged.
2. Choose a **layout**:
   - **Grid** – an even grid,
   - **Side by side** – columns,
   - **Stacked** – rows.
3. Choose the **monitor** – in the list or by clicking a monitor in the true-to-scale
   **monitor preview**. The preview shows all monitors and the current position of the windows.
4. **Gap** between the windows and **margin** to the screen edge, in pixels.
5. **“Arrange N”**.

The taskbar, DPI scaling and a minimum size of 320×240 pixels are respected. If there is not enough
room, the windows overlap (a hint appears). Other programs are never changed. If a single window
cannot be moved, the others are arranged anyway.

**Saved layouts:** enter a name → **Save** stores layout, monitor, gap and margin. **Apply** loads a
saved layout and applies it immediately; the trash icon deletes it.

**Window position per account:** If “Remember window position per account” is on under Settings →
Windows (default), Nexus RAM remembers the position and size of each Roblox window and restores them
the next time that account is launched.
