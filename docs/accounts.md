# Managing accounts

[← Overview](../README.md)

## Add an account

**Accounts → Add account** (or `Ctrl+N`). There are six ways:

| Method | Result | Can launch? |
| --- | --- | --- |
| [Sign in through Roblox](#sign-in-through-roblox) | Account with session | ✔ |
| [Paste your own session](#paste-your-own-session) | Account with session | ✔ |
| [Sessions from file](#sessions-from-file) | Many accounts with session | ✔ |
| [Sign-ins from file](#sign-ins-from-file) | Many accounts with session (you sign in one after another) | ✔ |
| [Save profile only](#save-profile-only) | Account without session | only after adding a session |
| [Confirm with Roblox OAuth](#confirm-with-roblox-oauth) | Account with confirmed identity, without session | only after adding a session |

With every method you can set an **alias**, **notes** and a **group** right away. Each Roblox account
(user ID) exists only once: if you add a session for an account that already exists, it receives the
new session; “Save profile only” instead reports that it is already saved.

### Sign in through Roblox

The easiest and safest way.

1. Confirm: “I am signing in with my own account.”
2. **Open sign-in window** – a separate, isolated window opens with the official page
   `roblox.com/login` (private mode, no connection to your browser).
3. Sign in as usual – including CAPTCHA and two-step verification.
4. After a successful sign-in the window closes by itself; Nexus RAM takes over only the session,
   checks it with Roblox and stores it encrypted.

The window only allows Roblox pages over HTTPS and opens no pop-ups. If you close it early, nothing
is saved. After 10 minutes without signing in, the process stops.

### Paste your own session

For advanced users: you paste the `.ROBLOSECURITY` value of **your own** account (it starts with
`_|WARNING:-DO-NOT-SHARE-THIS.`).

1. Paste the value into the field.
2. Confirm: “This is my own account and I understand the risk.”
3. **Save session** – the value is checked with Roblox, assigned to the right account and stored
   encrypted. It is never shown again.

> ⚠ Anyone who has this value can sign in as you. Never share it and never paste values someone else
> sent you.

### Sessions from file

Imports many of your own sessions at once.

- Format: text file (`.txt`, UTF-8), **one `.ROBLOSECURITY` value per line**.
- Empty lines and lines starting with `#` are ignored.
- At most **500 lines** and **4 MB** per file. Local files only (no network drives).
- Lines in the format `username:password` are rejected – use
  [Sign-ins from file](#sign-ins-from-file) for that.
- The sessions are checked one after another with a short pause. If Roblox reports a rate limit,
  the import stops; run it again later for the remaining lines (accounts already imported are only
  updated).
- The result lists imported accounts and failed **line numbers** – the values themselves are never
  shown.

### Sign-ins from file

For many accounts whose password you know. Nexus RAM **does not automate the sign-in**, it only saves
you the typing.

- Format: text file, **`username:password` per line**; empty lines and `#` lines are ignored; at most
  500 lines.
- For each line the sign-in window opens one after another with username and password pre-filled.
  **You complete the sign-in, CAPTCHA and two-step verification yourself.**
- The session taken over must belong to the username in that line.
- If you close a sign-in window, the rest of the file is cancelled.
- Passwords are **not** stored. The file does contain them in plain text, though – **delete it
  afterwards**.

### Save profile only

Stores only public profile data (username or user ID). Useful to organize accounts in advance; you
can launch them only after adding a session (right-click → **Add session**).

### Confirm with Roblox OAuth

Confirms an account’s identity via the official Roblox OAuth flow in your default browser. This does
**not** create a session for launching games. It requires your own OAuth app:

1. Create an OAuth 2.0 app on [create.roblox.com](https://create.roblox.com/).
2. Enter `http://localhost:53682/callback` as redirect URL (port as in the settings), with the
   permissions `openid` and `profile`.
3. Enter the client ID under **Settings → Accounts → Roblox OAuth client ID**.

## Account status

| Status | Meaning | What to do |
| --- | --- | --- |
| No session | Only the profile is stored | Add a session |
| Ready | Session available, ready to launch | – |
| Starting | A launch is running | – |
| In game | A client launched by Nexus RAM is running | – |
| Exited | The client was closed | – |
| Check required | Roblox requires a confirmation (e.g. CAPTCHA) | Sign in again through the sign-in window |
| Session expired | Roblox ended the session (sign-out, password change …) | Add the session again |
| Connection error | Roblox not reachable or request rejected | Check the internet connection, try again later |
| Rate limited | Too many requests to Roblox | Wait a few minutes |
| Not supported | The launch is not possible this way (e.g. second client verifiably blocked) | Read the message, see [Troubleshooting](troubleshooting.md) |

Accounts that need action also appear on the **Overview** under “Needs attention”.

## Edit and organize accounts

**Right-click** an account (or use the “⋯” menu):

| Entry | Function |
| --- | --- |
| Launch | Opens the launch dialog for this account or all selected accounts |
| Check session | Asks Roblox whether the stored session is still valid |
| Add session | For accounts without a session |
| Edit | Alias (max. 50 characters), notes (max. 2000 characters), group |
| Add to favorites / Remove from favorites | Favorites can be filtered together |
| Move to group | Assign a group or “No group” |
| Refresh profile | Reload name, display name and profile picture from Roblox |
| Move up / Move down | Custom order (sorting “Custom order”) |
| Remove session | Deletes only the stored session; the account stays |
| Delete | Deletes account and session (with confirmation) |

**View and order:**

- **Tiles** or **Table** – switch at the top right.
- **Sorting:** Custom order, Username, Display name, Recently launched, Date added, Status.
- **Filter by group, favorites or “No group”** – as a sidebar or as chips
  (Settings → Accounts).
- **Search** via the search field at the top (`Ctrl+K`).

**Multi-select:** `Ctrl+click` adds single accounts, `Shift+click` a range, `Ctrl+A` all of them.
Launch, favorites, group and delete then apply to all selected accounts. `Esc` clears the
selection, `Del` deletes (with confirmation).

## Keyboard shortcuts

| Keys | Function |
| --- | --- |
| `Ctrl+1` … `Ctrl+8` | Switch page |
| `Ctrl+K` | Account search |
| `Ctrl+N` | Add account |
| `Ctrl+L` | Launch selection |
| `Ctrl+A` | Select all accounts |
| `Del` | Delete selection |
| `Esc` | Clear selection |
| `Shift`/`Ctrl` + click | Multi-select |
