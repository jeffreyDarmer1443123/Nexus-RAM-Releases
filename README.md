# Nexus RAM

Roblox-Account-Manager für Windows. Nexus RAM verwaltet deine **eigenen** Roblox-Accounts lokal auf
deinem PC, startet Spiele über den offiziellen Roblox-Client – auch mehrere Accounts nacheinander –
und ordnet die Roblox-Fenster auf deinen Monitoren an. Keine Cloud, kein Konto beim Entwickler,
keine Telemetrie.

Dieses Repository enthält die **Installer, Updates und die Dokumentation**. Der Quellcode wird
separat gepflegt.

**[⬇ Neueste Version herunterladen](https://github.com/jeffreyDarmer1443123/Nexus-RAM-Releases/releases/latest)**
– Datei `Nexus.RAM_<Version>_x64-setup.exe`

## Schnellstart

1. Voraussetzungen: Windows 10 oder 11 (64 Bit) und der installierte [Roblox Player](https://www.roblox.com/download).
2. Installer herunterladen und ausführen. Bei der Warnung von Windows SmartScreen
   „Weitere Informationen“ → „Trotzdem ausführen“ wählen (Erklärung in der
   [Installationsanleitung](docs/installation.md#windows-smartscreen)).
3. Nexus RAM starten und den Einrichtungsassistenten durchgehen.
4. Unter **Accounts → Account hinzufügen** deinen ersten Account anlegen – am einfachsten mit
   „Im Roblox-Fenster anmelden“.
5. Unter **Launcher** eine Place-ID oder einen Roblox-Link eintragen, Accounts auswählen und starten.

## Dokumentation

| Kapitel | Inhalt |
| --- | --- |
| [Installation](docs/installation.md) | Download, SmartScreen, Installation, Umstieg von Nexus RAM 0.x, Prüfsummen, Deinstallation |
| [Erste Schritte](docs/erste-schritte.md) | Einrichtungsassistent, Aufbau der Oberfläche, Datenübernahme aus 0.x |
| [Accounts verwalten](docs/accounts.md) | Alle Wege, Accounts hinzuzufügen, Status, Sortierung, Favoriten, Mehrfachauswahl |
| [Gruppen und Startvorlagen](docs/gruppen-und-vorlagen.md) | Accounts bündeln, wiederkehrende Starts speichern |
| [Spiele starten](docs/spiele-starten.md) | Launcher, unterstützte Links, Startaufträge, mehrere Clients gleichzeitig |
| [Sitzungen und Fenster](docs/sitzungen-und-fenster.md) | Laufende Clients, Schließen, Auto-Rejoin, Anti-AFK, Fenster anordnen |
| [Einstellungen](docs/einstellungen.md) | Jede Einstellung mit Standardwert und erlaubtem Bereich |
| [Daten, Backups und Sicherheit](docs/daten-und-sicherheit.md) | Speicherorte, Tresor, Backups, Sicherungen, Datenschutz, Netzwerkziele |
| [Updates](docs/updates.md) | Wie Updates geprüft und sicher installiert werden |
| [Fehlerbehebung und FAQ](docs/fehlerbehebung.md) | Häufige Meldungen, Ursachen und Lösungen |
| [Änderungsprotokoll](CHANGELOG.md) | Was sich in welcher Version geändert hat |

## Wichtige Hinweise

- Verwalte nur Accounts, die **dir gehören**. Sitzungswerte (`.ROBLOSECURITY`) sind wie Passwörter –
  gib sie niemals weiter.
- Mehrere gleichzeitige Roblox-Clients unterstützt Roblox **nicht offiziell**. Nexus RAM ermöglicht
  sie, indem es im selbst gestarteten Client das Handle auf `ROBLOX_singletonEvent` schließt
  (abschaltbar). Das kann den Nutzungsbedingungen von Roblox widersprechen; die Nutzung erfolgt auf
  eigene Verantwortung.
- Nexus RAM liest keine Browserdaten aus und umgeht keine CAPTCHAs oder Zwei-Faktor-Abfragen.
