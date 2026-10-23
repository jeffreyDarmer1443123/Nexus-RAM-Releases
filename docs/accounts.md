# Accounts verwalten

[← Übersicht](../README.md)

## Account hinzufügen

**Accounts → Account hinzufügen** (oder `Strg+N`). Es gibt sechs Wege:

| Methode | Ergebnis | Kann starten? |
| --- | --- | --- |
| [Im Roblox-Fenster anmelden](#im-roblox-fenster-anmelden) | Account mit Sitzung | ✔ |
| [Eigene Sitzung einfügen](#eigene-sitzung-einfügen) | Account mit Sitzung | ✔ |
| [Sitzungen aus Datei](#sitzungen-aus-datei) | Viele Accounts mit Sitzung | ✔ |
| [Anmeldungen aus Datei](#anmeldungen-aus-datei) | Viele Accounts mit Sitzung (du meldest dich nacheinander an) | ✔ |
| [Nur Profil speichern](#nur-profil-speichern) | Account ohne Sitzung | erst nach Hinzufügen einer Sitzung |
| [Mit Roblox OAuth bestätigen](#mit-roblox-oauth-bestätigen) | Account mit bestätigter Identität, ohne Sitzung | erst nach Hinzufügen einer Sitzung |

Bei allen Methoden kannst du gleich einen **Alias**, **Notizen** und eine **Gruppe** festlegen.
Jeder Roblox-Account (User-ID) existiert nur einmal: Fügst du für einen schon vorhandenen Account eine
Sitzung hinzu, erhält er die neue Sitzung; „Nur Profil speichern“ meldet dagegen, dass er bereits
gespeichert ist.

### Im Roblox-Fenster anmelden

Der einfachste und sicherste Weg.

1. Bestätigen: „Ich melde mich mit meinem eigenen Account an.“
2. **Anmeldefenster öffnen** – es öffnet sich ein eigenes, abgeschottetes Fenster mit der
   offiziellen Seite `roblox.com/login` (privater Modus, keine Verbindung zu deinem Browser).
3. Ganz normal anmelden – inklusive CAPTCHA und Zwei-Faktor-Bestätigung.
4. Nach erfolgreicher Anmeldung schließt sich das Fenster von selbst; Nexus RAM übernimmt nur die
   Sitzung, prüft sie bei Roblox und speichert sie verschlüsselt.

Das Fenster lässt nur Roblox-Seiten über HTTPS zu und öffnet keine Popups. Schließt du es vorher,
wird nichts gespeichert. Nach 10 Minuten ohne Anmeldung bricht der Vorgang ab.

### Eigene Sitzung einfügen

Für Fortgeschrittene: Du fügst den `.ROBLOSECURITY`-Wert **deines eigenen** Accounts ein (beginnt mit
`_|WARNING:-DO-NOT-SHARE-THIS.`).

1. Wert in das Feld einfügen.
2. Bestätigen: „Es ist mein eigener Account und ich verstehe das Risiko.“
3. **Sitzung speichern** – der Wert wird bei Roblox geprüft, dem richtigen Account zugeordnet und
   verschlüsselt gespeichert. Er wird danach nie wieder angezeigt.

> ⚠ Wer diesen Wert besitzt, kann sich als du anmelden. Gib ihn niemals weiter und füge niemals
> Werte ein, die dir jemand anderes geschickt hat.

### Sitzungen aus Datei

Importiert viele eigene Sitzungen auf einmal.

- Format: Textdatei (`.txt`, UTF-8), **ein `.ROBLOSECURITY`-Wert pro Zeile**.
- Leere Zeilen und Zeilen, die mit `#` beginnen, werden ignoriert.
- Höchstens **500 Zeilen** und **4 MB** pro Datei. Nur lokale Dateien (keine Netzlaufwerke).
- Zeilen im Format `Benutzername:Passwort` werden abgelehnt – dafür gibt es
  [Anmeldungen aus Datei](#anmeldungen-aus-datei).
- Die Sitzungen werden nacheinander mit kurzem Abstand geprüft. Meldet Roblox ein Rate Limit, stoppt
  der Import; starte ihn später erneut für die restlichen Zeilen (bereits übernommene werden nur
  aktualisiert).
- Das Ergebnis nennt übernommene Accounts und fehlgeschlagene **Zeilennummern** – die Werte selbst
  werden nie angezeigt.

### Anmeldungen aus Datei

Für viele Accounts, deren Passwort du kennst. Nexus RAM **automatisiert nicht die Anmeldung**,
sondern nimmt dir nur das Abtippen ab.

- Format: Textdatei, **`Benutzername:Passwort` pro Zeile**; leere Zeilen und `#`-Zeilen werden
  ignoriert; höchstens 500 Zeilen.
- Für jede Zeile öffnet sich nacheinander das Anmeldefenster, Benutzername und Passwort sind
  vorausgefüllt. **Anmelden, CAPTCHA und Zwei-Faktor erledigst du selbst.**
- Die übernommene Sitzung muss zum Benutzernamen der Zeile passen.
- Schließt du ein Anmeldefenster, wird der Rest der Datei abgebrochen.
- Passwörter werden **nicht** gespeichert. Die Datei enthält sie aber im Klartext – **lösche sie
  danach**.

### Nur Profil speichern

Speichert nur öffentliche Profildaten (Benutzername oder User-ID). Praktisch, um Accounts schon
einzuordnen; starten kannst du sie erst, wenn du eine Sitzung hinzufügst
(Rechtsklick → **Sitzung hinzufügen**).

### Mit Roblox OAuth bestätigen

Bestätigt die Identität eines Accounts über den offiziellen Roblox-OAuth-Ablauf im Standardbrowser.
Ergibt **keine** Sitzung zum Spielstart. Voraussetzung ist eine eigene OAuth-App:

1. Auf [create.roblox.com](https://create.roblox.com/) eine OAuth-2.0-App anlegen.
2. Als Redirect-URL `http://localhost:53682/callback` eintragen (Port wie in den Einstellungen),
   Berechtigungen `openid` und `profile`.
3. Die Client-ID unter **Einstellungen → Accounts → Roblox-OAuth-Client-ID** eintragen.

## Status eines Accounts

| Status | Bedeutung | Was tun? |
| --- | --- | --- |
| Keine Sitzung | Nur Profil gespeichert | Sitzung hinzufügen |
| Bereit | Sitzung vorhanden, startbereit | – |
| Startet | Ein Start läuft | – |
| Im Spiel | Client von Nexus RAM läuft | – |
| Beendet | Client wurde geschlossen | – |
| Prüfung nötig | Roblox verlangt eine Bestätigung (z. B. CAPTCHA) | Im Anmeldefenster neu anmelden |
| Sitzung abgelaufen | Roblox hat die Sitzung beendet (Abmeldung, Passwortwechsel …) | Sitzung neu hinzufügen |
| Verbindungsfehler | Roblox nicht erreichbar oder Anfrage abgelehnt | Internet prüfen, später erneut |
| Rate Limit | Zu viele Anfragen an Roblox | Einige Minuten warten |
| Nicht unterstützt | Der Start ist so nicht möglich (z. B. zweiter Client nachweislich blockiert) | Meldung lesen, siehe [Fehlerbehebung](fehlerbehebung.md) |

Accounts mit Handlungsbedarf erscheinen auch auf der **Übersicht** unter „Braucht Aufmerksamkeit“.

## Accounts bearbeiten und organisieren

**Rechtsklick** auf einen Account (oder das Menü „⋯“) bietet:

| Eintrag | Funktion |
| --- | --- |
| Starten | Öffnet den Startdialog für diesen bzw. alle ausgewählten Accounts |
| Sitzung prüfen | Fragt bei Roblox nach, ob die gespeicherte Sitzung noch gültig ist |
| Sitzung hinzufügen | Für Accounts ohne Sitzung |
| Bearbeiten | Alias (max. 50 Zeichen), Notizen (max. 2000 Zeichen), Gruppe |
| Zu Favoriten / Aus Favoriten entfernen | Favoriten lassen sich gesammelt filtern |
| In Gruppe verschieben | Gruppe zuweisen oder „Ohne Gruppe“ |
| Profil aktualisieren | Name, Anzeigename und Profilbild neu von Roblox laden |
| Nach oben / Nach unten | Eigene Reihenfolge (Sortierung „Eigene Reihenfolge“) |
| Sitzung entfernen | Löscht nur die gespeicherte Sitzung, der Account bleibt |
| Löschen | Löscht Account und Sitzung (mit Bestätigung) |

**Ansicht und Ordnung:**

- **Kacheln** oder **Tabelle** – umschaltbar oben rechts.
- **Sortierung:** Eigene Reihenfolge, Benutzername, Anzeigename, Zuletzt gestartet, Hinzugefügt,
  Status.
- **Filter nach Gruppe, Favoriten oder „Ohne Gruppe“** – als Seitenleiste oder als Chips
  (Einstellungen → Accounts).
- **Suche** über das Suchfeld oben (`Strg+K`).

**Mehrfachauswahl:** `Strg+Klick` wählt einzelne Accounts dazu, `Shift+Klick` einen Bereich,
`Strg+A` alle. Danach wirken Starten, Favoriten, Gruppe und Löschen auf alle ausgewählten Accounts.
`Esc` hebt die Auswahl auf, `Entf` löscht (mit Bestätigung).

## Tastenkombinationen

| Tasten | Funktion |
| --- | --- |
| `Strg+1` … `Strg+8` | Bereich wechseln |
| `Strg+K` | Accountsuche |
| `Strg+N` | Account hinzufügen |
| `Strg+L` | Auswahl starten |
| `Strg+A` | Alle Accounts auswählen |
| `Entf` | Auswahl löschen |
| `Esc` | Auswahl aufheben |
| `Shift`/`Strg` + Klick | Mehrfachauswahl |
