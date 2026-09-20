# Mutexx Playlister – Downloads

Hier liegen die fertigen Installer von **Mutexx Playlister** und die Datei, die
die Anwendung nach Updates fragt. **Quelltext liegt hier keiner** – der wohnt in
einem privaten Repository. Dieses hier ist öffentlich, weil ein Updater sich
nicht anmelden kann: er ruft die Adresse unangemeldet auf, und was er nicht
lesen darf, kann er auch nicht anbieten.

## Herunterladen

Die jeweils neueste Fassung steht unter [Releases](../../releases/latest).
Gesucht ist die Datei, die auf `-setup.exe` endet.

**Nur Windows.** Die Anwendung legt ihre Daten unter `%LOCALAPPDATA%` ab und
holt den Claude-Schlüssel aus dem Windows Credential Manager; ein macOS- oder
Linux-Paket wäre ein Versprechen, das der Code nicht hält.

Installiert wird nach `C:\Program Files\Mutexx Production\Mutexx Playlister`,
die Daten liegen unter
`%LOCALAPPDATA%\Mutexx Production\Mutexx Playlister`. Weil das Programm unter
*Programme* liegt, fragt **auch jedes Update** einmal nach Administratorrechten
– ohne die lässt sich der Ordner nicht ersetzen.

## Warum Windows beim Start warnt

Mutexx Playlister ist **nicht code-signiert**, und das ist eine Entscheidung,
keine Nachlässigkeit: ein Zertifikat kostet jährlich Geld und macht die
Anwendung um kein Byte sicherer – es kauft nur das Wegbleiben der Warnung.

Was die Warnung wirklich sagt: diese Datei trägt kein bezahltes Zertifikat, und
Microsoft hat sie selten gesehen. Sie sagt **nicht**, dass etwas schädlich ist.

- „Weitere Informationen" → „Trotzdem ausführen" startet die Anwendung.
- Ein ZIP umgeht die Warnung **nicht**: Windows vererbt die Herkunftsmarkierung
  beim Entpacken an die enthaltenen Dateien.
- Ohne Zertifikat sammelt **jede neue Fassung** wieder von vorn Vertrauen.

## Prüfsummen

An jeder Veröffentlichung hängt `SHA256SUMS.txt`. So prüft man eine Datei nach:

```powershell
Get-FileHash .\Mutexx-Playlister_0.1.0_x64-setup.exe -Algorithm SHA256
```

```bash
sha256sum -c SHA256SUMS.txt --ignore-missing
```

## Automatische Updates

`latest.json` an jeder Veröffentlichung sagt der Anwendung, welche Fassung die
neueste ist und wo sie liegt. **Jedes Paket trägt eine eigene Signatur**, die
Mutexx Playlister gegen einen fest eingebauten öffentlichen Schlüssel prüft,
bevor es etwas installiert. Der Weg vom Server zum Rechner ist damit geschützt –
ganz ohne Authenticode: wer diese Dateien austauschte, käme trotzdem nicht
durch.

Die Anwendung sieht beim Start still nach. Gefunden heisst nicht installiert –
sie zeigt die Fassung an und wartet auf einen Klick.

## Was das Programm macht

Es bringt einen Song zu den Kuratoren, die dazu passen: Analyse läuft lokal
(also auch für unveröffentlichte Titel), die Kontaktliste gehört dem Nutzer, und
angeschrieben wird nur, wer öffentlich zur Einsendung aufruft. Dazu eine
Releaseplanung, die rückwärts vom Veröffentlichungstag rechnet.

Ein Produkt von [Mutexx Production](https://www.mutexxproduction.de).
