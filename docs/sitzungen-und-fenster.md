# Sitzungen und Fenster

[← Übersicht](../README.md)

## Sitzungen

Der Bereich **Sitzungen** zeigt alle laufenden Roblox-Clients in zwei Tabellen:

- **Von Nexus RAM gestartet** – mit Account, Spiel, PID, Laufzeit, CPU und Arbeitsspeicher.
- **Fremde Roblox-Clients** – nicht von Nexus RAM gestartet, keinem Account zugeordnet.

Die Werte aktualisieren sich laufend (Takt einstellbar unter Einstellungen → Launcher →
Prozessüberwachung). Eigene Sitzungen bleiben auch nach einem Neustart von Nexus RAM als eigene
erkannt, solange der Client weiterläuft.

### Aktionen

| Aktion | Wo | Wirkung |
| --- | --- | --- |
| Fokussieren | Symbol in der Zeile | Holt das Roblox-Fenster in den Vordergrund |
| Minimieren | Symbol in der Zeile | Minimiert das Fenster |
| Wiederherstellen | Menü „⋯“ | Stellt ein minimiertes Fenster wieder her |
| Auto-Rejoin aktivieren/deaktivieren | Menü „⋯“ (nur eigene, wenn Auto-Rejoin eingeschaltet ist) | Sitzung überwachen, siehe unten |
| Schließen | Menü „⋯“ oder Auswahl + **Auswahl schließen** | Beendet Roblox regulär (siehe unten) |
| Erzwungen beenden | Menü „⋯“ (nur eigene) | Beendet den Prozess sofort – ungespeicherter Spielfortschritt kann verloren gehen |
| Alle minimieren | Oben rechts | Minimiert alle eigenen Roblox-Fenster |

**Schließen** schickt Roblox zuerst die normale Aufforderung zum Beenden. Läuft der Client nach
5 Sekunden noch (Roblox bleibt manchmal im Hintergrund), wird genau dieser Prozess beendet. Die
Meldung nennt, wie viele regulär geschlossen und wie viele beendet wurden. Vor dem Schließen wird
nachgefragt (abschaltbar unter Einstellungen → Launcher → „Schließen von Sitzungen bestätigen“).
Fremde Clients lassen sich schließen, aber nie erzwungen beenden.

## Auto-Rejoin

Auto-Rejoin startet einen Account erneut, wenn sein Client **unerwartet** endet – zum Beispiel nach
einem Verbindungsabbruch.

**Einschalten:** Einstellungen → Launcher → **Auto-Rejoin**. Danach gilt es nur für Sitzungen, die du
als **überwacht** markierst:

- beim Starten: Häkchen „Auto-Rejoin für diese Starts aktivieren“, oder
- später: Sitzungen → Menü „⋯“ → **Auto-Rejoin aktivieren**.

Überwachte Sitzungen tragen die Markierung „Auto-Rejoin“.

| Verhalten | Ablauf |
| --- | --- |
| **Nachfragen** (Standard) | Es erscheint die Meldung „Überwachte Sitzung beendet – Erneut beitreten?“ mit dem Knopf **Erneut beitreten**. |
| **Automatisch** | Nach einer Wartezeit wird automatisch neu gestartet. Die Wartezeit beginnt bei der eingestellten Zeit (Standard 15 s) und verdoppelt sich mit jedem Versuch, höchstens bis 10 Minuten. Nach der maximalen Anzahl Versuche (Standard 3) gibt Auto-Rejoin auf. |

Neu gestartet wird dasselbe Ziel – dasselbe Spiel, derselbe Server oder private Server.

Auto-Rejoin greift **nicht**, wenn du den Client selbst über Nexus RAM schließt. Es **pausiert**
automatisch, wenn ein Neustart sinnlos wäre: abgelaufene Sitzung, Bestätigungsanfrage von Roblox,
Rate Limit, fehlende Sitzung, Roblox nicht installiert oder Start nicht unterstützt. Laufende,
pausierte oder aufgegebene Rejoins siehst du oben im Bereich Sitzungen und kannst sie dort
**abbrechen** oder **fortsetzen**.

## Anti-AFK

Roblox wirft untätige Spieler nach etwa 20 Minuten aus dem Spiel. Anti-AFK verhindert das, indem es
in jedem **eigenen** Roblox-Fenster regelmäßig einen Sprung (Leertaste) auslöst.

- Einschalten: Einstellungen → Launcher → **Anti-AFK** (Standard: aus).
- Intervall: Standard 120 s je Fenster (10–1800 s).
- Es wird nur ausgelöst, wenn du seit mindestens 2 Sekunden weder Maus noch Tastatur benutzt hast
  und keine Taste gedrückt hältst. Danach wird dein vorheriges Fenster wieder in den Vordergrund
  geholt, minimierte Roblox-Fenster werden wieder minimiert.
- Fremde Roblox-Clients und andere Programme erhalten nie Eingaben.
- Simulierte Eingaben können den Nutzungsbedingungen von Roblox widersprechen.

## Fenster anordnen

Der Bereich **Fenster** listet alle offenen Roblox-Fenster (eigene und fremde, minimierte sind
markiert). Pro Fenster: **Fokussieren**, **Minimieren** bzw. **Wiederherstellen**.

**Anordnen:**

1. Fenster auswählen (Häkchen) – ohne Auswahl werden **alle** Roblox-Fenster angeordnet.
2. **Layout** wählen:
   - **Raster** – gleichmäßiges Gitter,
   - **Nebeneinander** – Spalten,
   - **Untereinander** – Zeilen.
3. **Monitor** wählen – in der Liste oder durch Klick auf einen Monitor in der maßstäblichen
   **Monitorvorschau**. Die Vorschau zeigt alle Monitore und die aktuelle Lage der Fenster.
4. **Abstand** zwischen den Fenstern und **Rand** zum Bildschirmrand in Pixeln.
5. **„N anordnen“**.

Berücksichtigt werden Taskleiste, DPI-Skalierung und eine Mindestgröße von 320×240 Pixeln. Reicht
der Platz nicht, überlappen sich die Fenster (Hinweis erscheint). Andere Programme werden nie
verändert. Lässt sich ein einzelnes Fenster nicht bewegen, werden die übrigen trotzdem angeordnet.

**Gespeicherte Layouts:** Namen eingeben → **Speichern** sichert Layout, Monitor, Abstand und Rand.
Mit **Anwenden** wird ein gespeichertes Layout geladen und sofort angewendet, mit dem Papierkorb
gelöscht.

**Fensterposition pro Account:** Ist unter Einstellungen → Fenster „Fensterposition pro Account
merken“ eingeschaltet (Standard), merkt sich Nexus RAM Position und Größe jedes Roblox-Fensters und
stellt sie beim nächsten Start dieses Accounts wieder her.
