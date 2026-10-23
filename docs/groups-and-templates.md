# Groups and launch templates

[← Overview](../README.md)

## Groups

Groups combine accounts – for example all accounts for a certain game.

**Groups → New group**

| Field | Meaning |
| --- | --- |
| Name | max. 40 characters, unique |
| Color | Color tag in lists and filters |
| Icon | Small icon in front of the name |
| Launch template | Optional: a [launch template](#launch-templates) that “Launch template” runs |

On the groups page you see each group’s accounts with their status and can:

- **Launch group** – opens the launch dialog with all ready accounts of the group.
- **Launch template** – runs the linked launch template directly.
- change the order of the groups with the arrows, edit or delete a group.

Assign accounts via right-click → **Move to group** (also for several selected accounts at once) or
when adding or editing them. When a group is deleted, its accounts are kept and then appear under
“No group”.

## Launch templates

A launch template stores a recurring launch: which game, which accounts, with which interval – and
how the windows are arranged afterwards.

**Launcher → Launch templates → New template**

| Field | Meaning |
| --- | --- |
| Name | max. 60 characters |
| Place ID | The game (number from the Roblox link, e.g. `1818`) |
| Private server link | Optional: link containing `privateServerLinkCode=…` |
| Group | Optional: all accounts of this group are launched too – including those added to the group later |
| Launch interval (s) | 1–300 s; fallback value, see [Launch order](launching-games.md#launch-order-and-launch-interval) |
| Parallel launches | 1–10 |
| Layout | None, Grid, Side by side or Stacked – the windows are arranged this way automatically after launching |
| Accounts | Individually selected accounts, in addition to the group |

In the template list you can **Launch**, **Edit**, **Duplicate** or **Delete** each template.

When a template is launched, only accounts with a valid session that are not already running are
included; skipped accounts are named in the message. If a layout is chosen, Nexus RAM arranges the
windows once all launches of the template are finished – using monitor, gap and margin from the
[window settings](settings.md#windows).
