# Updates

[← Übersicht](../README.md)

## So kommen Updates zu dir

1. Beim Start fragt Nexus RAM bei GitHub nach, ob es eine neuere Version gibt
   (Einstellung „Beim Start nach Updates suchen“, Standard: an).
2. Gibt es eine, erscheint der Hinweis **„Version X verfügbar“**.
3. Installieren: **Einstellungen → Info & Updates** → **Installieren und neu starten** → bestätigen.
4. Der Download wird mit Fortschritt angezeigt, geprüft und installiert; Nexus RAM startet danach in
   der neuen Version neu. Deine Accounts und Einstellungen bleiben erhalten.

Ohne automatische Prüfung kannst du jederzeit unter **Einstellungen → Info & Updates → Nach Updates
suchen** manuell prüfen.

Laufende Startaufträge werden vor der Installation abgebrochen; laufende Roblox-Clients sind nicht
betroffen.

## Wie Updates abgesichert sind

Ein Update wird nur installiert, wenn **alle** Prüfungen bestehen:

| Prüfung | Schutz gegen |
| --- | --- |
| Quelle ist `https://github.com` (TLS mit Zertifikatsprüfung) | Umleitung auf fremde Server |
| **Minisign-Signatur** mit dem in Nexus RAM eingebauten öffentlichen Schlüssel | Gefälschte oder manipulierte Installer – nur Updates, die mit dem privaten Schlüssel des Herausgebers signiert sind, werden akzeptiert |
| **SHA-256-Prüfsumme** aus der Update-Information | Beschädigte oder unvollständige Downloads |

Fehlt die Prüfsumme oder stimmt etwas nicht, wird das Update **nicht** installiert und eine Meldung
erklärt den Grund. Die Installation erfolgt ohne Administratorrechte nur für dein Benutzerkonto.

## Manuell aktualisieren

Du kannst jederzeit den neuesten Installer von der
[Release-Seite](https://github.com/jeffreyDarmer1443123/Nexus-RAM-Releases/releases/latest)
herunterladen und über die vorhandene Installation installieren. Daten bleiben erhalten.

Ältere Versionen findest du unter
[allen Releases](https://github.com/jeffreyDarmer1443123/Nexus-RAM-Releases/releases). Eine ältere
Version wird nicht automatisch angeboten; installierst du sie manuell, kann eine Datenbank, die schon
von einer neueren Version stammt, abgelehnt werden (Nexus RAM verändert sie dann nicht).
