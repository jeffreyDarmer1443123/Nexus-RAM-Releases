# Changelog

[← Overview](README.md)

## 1.0.5 – 2026-11-01

- **Manage other Roblox clients:** clients you started yourself (for example from the browser) can
  now be included. Sessions → **Actions** → **Manage in Nexus RAM**, confirm, and Nexus RAM removes
  the lock that prevents further Roblox clients (when “Allow multiple clients” is on) and includes
  the client in anti-AFK. **Stop managing** only ends anti-AFK. Managed clients are never
  force-quit. See [Managing other clients](docs/sessions-and-windows.md#managing-other-clients).
- **Problem detection is more reliable:**
  - Nexus RAM now reads the actual Roblox log format, and text written by games is ignored.
  - A lost connection counts only when Roblox logs an error code (for example 277); teleports never
    count.
  - Clients launched a few seconds apart are matched to their log files correctly.
  - Nexus RAM only ends a stuck client when auto-rejoin can really relaunch it: automatic mode,
    attempts left, session saved, another client allowed. Otherwise the client keeps running.
- **Auto-rejoin:**
  - **Cancel** now also stops a launch that is already running.
  - Turning auto-rejoin off during the waiting time prevents the launch.
  - A slow launch no longer pauses auto-rejoin by mistake.
- **Frozen windows:** anti-AFK and saved window positions skip windows that do not respond.
- **Security hardening:**
  - Network and device paths are blocked in every file and folder selection.
  - Stricter limits apply when importing backups.
  - Events only reach the main window.
- **Accessibility:**
  - Confirmation dialogs read out their explanation and return the focus to where you were.
  - The action menus are named per row.
  - Notifications stay visible longer.

## 1.0.4 – 2026-10-27

- **Problem detection** for clients launched by Nexus RAM (Settings → Launcher → Problem
  detection, both on by default):
  - **Lost connection:** detected from the log files Roblox writes anyway (read-only). Teleports and
    leaving the game normally do not count – a disconnect counts only if no new join follows within
    20 seconds.
  - **Frozen client:** Windows keeps reporting the Roblox window as “not responding” (default
    90 seconds, adjustable 30–600).
- The session gets a “Connection lost (277)” or “Not responding” tag, plus an activity entry and a
  notification. For sessions watched by auto-rejoin, the stuck client is ended and auto-rejoin takes
  over (ask or automatic, as configured). See
  [Problem detection](docs/sessions-and-windows.md#problem-detection).

## 1.0.3 – 2026-10-26

- New button **Anti-AFK for all** in the Sessions section (shown while anti-AFK is on and clients
  launched by Nexus RAM are running). It resets the anti-AFK timer of every instance: all of them
  jump one after another as soon as you leave mouse and keyboard alone for 2 seconds, and from then
  on they stay on the same schedule. See [Anti-AFK](docs/sessions-and-windows.md#anti-afk).
- Fixed: if you were using mouse or keyboard at the moment a jump was due, that jump was postponed
  by a whole interval. It now follows as soon as you have been idle for 2 seconds.

## 1.0.2 – 2026-10-23

- New setting **Anonymize usernames** (Settings → General): shows a code such as “Account 3F9A”
  instead of usernames and display names and hides profile pictures and user IDs – everywhere in
  the app, including activity entries, error messages and notifications. Your own aliases stay
  visible. See [Hiding usernames](docs/accounts.md#hiding-usernames-streaming).
- New installations start in **English**. Existing installations keep their chosen language.

## 1.0.1 – 2026-10-23

- The activity log no longer shows handle messages (result of the handle diagnostics, successful
  closing of `ROBLOX_singletonEvent`). They are still written to the log file. Warnings when the event
  could not be closed remain visible.
- Existing handle messages are removed automatically on the first start and are not brought over
  during the migration from 0.x.

## 1.0.0 – 2026-10-23

First version of the completely rebuilt Nexus RAM.

- **Accounts:** sign-in through an own Roblox window, pasting a session, sessions and sign-ins from
  file, profile only, OAuth confirmation; status, favorites, groups, search, sorting, tile and table
  view, multi-select, keyboard shortcuts.
- **Launching:** place IDs, game, server, private server and share links; launches with progress and
  limited retries; launch templates with automatic window arrangement.
- **Several clients:** closes `ROBLOX_singletonEvent` in the client it launched itself (can be turned
  off). Launches are negotiated: the next account starts as soon as the previous one is ready; the
  launch interval is only a fallback.
- **Sessions:** own and other clients, focus, minimize, close, force-quit own clients, auto-rejoin,
  anti-AFK.
- **Windows:** arrange as grid, side by side or stacked with monitor preview, saved layouts, window
  position per account.
- **Data:** vault with AES-256-GCM and Windows DPAPI, encrypted backups, automatic snapshots with
  restore, migration from Nexus RAM 0.x, integrity check, diagnostics export without secrets.
- **Updates:** automatic check; installation only with a valid Minisign signature and matching
  SHA-256 checksum.
- Interface in German and English, dark and light theme, adjustable accent color.
