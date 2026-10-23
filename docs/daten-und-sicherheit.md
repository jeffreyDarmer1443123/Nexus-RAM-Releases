# Daten, Backups und Sicherheit

[← Übersicht](../README.md)

Alle Funktionen dieses Kapitels findest du unter **Einstellungen → Daten & Sicherheit**.

## Wo liegen meine Daten?

Standard-Datenordner: `%APPDATA%\com.nexusram2.app` (Knopf **Ordner öffnen**)

| Datei / Ordner | Inhalt |
| --- | --- |
| `nexus-ram-2.db` (+ `-wal`, `-shm`) | Datenbank: Accounts, Gruppen, Vorlagen, Layouts, Einstellungen, Aktivität |
| `vault.key` | Tresorschlüssel, durch Windows an dein Benutzerkonto gebunden |
| `logs\` | Logdateien (ohne Sitzungswerte, Passwörter oder Tokens) |
| `snapshots\` | [Automatische Sicherungen](#automatische-sicherungen) der Datenbank |
| `migration\` | Kopien der Altdaten aus Nexus RAM 0.x, falls übernommen |

**Datenordner ändern:** Nur solange noch **kein Account** gespeichert ist (Einrichtungsassistent
oder **Ändern** neben dem Pfad). Nexus RAM startet danach neu. Netzlaufwerke, Systemordner und
Laufwerkswurzeln (z. B. `C:\`) sind nicht erlaubt.

## Wie sind Sitzungen geschützt?

- Sitzungswerte werden nur im **Tresor** gespeichert: verschlüsselt mit AES-256-GCM, jeder Eintrag
  untrennbar an seinen Account gebunden.
- Der Schlüssel dazu ist mit **Windows DPAPI** an dein Windows-Benutzerkonto gebunden. Auf einem
  anderen PC oder unter einem anderen Windows-Konto lassen sich die Sitzungen daher nicht
  entschlüsseln – nimm dafür ein [Backup mit Sitzungen](#backup-erstellen).
- Gespeicherte Sitzungen werden **nie** wieder angezeigt, nicht ins Log geschrieben und nur an die
  Roblox-API gesendet.
- Der Status zeigt, womit der Schlüssel geschützt ist und wie viele Sitzungen gespeichert sind.

**Grenze:** Schadsoftware, die unter deinem Windows-Konto läuft, kann grundsätzlich auf alles
zugreifen, was du selbst entschlüsseln kannst – das gilt für jede Anwendung. Halte Windows und
deinen Virenschutz aktuell.

## Backup erstellen

**Backup erstellen** speichert eine verschlüsselte Datei (`.nxbackup`) mit Accounts, Gruppen,
Startvorlagen, Fenster-Layouts und Einstellungen.

1. **Speicherort** wählen.
2. **Passphrase** eingeben (mindestens 12 Zeichen) und wiederholen. Ohne Passphrase ist das Backup
   nicht lesbar – es gibt keine Wiederherstellung einer vergessenen Passphrase.
3. Optional **Gespeicherte Sitzungen einschließen** – dann zusätzlich das Risiko bestätigen. Wer
   Datei **und** Passphrase besitzt, kann sich mit diesen Accounts anmelden.
4. **Backup erstellen**.

Verschlüsselung: Argon2id (Schlüsselableitung aus der Passphrase) + AES-256-GCM.

## Backup importieren

1. **Backup importieren** → Datei wählen, Passphrase eingeben.
2. **Modus** wählen:
   - **Zusammenführen** – vorhandene Accounts bleiben, neue kommen hinzu.
   - **Ersetzen** – alle aktuellen Daten werden durch das Backup ersetzt. Vorher wird der aktuelle
     Stand automatisch gesichert. Dafür dürfen keine Clients laufen und keine Starts aktiv sein.
3. **Importieren**.

Falsche Passphrasen und veränderte oder beschädigte Dateien werden erkannt – dann ändert sich nichts.
Backups aus **Nexus RAM 0.x** lassen sich ebenfalls importieren.

## Automatische Sicherungen

Vor jedem Import im Modus „Ersetzen“, vor jeder Wiederherstellung und vor jeder Datenübernahme
sichert Nexus RAM die Datenbank automatisch. Mit **Jetzt sichern** legst du selbst eine Sicherung an.
Es werden die **10 neuesten** Sicherungen behalten.

**Wiederherstellen** ersetzt den aktuellen Stand durch die gewählte Sicherung – der aktuelle Stand wird
vorher selbst gesichert. Dafür dürfen keine Clients laufen und keine Starts aktiv sein.

> Sicherungen liegen im selben Datenordner und schützen vor Fehlbedienung, nicht vor dem Verlust des
> PCs. Dafür ist das [Backup](#backup-erstellen) gedacht.

## Wartung

| Funktion | Wirkung |
| --- | --- |
| **Integrität prüfen** | Prüft die Datenbank und ob alle gespeicherten Sitzungen entschlüsselbar sind |
| **Cache leeren** | Löscht zwischengespeicherte Profilbilder, Spielnamen, erledigte Startaufträge und die Roblox-Erkennung |
| **Diagnose exportieren** | Speichert eine JSON-Datei für die Fehlersuche: Version, Roblox-Installation, Einstellungen, letzte Ereignisse, Logauszug – **ohne** Sitzungswerte, Passwörter oder Tokens |

## Datenschutz

- Keine Telemetrie, keine Analyse, kein Konto beim Entwickler. Deine Daten verlassen den PC nur in
  Richtung Roblox (für die Funktionen der App) und GitHub (nur für die Update-Prüfung, ohne
  Nutzerdaten).
- Nexus RAM liest keine Browserdaten oder Passwörter anderer Programme aus.

## Netzwerkziele

Nexus RAM verbindet sich ausschließlich mit diesen Adressen (auch einsehbar unter
**Einstellungen → Info & Updates**):

| Ziel | Zweck |
| --- | --- |
| `users.roblox.com`, `auth.roblox.com`, `games.roblox.com`, `thumbnails.roblox.com`, `apis.roblox.com` | Roblox-API: Profile, Sitzungsprüfung, Anmelde-Ticket, Spielnamen, Profilbilder, Teilen-Links, OAuth |
| `*.rbxcdn.com` | Profilbilder (nur Anzeige) |
| `www.roblox.com` | Das eigene Anmeldefenster |
| `github.com` (+ `objects.githubusercontent.com`) | Update-Prüfung und Download, signiert |
| `127.0.0.1` | Nur lokaler OAuth-Rückruf |

Alle Verbindungen nutzen HTTPS mit Zertifikatsprüfung (außer dem lokalen Rückruf).
