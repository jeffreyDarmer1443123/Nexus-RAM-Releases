# Änderungsprotokoll

[← Übersicht](README.md)

## 1.0.1 – 2026-10-23

- Das Aktivitätsprotokoll zeigt keine Handle-Meldungen mehr (Ergebnis der Handle-Diagnose,
  erfolgreiches Schließen von `ROBLOX_singletonEvent`). Sie stehen weiterhin in der Logdatei.
  Warnungen, wenn das Event nicht geschlossen werden konnte, bleiben sichtbar.
- Vorhandene Handle-Meldungen werden beim ersten Start automatisch entfernt und bei der
  Datenübernahme aus 0.x nicht übernommen.

## 1.0.0 – 2026-10-23

Erste Version des vollständig neu entwickelten Nexus RAM.

- **Accounts:** Anmeldung im eigenen Roblox-Fenster, Sitzung einfügen, Sitzungen und Anmeldungen aus
  Datei, reines Profil, OAuth-Bestätigung; Status, Favoriten, Gruppen, Suche, Sortierung, Kachel- und
  Tabellenansicht, Mehrfachauswahl, Tastenkombinationen.
- **Starten:** Place-IDs, Spiel-, Server-, Privatserver- und Teilen-Links; Startaufträge mit
  Fortschritt und begrenzten Wiederholungen; Startvorlagen mit automatischer Fensteranordnung.
- **Mehrere Clients:** Schließt im selbst gestarteten Client `ROBLOX_singletonEvent` (abschaltbar).
  Starts werden ausgehandelt: Der nächste Account startet, sobald der vorherige bereit ist; der
  Startabstand dient nur noch als Rückfall.
- **Sitzungen:** eigene und fremde Clients, Fokussieren, Minimieren, Schließen, erzwungenes Beenden
  eigener Clients, Auto-Rejoin, Anti-AFK.
- **Fenster:** Anordnen als Raster, nebeneinander oder untereinander mit Monitorvorschau,
  gespeicherte Layouts, Fensterposition pro Account.
- **Daten:** Tresor mit AES-256-GCM und Windows DPAPI, verschlüsselte Backups, automatische
  Sicherungen mit Wiederherstellung, Datenübernahme aus Nexus RAM 0.x, Integritätsprüfung,
  Diagnoseexport ohne Geheimnisse.
- **Updates:** automatische Prüfung; Installation nur mit gültiger Minisign-Signatur und passender
  SHA-256-Prüfsumme.
- Oberfläche auf Deutsch und Englisch, dunkles und helles Design, einstellbare Akzentfarbe.
