# Spiele starten

[← Übersicht](../README.md)

Nexus RAM startet Roblox genauso wie der „Spielen“-Knopf auf roblox.com: Es fordert mit der
gespeicherten Sitzung bei Roblox ein kurzlebiges Anmelde-Ticket an und übergibt es dem **offiziellen
Roblox-Client**. Jeder gestartete Client wird anhand seiner Prozess-ID und Startzeit eindeutig dem
Account zugeordnet.

## Wo kann ich starten?

| Ort | Wie |
| --- | --- |
| **Launcher** | Vollständiges Startformular, Startvorlagen und Startaufträge |
| **Übersicht → Schnellstart** | Kompaktes Formular |
| **Accounts** | Accounts auswählen → Rechtsklick → **Starten** oder `Strg+L` |
| **Gruppen** | **Gruppe starten** oder **Vorlage starten** |
| **Startvorlagen** | **Starten** neben der Vorlage |

## Das Startformular

| Feld | Bedeutung |
| --- | --- |
| **Spiel** | Place-ID oder Roblox-Link (siehe unten). Nexus RAM prüft die Eingabe sofort und zeigt den Spielnamen an. |
| **Server-ID** (optional) | GUID eines bestimmten Servers, um genau diesem beizutreten. Nur zusammen mit einer reinen Place-ID. |
| **Accounts** | Auswahl mit Filterfeld, „Alle auswählen“ und „Nur startbereite“. Accounts ohne Sitzung oder mit laufendem Client werden übersprungen. |
| **Startabstand (s)** | Nur Rückfallwert – siehe [Startreihenfolge](#startreihenfolge-und-startabstand). Vorgabe aus den Einstellungen. |
| **Gleichzeitige Starts** | Wie viele Startvorgänge gleichzeitig vorbereitet werden (1–10). Gilt für Startvorgänge, nicht für laufende Clients. |
| **Auto-Rejoin für diese Starts aktivieren** | Nur sichtbar, wenn Auto-Rejoin in den Einstellungen eingeschaltet ist. Die gestarteten Sitzungen werden überwacht ([Auto-Rejoin](sitzungen-und-fenster.md#auto-rejoin)). |

Der Knopf **„N starten“** legt für jeden Account einen Startauftrag an.

### Unterstützte Eingaben im Feld „Spiel“

| Eingabe | Beispiel |
| --- | --- |
| Place-ID | `1818` |
| Spiel-Link | `https://www.roblox.com/games/1818/Classic-Crossroads` |
| Link mit Sprachpfad | `https://www.roblox.com/de/games/1818/…` |
| Start-Link | `https://www.roblox.com/games/start?placeId=920587237` |
| Privater Server | `https://www.roblox.com/games/1818/…?privateServerLinkCode=…` |
| Teilen-Link eines Servers | `https://www.roblox.com/share?code=…&type=Server` |
| Bestimmter Server | `https://www.roblox.com/games/1818/…?gameInstanceId=<GUID>` |

Erlaubt sind nur Place-IDs und Links auf `https://www.roblox.com` (auch `roblox.com` und
`web.roblox.com`). Andere Adressen, `http://`, Profil-Links oder Teilen-Links für Profile werden
abgelehnt.

## Startaufträge

Jeder Start erscheint im Bereich **Startaufträge** (Launcher, Übersicht) mit Fortschrittsbalken:

| Zustand | Bedeutung |
| --- | --- |
| Wartet | Wartet auf einen freien Startplatz |
| Vorbereitung | Prüft Account und Roblox-Installation |
| Anmeldung | Fordert das Anmelde-Ticket bei Roblox an |
| Startet | Roblox wird gestartet, der neue Prozess wird erkannt |
| Läuft | Client läuft und ist dem Account zugeordnet |
| Fehlgeschlagen | Start nicht möglich – die Meldung nennt den Grund, ggf. mit Diagnosecode |
| Abgebrochen | Von dir abgebrochen |
| Nicht unterstützt | Start so nicht möglich (z. B. zweiter Client nachweislich blockiert) |

- Einzelne Aufträge lassen sich mit **✕** abbrechen, alle mit **Alle abbrechen** (auch über das
  Infobereich-Symbol → **Alle Starts abbrechen**).
- **Erledigte entfernen** räumt die Liste auf.
- Bei Netzwerkfehlern wird automatisch erneut versucht (Anzahl in den Einstellungen,
  Standard 1 Wiederholung). Abgelaufene Sitzungen oder Bestätigungsanfragen von Roblox werden
  **nicht** wiederholt – der Account erhält den passenden Status.
- **Bei einem Fehlstart** laufen die übrigen Starts standardmäßig weiter; in den Einstellungen kann
  stattdessen „Restliche Starts abbrechen“ gewählt werden.

## Startreihenfolge und Startabstand

Clients werden **nacheinander** gestartet, damit jeder neue Prozess eindeutig seinem Account
zugeordnet werden kann. Die Wartezeit zwischen zwei Starts wird **automatisch ausgehandelt**:

1. Roblox startet und legt das Objekt `ROBLOX_singletonEvent` an.
2. Nexus RAM schließt im gerade gestarteten Client das Handle darauf
   (Einstellung „Mehrere Clients ermöglichen“, Standard: an).
3. **Sobald das gelungen ist, startet der nächste Account sofort** (nach 0,25 s Sicherheitsabstand).

Der **Startabstand** (Standard 8 s) ist nur der Rückfall: Er gilt, wenn das Event nicht gefunden oder
nicht geschlossen werden konnte oder wenn „Mehrere Clients ermöglichen“ ausgeschaltet ist. Nexus RAM
sucht höchstens so lange nach dem Event, wie der Startabstand dauern würde – kein Start wird also
langsamer als mit festem Abstand.

## Mehrere Clients gleichzeitig

Roblox unterstützt mehrere gleichzeitige Clients **nicht offiziell**. Normalerweise beendet ein neuer
Client den laufenden. Nexus RAM ermöglicht mehrere Clients, indem es nach jedem Start **im selbst
gestarteten Client** das Handle auf `ROBLOX_singletonEvent` schließt:

- Es werden ausschließlich von Nexus RAM gestartete `RobloxPlayerBeta.exe`-Prozesse angefasst und nur
  genau dieses eine Handle. Andere Programme und fremde Roblox-Clients bleiben unberührt.
- Abschaltbar unter **Einstellungen → Launcher → Mehrere Clients ermöglichen**. Ohne diese Funktion
  beendet Roblox in der Regel den vorher laufenden Client.
- Der Eingriff in den Roblox-Prozess kann den Nutzungsbedingungen von Roblox widersprechen. Die
  Nutzung erfolgt auf eigene Verantwortung.

**Probelauf (optional):** Unter **Einstellungen → Launcher → Probelauf für parallele Clients
erlauben** (Standard: aus) beobachtet Nexus RAM beim nächsten Zweitstart einige Sekunden lang, ob
beide Clients weiterlaufen, und merkt sich das Ergebnis für die installierte Roblox-Version. Ist
nachgewiesen, dass Roblox keinen zweiten Client zulässt, startet Nexus RAM in einem Stapel keine
weiteren Clients, die den laufenden beenden würden. Nach einem Roblox-Update wird neu geprüft.

## Fremde Clients

Roblox-Clients, die nicht von Nexus RAM gestartet wurden (z. B. über die Website), erscheinen als
**fremd**. Sie werden angezeigt, aber nie einem Account zugeordnet, nie erzwungen beendet und nicht
von Anti-AFK oder Auto-Rejoin berührt.
