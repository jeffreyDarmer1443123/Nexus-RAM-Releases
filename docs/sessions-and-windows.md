# Sessions and windows

[← Overview](../README.md)

## Sessions

The **Sessions** section shows all running Roblox clients in two tables:

- **Launched by Nexus RAM** – with account, game, PID, uptime, CPU and memory.
- **Other Roblox clients** – not launched by Nexus RAM, not assigned to any account.

The values update continuously (interval under Settings → Launcher → Process monitoring). Your own
sessions are still recognized as your own after Nexus RAM restarts, as long as the client keeps
running.

### Actions

| Action | Where | Effect |
| --- | --- | --- |
| Focus | Icon in the row | Brings the Roblox window to the front |
| Minimize | Icon in the row | Minimizes the window |
| Restore | “⋯” menu | Restores a minimized window |
| Enable/Disable auto-rejoin | “⋯” menu (own sessions only, when auto-rejoin is turned on) | Watch the session, see below |
| Close | “⋯” menu, or select + **Close selection** | Ends Roblox regularly (see below) |
| Force quit | “⋯” menu (own sessions only) | Ends the process immediately – unsaved game progress may be lost |
| Minimize all | Top right | Minimizes all own Roblox windows |

**Close** first sends Roblox the normal request to quit. If the client is still running after
5 seconds (Roblox sometimes stays in the background), exactly this process is ended. The message
tells you how many were closed regularly and how many were ended. You are asked before closing
(can be turned off under Settings → Launcher → “Confirm closing sessions”). Other clients can be
closed but never force-quit.

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

## Anti-AFK

Roblox kicks idle players after about 20 minutes. Anti-AFK prevents this by regularly triggering a
jump (space bar) in each of **your own** Roblox windows.

- Turn on: Settings → Launcher → **Anti-AFK** (default: off).
- Interval: default 120 s per window (10–1800 s).
- It only triggers when you have not used mouse or keyboard for at least 2 seconds and are not
  holding a key. Afterwards your previous window is brought back to the front; minimized Roblox
  windows are minimized again.
- Other Roblox clients and other programs never receive input.
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
