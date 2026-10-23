# Changelog

[← Overview](README.md)

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
