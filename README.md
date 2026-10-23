# Nexus RAM

Roblox-Account-Manager für Windows: verwaltet deine eigenen Accounts lokal, startet Spiele über den
offiziellen Roblox-Client und ordnet Roblox-Fenster an. Keine Cloud, keine Telemetrie.

Dieses Repository enthält nur die **Releases** (Installer und Updates), nicht den Quellcode.

## Installation

1. Voraussetzungen: Windows 10 oder 11 (64 Bit) und der installierte Roblox Player.
2. Unter [Releases](https://github.com/jeffreyDarmer1443123/Nexus-RAM-Releases/releases/latest)
   die Datei `Nexus.RAM_<Version>_x64-setup.exe` herunterladen und ausführen.
   Administratorrechte sind nicht nötig.
3. Windows SmartScreen warnt, weil der Installer nicht mit einem Zertifikat signiert ist:
   „Weitere Informationen“ → „Trotzdem ausführen“.

## Updates

Nexus RAM prüft beim Start, ob eine neue Version vorliegt, und meldet sie. Installiert wird unter
**Einstellungen → Info & Updates → „Installieren und neu starten“**. Ein Update wird nur
installiert, wenn seine Minisign-Signatur und seine SHA-256-Prüfsumme stimmen.

## Prüfsummen

Jedes Release enthält `SHA256SUMS.txt`. In PowerShell prüfen:

```powershell
Get-FileHash .\Nexus.RAM_<Version>_x64-setup.exe -Algorithm SHA256
```

## Hinweise

- Verwalte nur Accounts, die dir gehören. Sitzungswerte (`.ROBLOSECURITY`) sind wie Passwörter.
- Mehrere gleichzeitige Roblox-Clients unterstützt Roblox nicht offiziell; Nexus RAM schließt dafür
  im selbst gestarteten Client das Handle auf `ROBLOX_singletonEvent` (abschaltbar). Das kann den
  Nutzungsbedingungen von Roblox widersprechen.
- Ist „Nexus RAM“ 0.x installiert, ersetzt der Installer das alte Programm. Die alten Daten bleiben
  erhalten und lassen sich in Nexus RAM unter Einstellungen → Daten & Sicherheit übernehmen.
