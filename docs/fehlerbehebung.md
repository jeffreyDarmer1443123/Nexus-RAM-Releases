# Fehlerbehebung und FAQ

[← Übersicht](../README.md)

Fehlermeldungen in Nexus RAM nennen die Ursache und – bei technischen Fehlern – einen
**Diagnosecode** (z. B. `E_NETWORK`, Liste [unten](#diagnosecodes)). Alle Ereignisse stehen außerdem
im Bereich **Aktivität**.

## Häufige Probleme

### Windows blockiert den Installer („Der Computer wurde durch Windows geschützt“)
Der Installer ist nicht mit einem Code-Signing-Zertifikat signiert. „Weitere Informationen“ →
„Trotzdem ausführen“. Details: [Installation](installation.md#windows-smartscreen).

### „Roblox Player wurde nicht gefunden“
Nexus RAM findet den Roblox Player über dessen Registrierung in Windows.
1. Roblox Player von [roblox.com/download](https://www.roblox.com/download) installieren und einmal
   normal starten.
2. Nexus RAM neu starten oder **Einstellungen → Daten & Sicherheit → Cache leeren**.

Ein als Roblox-Handler registrierter Drittanbieter-Bootstrapper wird unverändert verwendet.

### Status „Sitzung abgelaufen“ (`E_SESSION_EXPIRED`)
Roblox hat die Sitzung beendet – etwa durch „Überall abmelden“, eine Passwortänderung oder lange
Inaktivität. Rechtsklick auf den Account → **Sitzung hinzufügen** und neu anmelden.

### Status „Prüfung nötig“ (`E_CHALLENGE_REQUIRED`)
Roblox verlangt eine interaktive Bestätigung (z. B. CAPTCHA). Nexus RAM umgeht so etwas nicht.
Melde dich über **Sitzung hinzufügen → Im Roblox-Fenster anmelden** neu an.

### „Rate Limit“ (`E_RATE_LIMITED`)
Roblox begrenzt vorübergehend die Anfragen. Einige Minuten warten; Massenimporte und
Sitzungsprüfungen stoppen in diesem Fall von selbst.

### Der zweite Client beendet den ersten
- Prüfe **Einstellungen → Launcher → Mehrere Clients ermöglichen** (muss an sein).
- Schau im Bereich **Aktivität** nach Warnungen wie „ROBLOX_singletonEvent konnte nicht geschlossen
  werden“ oder „… nicht gefunden“ – sie nennen PID und Grund.
- Nach einem Roblox-Update kann sich das Verhalten ändern. Roblox unterstützt mehrere Clients nicht
  offiziell; eine Garantie gibt es nicht.

### „Der Spielclient unterstützt diese parallele Ausführung nicht“ (`E_UNSUPPORTED`)
Für die installierte Roblox-Version wurde (per Probelauf) nachgewiesen, dass kein zweiter Client
möglich ist. Starte einen einzelnen Account (er ersetzt dann den laufenden Client) oder schließe
zuerst den laufenden Client. Nach einem Roblox-Update wird neu geprüft.

### „Roblox wurde aufgerufen, aber es wurde kein Spielclient-Prozess erkannt“ (`E_PROCESS`)
Roblox hat den Start abgelehnt oder installiert gerade ein Update. Kurz warten und erneut starten.
Prüfe, ob sich Roblox über die Website normal starten lässt.

### „Für diesen Account läuft bereits ein Client“
Pro Account startet Nexus RAM höchstens einen Client. Schließe ihn zuerst unter **Sitzungen**.

### Starts dauern so lange wie der Startabstand
Normalerweise startet der nächste Account, sobald der vorherige bereit ist. Dauert jeder Start so lange
wie der eingestellte Startabstand, konnte `ROBLOX_singletonEvent` nicht geschlossen werden (siehe
Aktivität) oder „Mehrere Clients ermöglichen“ ist aus. Siehe
[Startreihenfolge](spiele-starten.md#startreihenfolge-und-startabstand).

### Anti-AFK springt nicht
Anti-AFK wartet, bis du mindestens 2 Sekunden lang weder Maus noch Tastatur benutzt und keine Taste
gedrückt hältst. Es wirkt nur auf von Nexus RAM gestartete Clients.

### Auto-Rejoin startet nicht neu
- Ist Auto-Rejoin in den Einstellungen eingeschaltet **und** die Sitzung als überwacht markiert?
- Hast du den Client selbst über Nexus RAM geschlossen? Dann ist kein Rejoin vorgesehen.
- Im Bereich **Sitzungen** oben: Ist der Rejoin pausiert oder aufgegeben? Der Grund steht daneben;
  mit **Fortsetzen** geht es weiter.

### Sitzungen sind nach PC- oder Windows-Konto-Wechsel nicht mehr lesbar
Der Tresorschlüssel ist an dein Windows-Konto gebunden. Übertrage Accounts mit einem
[Backup inklusive Sitzungen](daten-und-sicherheit.md#backup-erstellen).

### Die Datenübernahme findet keine Daten von Nexus RAM 0.x
Gesucht wird in `%APPDATA%\com.nexusram.app` (auch, wenn 0.x dort auf einen anderen Datenordner
verweist). Wurden die alten Daten bei der Deinstallation gelöscht, nutze ein `.nxbackup`-Backup aus
0.x über **Backup importieren**.

### Kein Update-Hinweis
Prüfe „Beim Start nach Updates suchen“ und die Internetverbindung, oder suche manuell unter
**Einstellungen → Info & Updates**. Siehe [Updates](updates.md).

### Nexus RAM startet nicht
Erscheint „Nexus RAM konnte nicht starten“, steht der Grund in der Meldung. Die Logdateien liegen in
`%APPDATA%\com.nexusram2.app\logs`. Es läuft immer nur eine Instanz: Ein zweiter Start holt das
vorhandene Fenster nach vorn – prüfe auch den Infobereich.

## Fehler melden

Unter **Einstellungen → Daten & Sicherheit → Diagnose exportieren** entsteht eine JSON-Datei ohne
Sitzungswerte, Passwörter oder Tokens. Sie enthält Version, Roblox-Installation, Einstellungen,
letzte Ereignisse und einen Logauszug und hilft bei der Fehlersuche.

## FAQ

**Ist die Nutzung erlaubt?**
Nexus RAM nutzt die offiziellen Wege von Roblox (Anmeldeseite, Anmelde-Ticket, offizieller Client).
Mehrere gleichzeitige Clients und simulierte Eingaben (Anti-AFK) unterstützt Roblox nicht offiziell;
sie können den Nutzungsbedingungen widersprechen. Beides ist abschaltbar, Anti-AFK ist standardmäßig
aus. Die Nutzung erfolgt auf eigene Verantwortung.

**Speichert Nexus RAM meine Passwörter?**
Nein. Gespeichert werden nur Sitzungswerte, verschlüsselt im Tresor. Bei „Anmeldungen aus Datei“
werden Passwörter nur zum Vorausfüllen verwendet und nicht gespeichert.

**Braucht Nexus RAM Administratorrechte?**
Nein – weder für die Installation noch im Betrieb.

**Werden Daten an den Entwickler gesendet?**
Nein. Siehe [Datenschutz und Netzwerkziele](daten-und-sicherheit.md#datenschutz).

**Kann ich Nexus RAM auf mehreren PCs nutzen?**
Ja, jede Installation hat ihre eigenen Daten. Übertragen kannst du sie per verschlüsseltem Backup.

**Kann ich Nexus RAM 0.x und 1.x parallel nutzen?**
Beide teilen sich Produktnamen und Installationsordner; der Installer von 1.x ersetzt 0.x. Die Daten
sind getrennt; die alten lassen sich übernehmen.

## Diagnosecodes

| Code | Bedeutung |
| --- | --- |
| `E_VALIDATION` | Ungültige Eingabe |
| `E_NOT_FOUND` | Etwas wurde nicht gefunden |
| `E_CONFLICT` | Widerspruch zum aktuellen Zustand (z. B. Account bereits gespeichert, Client läuft schon) |
| `E_NETWORK` | Verbindungsproblem |
| `E_REJECTED` | Roblox hat die Anfrage abgelehnt |
| `E_RATE_LIMITED` | Roblox begrenzt die Anfragen |
| `E_SESSION_EXPIRED` | Sitzung abgelaufen oder ungültig |
| `E_CHALLENGE_REQUIRED` | Roblox verlangt eine Sicherheitsprüfung |
| `E_NO_SESSION` | Für den Account ist keine Sitzung gespeichert |
| `E_ROBLOX_NOT_INSTALLED` | Roblox Player nicht gefunden |
| `E_UNSUPPORTED` | Vorgang so nicht möglich (z. B. zweiter Client blockiert) |
| `E_CANCELLED` | Abgebrochen |
| `E_PROCESS` | Problem mit einem Roblox-Prozess oder -Fenster |
| `E_BACKUP_AUTH` | Backup beschädigt, verändert oder falsche Passphrase |
| `E_BACKUP` | Sonstiger Backup-Fehler |
| `E_UPDATE` | Update konnte nicht geprüft oder installiert werden |
| `E_SECRET_STORE` | Problem mit dem Tresor |
| `E_DATABASE` | Datenbankfehler |
| `E_IO` / `E_PERMISSION` | Datei- bzw. Zugriffsproblem |
| `E_TIMEOUT` | Zeitüberschreitung |
| `E_MIGRATION` | Datenübernahme fehlgeschlagen |
| `E_INTERNAL` | Unerwarteter Fehler – bitte Diagnose exportieren |
