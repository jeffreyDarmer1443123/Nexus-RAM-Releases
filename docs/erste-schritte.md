# Erste Schritte

[← Übersicht](../README.md)

## Einrichtungsassistent

Beim ersten Start führt ein Assistent in fünf Schritten durch die Einrichtung. Mit **Überspringen**
kannst du ihn jederzeit beenden; alles lässt sich später in den Einstellungen nachholen.

| Schritt | Was passiert |
| --- | --- |
| **Sicherheit** | Kurze Regeln: nur eigene Accounts, Sitzungswerte nie weitergeben, keine CAPTCHA-Umgehung, Mehrfach-Clients sind von Roblox nicht offiziell unterstützt. |
| **Roblox** | Nexus RAM prüft, ob der Roblox Player installiert ist, und zeigt die erkannte Version. |
| **Daten** | Zeigt den Datenordner. Solange noch kein Account angelegt ist, kannst du hier einen anderen Ordner wählen (Nexus RAM startet danach neu). |
| **Übernahme** | Findet Nexus RAM Daten der Version 0.x, kannst du sie hier übernehmen (siehe unten). |
| **Erster Account** | Öffnet direkt den Dialog „Account hinzufügen“ – oder du klickst „Los geht’s“. |

## Aufbau der Oberfläche

**Seitenleiste (links)** – die Bereiche, umschaltbar auch mit `Strg+1` … `Strg+8`:

| Bereich | Wofür |
| --- | --- |
| Übersicht | Kennzahlen, Schnellstart, Accounts mit Handlungsbedarf, laufende Clients, Startaufträge, letzte Ereignisse |
| Accounts | Alle Accounts verwalten, hinzufügen, starten |
| Gruppen | Accounts zu Gruppen zusammenfassen |
| Launcher | Spiele starten, Startvorlagen, Startaufträge |
| Sitzungen | Laufende Roblox-Clients, Schließen, Auto-Rejoin |
| Fenster | Roblox-Fenster anordnen, Layouts speichern |
| Aktivität | Protokoll aller Ereignisse |
| Einstellungen | Alle Optionen, Backups, Updates |

Die Seitenleiste lässt sich mit dem Symbol unten links einklappen.

**Kopfzeile (oben):**

- **Suchfeld** (`Strg+K`) – sucht nach Benutzername, Anzeigename, Alias und Notizen sowie nach der
  exakten User-ID und springt zur Accountliste.
- **Live-Leiste** – zeigt die Profilbilder aller von Nexus RAM gestarteten, laufenden Clients; beim
  Darüberfahren erscheinen Name, Laufzeit und Arbeitsspeicher. Ein Klick holt das Roblox-Fenster dieses Accounts in den Vordergrund. Rechts daneben
  steht, wie viele **fremde** Roblox-Clients laufen (nicht von Nexus RAM gestartet).
- **Startaufträge** – solange Starts laufen, ein Hinweis mit der Anzahl.
- **CPU / RAM** – Auslastung des PCs.

## Datenübernahme aus Nexus RAM 0.x

Nexus RAM 1.x hat eine eigene Datenbank. Daten der alten Version 0.x werden **nicht automatisch**
übernommen, sondern nur auf deinen Wunsch – entweder im Einrichtungsassistenten oder später unter
**Einstellungen → Daten & Sicherheit → Daten aus Nexus RAM 0.x**.

1. **Nach Daten suchen** – zeigt, was gefunden wurde: Anzahl Accounts, Sitzungen, Gruppen,
   Vorlagen und Layouts. Dafür wird eine Kopie gelesen; die alten Daten werden nicht verändert.
2. **Daten übernehmen** – nach Bestätigung werden übernommen: Accounts (inkl. Alias, Notizen,
   Favoriten, Reihenfolge), Sitzungen, Gruppen, Startvorlagen, Fenster-Layouts, gespeicherte
   Fensterpositionen, die letzten Ereignisse und die Einstellungen.

Gut zu wissen:

- Vorher werden die alten Dateien vollständig in den Unterordner `migration` des Datenordners
  kopiert und die neue Datenbank gesichert. Die Originale unter `%APPDATA%\com.nexusram.app` bleiben
  unverändert.
- **Schließe die alte App vorher.** Läuft sie noch, weist Nexus RAM darauf hin, damit keine
  Änderungen verloren gehen.
- Bereits vorhandene Accounts (gleiche Roblox-User-ID) bleiben unverändert und werden übersprungen.
  Eine zweite Übernahme ist daher unschädlich.
- Sitzungen sind an dein **Windows-Benutzerkonto** gebunden. Stammen die alten Daten von einem
  anderen Windows-Konto oder PC, werden alle Daten außer den Sitzungen übernommen; die Sitzungen
  fügst du dann neu hinzu.
- Auch verschlüsselte Backups aus 0.x (`.nxbackup`) lassen sich unter
  [Backup importieren](daten-und-sicherheit.md#backup-importieren) einlesen.

## Nächste Schritte

- [Accounts hinzufügen](accounts.md)
- [Ein Spiel starten](spiele-starten.md)
