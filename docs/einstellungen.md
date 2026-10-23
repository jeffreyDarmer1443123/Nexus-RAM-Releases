# Einstellungen

[← Übersicht](../README.md)

**Einstellungen** hat sechs Reiter. In den ersten vier werden Änderungen erst mit **Speichern**
übernommen; **Verwerfen** stellt den gespeicherten Stand wieder her. Ungültige Werte werden beim
Speichern mit einer Meldung abgelehnt.

## Allgemein

| Einstellung | Standard | Werte / Hinweis |
| --- | --- | --- |
| Sprache | Deutsch | Deutsch, English |
| Darstellung | Dunkel | Dunkel, Hell, Wie Windows |
| Akzentfarbe | Orange | 8 Farben zur Auswahl |
| Mit Windows starten | aus | Startet Nexus RAM bei der Windows-Anmeldung minimiert im Infobereich |
| Beim Schließen in den Infobereich minimieren | aus | Das ✕ versteckt das Fenster nur; Nexus RAM läuft im Infobereich (Taskleiste unten rechts) weiter |
| Benachrichtigungen | an | Windows-Benachrichtigungen bei Client gestartet/beendet, Fehlstart, Anmeldefehler und Update – nur wenn das Fenster nicht sichtbar ist |
| Beim Start nach Updates suchen | an | Siehe [Updates](updates.md) |
| Protokollstufe | info | error, warn, info, debug – wie ausführlich die Logdatei schreibt |

**Infobereich-Symbol:** Rechtsklick bietet **Nexus RAM öffnen**, **Alle Starts abbrechen** und
**Beenden**.

## Accounts

| Einstellung | Standard | Werte / Hinweis |
| --- | --- | --- |
| Standardsortierung | Eigene Reihenfolge | Eigene Reihenfolge, Benutzername, Anzeigename, Zuletzt gestartet, Hinzugefügt, Status |
| Standardansicht | Kacheln | Kacheln, Tabelle |
| Gruppen | Sidebar | Gruppenfilter als Seitenleiste oder als Chips |
| Avatar-Cache (Stunden) | 24 | 1–720 – wie lange Profilbilder zwischengespeichert werden |
| Sitzungen beim Start prüfen | aus | Prüft alle gespeicherten Sitzungen nacheinander mit Abstand; stoppt bei Rate Limit |
| Roblox-OAuth-Client-ID | leer | Nur für [OAuth-Bestätigung](accounts.md#mit-roblox-oauth-bestätigen) |
| OAuth-Port | 53682 | 1024–65535 – Port des lokalen Rückrufs `http://localhost:<Port>/callback` |

## Launcher

| Einstellung | Standard | Werte / Hinweis |
| --- | --- | --- |
| Startabstand (s) | 8 | 1–300 – nur Rückfall, siehe [Startreihenfolge](spiele-starten.md#startreihenfolge-und-startabstand) |
| Gleichzeitige Starts | 1 | 1–10 |
| Standard-Place-ID | leer | Wird im Startformular vorausgefüllt |
| Bei einem Fehlstart | Weitere Starts fortsetzen | oder: Restliche Starts abbrechen |
| Wiederholungen bei Netzwerkfehlern | 1 | 0–5 |
| Schließen von Sitzungen bestätigen | an | Rückfrage vor dem Schließen von Roblox |
| Prozessüberwachung (s) | 2 | 1–10 – wie oft Prozesse, CPU und RAM aktualisiert werden |
| Mehrere Clients ermöglichen | an | Schließt im eigenen Client `ROBLOX_singletonEvent`, siehe [Mehrere Clients](spiele-starten.md#mehrere-clients-gleichzeitig) |
| Probelauf für parallele Clients erlauben | aus | Prüft beim nächsten Zweitstart, ob beide Clients weiterlaufen |
| Anti-AFK | aus | Siehe [Anti-AFK](sitzungen-und-fenster.md#anti-afk) |
| Intervall (s) | 120 | 10–1800 |
| Auto-Rejoin | aus | Siehe [Auto-Rejoin](sitzungen-und-fenster.md#auto-rejoin) |
| Verhalten | Nachfragen | Nachfragen, Automatisch |
| Maximale Versuche | 3 | 1–10 |
| Wartezeit (s) | 15 | 5–600 – Startwert, verdoppelt sich je Versuch (max. 10 min) |

## Fenster

| Einstellung | Standard | Werte / Hinweis |
| --- | --- | --- |
| Bevorzugter Monitor | Hauptmonitor | Ziel für das Anordnen, wenn kein anderer gewählt ist |
| Standard-Layout | Raster | Keins, Raster, Nebeneinander, Untereinander |
| Fensterabstand (px) | 8 | 0–200 |
| Rand (px) | 8 | 0–400 |
| Fensterposition pro Account merken | an | Stellt Position und Größe beim nächsten Start wieder her |

## Daten & Sicherheit

Datenordner, Tresor-Status, verschlüsselte Backups, automatische Sicherungen, Datenübernahme aus
0.x und Wartung (Integrität prüfen, Cache leeren, Diagnose exportieren) – ausführlich unter
[Daten, Backups und Sicherheit](daten-und-sicherheit.md).

## Info & Updates

Version, erkannter Roblox Player, Update-Prüfung und -Installation, die vollständige Liste der
Netzwerkziele und alle Tastenkombinationen – siehe [Updates](updates.md) und
[Netzwerkziele](daten-und-sicherheit.md#netzwerkziele).
