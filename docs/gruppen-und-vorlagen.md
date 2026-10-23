# Gruppen und Startvorlagen

[← Übersicht](../README.md)

## Gruppen

Gruppen fassen Accounts zusammen – zum Beispiel alle Accounts für ein bestimmtes Spiel.

**Gruppen → Neue Gruppe**

| Feld | Bedeutung |
| --- | --- |
| Name | max. 40 Zeichen, eindeutig |
| Farbe | Farbmarkierung in Listen und Filtern |
| Symbol | Kleines Symbol vor dem Namen |
| Startvorlage | Optional: eine [Startvorlage](#startvorlagen), die mit „Vorlage starten“ ausgeführt wird |

Auf der Gruppenseite siehst du für jede Gruppe ihre Accounts mit Status und kannst:

- **Gruppe starten** – öffnet den Startdialog mit allen startbereiten Accounts der Gruppe.
- **Vorlage starten** – führt die verknüpfte Startvorlage direkt aus.
- die Reihenfolge der Gruppen mit den Pfeilen ändern, die Gruppe bearbeiten oder löschen.

Accounts ordnest du über Rechtsklick → **In Gruppe verschieben** zu (auch für mehrere ausgewählte
Accounts gleichzeitig) oder beim Hinzufügen bzw. Bearbeiten. Wird eine Gruppe gelöscht, bleiben ihre
Accounts erhalten und stehen danach unter „Ohne Gruppe“.

## Startvorlagen

Eine Startvorlage speichert einen wiederkehrenden Start: welches Spiel, welche Accounts, mit welchem
Abstand – und wie die Fenster danach angeordnet werden.

**Launcher → Startvorlagen → Neue Vorlage**

| Feld | Bedeutung |
| --- | --- |
| Name | max. 60 Zeichen |
| Place-ID | Das Spiel (Zahl aus dem Roblox-Link, z. B. `1818`) |
| Link zum privaten Server | Optional: Link mit `privateServerLinkCode=…` |
| Gruppe | Optional: Alle Accounts dieser Gruppe werden mitgestartet – auch solche, die erst später zur Gruppe kommen |
| Startabstand (s) | 1–300 s; Rückfallwert, siehe [Startreihenfolge](spiele-starten.md#startreihenfolge-und-startabstand) |
| Gleichzeitige Starts | 1–10 |
| Layout | Keins, Raster, Nebeneinander oder Untereinander – die Fenster werden nach dem Start automatisch so angeordnet |
| Accounts | Einzeln gewählte Accounts, zusätzlich zur Gruppe |

In der Vorlagenliste kannst du jede Vorlage **Starten**, **Bearbeiten**, **Kopieren** oder **Löschen**.

Beim Start einer Vorlage werden nur Accounts mit gültiger Sitzung berücksichtigt, die nicht schon
laufen; übersprungene Accounts nennt die Meldung. Ist ein Layout gewählt, ordnet Nexus RAM die
Fenster an, sobald alle Starts der Vorlage abgeschlossen sind – mit Monitor, Abstand und Rand aus
den [Fenster-Einstellungen](einstellungen.md#fenster).
