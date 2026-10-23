# Installation

[← Übersicht](../README.md)

## Systemvoraussetzungen

| | |
| --- | --- |
| Betriebssystem | Windows 10 oder Windows 11, 64 Bit |
| Roblox | Installierter Roblox Player ([roblox.com/download](https://www.roblox.com/download)). Accounts lassen sich auch ohne Roblox verwalten, Starten geht aber erst mit Roblox. |
| Rechte | Keine Administratorrechte nötig – Nexus RAM wird nur für dein Windows-Benutzerkonto installiert. |
| Speicherplatz | ca. 250 MB (der Installer enthält die WebView2-Laufzeit, damit keine Downloads nötig sind) |
| Internet | Für Anmeldung, Spielstarts, Profilbilder und Updates |

## Herunterladen

Öffne die [neueste Version](https://github.com/jeffreyDarmer1443123/Nexus-RAM-Releases/releases/latest)
und lade unter **Assets** die passende Datei herunter:

| Datei | Wofür |
| --- | --- |
| `Nexus.RAM_<Version>_x64-setup.exe` | **Empfohlen.** Normaler Installer. |
| `Nexus.RAM_<Version>_x64_de-DE.msi` / `…_en-US.msi` | Alternative im MSI-Format (z. B. für Softwareverteilung). |
| `*.sig` | Signaturen für das automatische Update – nicht zum Herunterladen gedacht. |
| `latest.json` | Update-Information für installierte Versionen. |
| `SHA256SUMS.txt` | Prüfsummen aller Dateien (siehe [Download prüfen](#download-prüfen-optional)). |

## Windows SmartScreen

Beim ersten Start des Installers zeigt Windows oft
**„Der Computer wurde durch Windows geschützt“**. Das liegt daran, dass der Installer nicht mit einem
kostenpflichtigen Code-Signing-Zertifikat signiert ist – nicht daran, dass etwas Schädliches gefunden
wurde.

1. Auf **„Weitere Informationen“** klicken.
2. **„Trotzdem ausführen“** wählen.

Wenn du sichergehen willst, prüfe vorher die Prüfsumme (nächster Abschnitt).

## Download prüfen (optional)

Jedes Release enthält `SHA256SUMS.txt`. Vergleiche den Wert deiner heruntergeladenen Datei mit der
Zeile in dieser Datei. In PowerShell:

```powershell
Get-FileHash "$env:USERPROFILE\Downloads\Nexus.RAM_1.0.1_x64-setup.exe" -Algorithm SHA256
```

Die ausgegebene Zeichenfolge (Groß-/Kleinschreibung egal) muss mit dem Eintrag in `SHA256SUMS.txt`
übereinstimmen. Weicht sie ab, die Datei nicht ausführen und erneut herunterladen.

## Installieren

1. `Nexus.RAM_<Version>_x64-setup.exe` ausführen. Der Installer erscheint in der Sprache deines
   Windows (Deutsch oder Englisch).
2. Dem Assistenten folgen.
3. Auf der letzten Seite kannst du Nexus RAM direkt starten. Danach findest du es im Startmenü.

Installationsordner: `%LOCALAPPDATA%\Nexus RAM`

## Umstieg von Nexus RAM 0.x

Hast du die ältere Version **Nexus RAM 0.x** installiert, gilt:

- Der Installer **ersetzt das alte Programm** (gleicher Produktname, gleicher Installationsordner).
  Windows kann dabei fragen, ob die vorhandene Version zuerst deinstalliert werden soll – das ist
  in Ordnung.
- Falls dabei angeboten wird, **App-Daten zu löschen: nicht ankreuzen.** Sonst gehen deine alten
  Accounts verloren, bevor du sie übernehmen konntest.
- Deine alten Daten bleiben in `%APPDATA%\com.nexusram.app` liegen. Nexus RAM liest sie dort nur
  und übernimmt sie auf Wunsch – siehe
  [Datenübernahme aus Nexus RAM 0.x](erste-schritte.md#datenübernahme-aus-nexus-ram-0x).

## Deinstallieren

1. **Windows-Einstellungen → Apps → Installierte Apps → Nexus RAM → Deinstallieren**.
2. Wenn du auch alle Accounts und Einstellungen löschen willst, entferne danach (falls noch
   vorhanden) diese Ordner:

| Ordner | Inhalt |
| --- | --- |
| `%APPDATA%\com.nexusram2.app` | Datenbank, verschlüsselte Sitzungen, Tresorschlüssel, Logs, Sicherungen |
| `%LOCALAPPDATA%\com.nexusram2.app` | Zwischenspeicher der Oberfläche |

> `com.nexusram2.app` ist die interne Kennung von Nexus RAM 1.x. Der Ordner
> `%APPDATA%\com.nexusram.app` (ohne „2“) gehört zur alten Version 0.x.

Tipp: Vorher unter **Einstellungen → Daten & Sicherheit → Backup erstellen** ein verschlüsseltes
Backup anlegen, falls du die Accounts später wieder brauchst.
