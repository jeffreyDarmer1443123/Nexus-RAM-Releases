# Settings

[← Overview](../README.md)

**Settings** has six tabs. In the first four, changes only take effect after **Save**; **Discard**
restores the saved state. Invalid values are rejected with a message when saving.

## General

| Setting | Default | Values / note |
| --- | --- | --- |
| Language | German | German (Deutsch), English |
| Appearance | Dark | Dark, Light, Like Windows |
| Accent color | Orange | 8 colors to choose from |
| Start with Windows | off | Starts Nexus RAM minimized to the notification area when you sign in to Windows |
| Minimize to the notification area when closing | off | The ✕ only hides the window; Nexus RAM keeps running in the notification area (bottom right of the taskbar) |
| Notifications | on | Windows notifications for client started/ended, failed launch, sign-in errors and updates – only while the window is hidden |
| Check for updates on start | on | See [Updates](updates.md) |
| Log level | info | error, warn, info, debug – how detailed the log file is |

**Notification-area icon:** right-click offers **Nexus RAM öffnen** (open), **Alle Starts abbrechen**
(cancel all launches) and **Beenden** (quit). These three menu items are currently always shown in
German.

## Accounts

| Setting | Default | Values / note |
| --- | --- | --- |
| Default sort | Custom order | Custom order, Username, Display name, Recently launched, Date added, Status |
| Default view | Tiles | Tiles, Table |
| Groups | Sidebar | Group filter as a sidebar or as chips |
| Avatar cache (hours) | 24 | 1–720 – how long profile pictures are cached |
| Check sessions on start | off | Checks all stored sessions one by one with a pause; stops on rate limits |
| Roblox OAuth client ID | empty | Only for [OAuth confirmation](accounts.md#confirm-with-roblox-oauth) |
| OAuth port | 53682 | 1024–65535 – port of the local callback `http://localhost:<port>/callback` |

## Launcher

| Setting | Default | Values / note |
| --- | --- | --- |
| Launch interval (s) | 8 | 1–300 – fallback only, see [Launch order](launching-games.md#launch-order-and-launch-interval) |
| Parallel launches | 1 | 1–10 |
| Default place ID | empty | Pre-filled in the launch form |
| When a launch fails | Continue other launches | or: Cancel remaining launches |
| Retries on network errors | 1 | 0–5 |
| Confirm closing sessions | on | Asks before closing Roblox |
| Process monitoring (s) | 2 | 1–10 – how often processes, CPU and memory are updated |
| Allow multiple clients | on | Closes `ROBLOX_singletonEvent` in the own client, see [Several clients](launching-games.md#several-clients-at-the-same-time) |
| Allow a probe for parallel clients | off | On the next second launch, checks whether both clients keep running |
| Anti-AFK | off | See [Anti-AFK](sessions-and-windows.md#anti-afk) |
| Interval (s) | 120 | 10–1800 |
| Auto-rejoin | off | See [Auto-rejoin](sessions-and-windows.md#auto-rejoin) |
| Behavior | Ask | Ask, Automatic |
| Maximum attempts | 3 | 1–10 |
| Wait time (s) | 15 | 5–600 – starting value, doubles with each attempt (max. 10 min) |

## Windows

| Setting | Default | Values / note |
| --- | --- | --- |
| Preferred monitor | Primary monitor | Target for arranging when no other monitor is chosen |
| Default layout | Grid | None, Grid, Side by side, Stacked |
| Window gap (px) | 8 | 0–200 |
| Margin (px) | 8 | 0–400 |
| Remember window position per account | on | Restores position and size on the next launch |

## Data & security

Data folder, vault status, encrypted backups, automatic snapshots, migration from 0.x and maintenance
(check integrity, clear cache, export diagnostics) – described in detail under
[Data, backups and security](data-and-security.md).

## About & updates

Version, detected Roblox Player, checking for and installing updates, the full list of network
destinations and all keyboard shortcuts – see [Updates](updates.md) and
[Network destinations](data-and-security.md#network-destinations).
