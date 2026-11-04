# OCR mit Tesseract unter Termux

**Stand: 04.11.2026**  
**Status: Tesseract 5.5.4 auf dem Zielgerät installiert; deu/eng nachgewiesen; erster lokaler OCR-Lauftest am 02.11.2026 erfolgreich. Reproduzierbarkeit und Erkennungsqualität weiter zu prüfen.**

## Ziel

Prüfen, ob Tesseract als lokal ausführbare OCR-Engine auf dem Android-Entwicklungsgerät unter Termux eingesetzt werden kann. Die OCR soll ohne Cloud-Dienst arbeiten und später als lokaler Verarbeitungsschritt in die Dokumentenpipeline integriert werden.

## Technische Grundlage

Das offizielle Termux-Paketrepository enthält ein Buildskript für das Paket `tesseract`:

https://github.com/termux/termux-packages/blob/master/packages/tesseract/build.sh

Das dort derzeit sichtbare Buildskript nennt Tesseract 5.5.3 und die Paketlizenz Apache-2.0. Das Paket-Buildskript lädt im gezeigten Build-Schritt englische Sprachdaten (`eng.traineddata`). Daraus folgt ausdrücklich **nicht**, dass deutsche Sprachdaten (`deu`) automatisch installiert sind.

Upstream-Projekt:
https://github.com/tesseract-ocr/tesseract

Termux-Paketprojekt:
https://github.com/termux/termux-packages

Die Repository-Angaben können sich ändern. Vor der Installation ist der aktuelle Paketstand im verwendeten Termux-Repository zu prüfen.

## Tatsächlich dokumentierte Termux-Schritte

Die folgenden Angaben stammen aus dem früheren Arbeitsverlauf und sind als ausgeführte Schritte dokumentiert:

### 01.11.2026 – Paket suchen und installieren

Ausgeführte Suche:

```sh
pkg search tesseract
```

Ausgabe enthielt:

```text
tesseract/stable 5.5.4 aarch64
```

Anschließend wurde ausgeführt:

```sh
pkg install tesseract
```

Die Installation wurde erfolgreich abgeschlossen. Der Paketmanager meldete Tesseract 5.5.4 und 16 Abhängigkeiten, 27,5 MB heruntergeladene Pakete sowie rund 111 MB zusätzlichen Speicherbedarf.

### 02.11.2026 – Sprachdaten und OCR-Test

Ausgeführter Sprachdatencheck:

```sh
tesseract --list-langs
```

Nachgewiesene Sprachen:

```text
deu
eng
```

Ausgeführter OCR-Aufruf:

```sh
tesseract ~/AndroidLocalAgent/data/ocr_test.png stdout -l deu+eng
```

Der erste Testlauf lieferte bereits Text, enthielt jedoch Fehler. Dokumentierte Erkennung unter anderem:

```text
ANDROIDLOCAL AGENT
CORTEST2028
Dokumenten-Intaligenz
```

Ein verbesserter Testlauf erkannte:

```text
ANDROID LOCAL AGENT
OCR TEST 2026
Dokumenten-Intelligenz
```

**Bewertung:** Installation, Sprachdatenverfügbarkeit und lokaler OCR-Aufruf sind damit als praktisch durchgeführt dokumentiert. Die Testausgabe zeigt eine grundsätzlich funktionierende Erkennung, aber noch keine belastbare Qualitätsmessung. Insbesondere ist ein einzelnes Testbild kein Nachweis für die sichere Verarbeitung komplexer Bescheide oder PDFs.

## Vorgeschlagene Prüfsequenz

Die folgenden Befehle sind ein **Testplan**, kein behauptetes Protokoll bereits ausgeführter Befehle. Vor dem Ausführen auf dem Gerät prüfen, ob die Termux-Installation aus einer aktuellen, unterstützten Quelle stammt.

### 1. Paketindex aktualisieren und installierten Stand erfassen

```sh
pkg update
pkg upgrade
```

### 2. Installation bei Bedarf prüfen bzw. reparieren

```sh
pkg install tesseract
```

### 3. Installation und Version nachweisen

```sh
command -v tesseract
tesseract --version
```

Die vollständige Versionsausgabe in einem Testprotokoll sichern.

### 4. Verfügbare Sprachdaten prüfen

```sh
tesseract --list-langs
```

Nur wenn `deu` in der Liste erscheint, ist die deutsche Spracheinstellung für diesen Test nachgewiesen. Nicht aus der Paketinstallation auf deutsche Sprachdaten schließen.

### 5. Anonymisiertes Testbild verarbeiten

Ein synthetisches Testbild mit einem bekannten kurzen Text verwenden. Keine echten Bescheide oder personenbezogenen Dokumente für den ersten Funktionstest nutzen.

```sh
tesseract testbild.png stdout -l eng
```

Für einen deutschen Test erst nach nachgewiesenem Vorhandensein von `deu`:

```sh
tesseract testbild_de.png stdout -l deu
```

### 6. Testprotokoll

Festhalten:

- Datum und Geräte-/Android-Version.
- Termux-Version und Paketquelle.
- Tesseract-Version.
- Ausgabe von `tesseract --list-langs`.
- Testbild (synthetisch) und erwarteter Text.
- Tatsächlich erkannter Text.
- Erkennungsfehler, Umlaute, Zeilenumbrüche und Layoutverluste.
- Laufzeit und Speicherbedarf, soweit messbar.
- Exit-Code.

## Deutsche Sprachdaten

Der Termux-Buildschritt zeigt eine automatische Bereitstellung englischer Daten. Für Deutsch muss ein zulässiger und reproduzierbarer Weg gewählt werden. Vor einer Übernahme sind Herkunft, Version und Lizenz der konkreten `deu.traineddata` zu dokumentieren. Die Sprachdaten sind nicht automatisch mit der Lizenz des Tesseract-Programms gleichzusetzen.

Upstream-Datenprojekt:
https://github.com/tesseract-ocr/tessdata

## PDF-Verarbeitung

Tesseract verarbeitet Bilddaten. Für gescannte PDFs ist daher eine separate, lokal ausführbare PDF-Seitenvorverarbeitung erforderlich, die jede relevante Seite in ein geeignetes Bildformat rendert. Diese Pipeline ist noch nicht implementiert. Textbasierte PDFs sollten später zunächst auf direkt extrahierbaren Text geprüft werden, bevor OCR ausgeführt wird.

## Python-Anbindung

Eine Python-Anbindung wird erst nach einem erfolgreichen Kommandozeilentest untersucht. Zunächst sollte ein kontrollierter lokaler Prozessaufruf verwendet werden. Abhängigkeiten, Pfade, Fehlerausgaben und Dateiberechtigungen sind zu dokumentieren. Eine Python-Bibliothek ist nicht automatisch erforderlich.

## Datenschutz und Sicherheit

- Ausschließlich synthetische oder vollständig anonymisierte Testdateien verwenden.
- OCR lokal ausführen; keine externen OCR-Webdienste einbinden.
- Vor einer späteren KI-Übermittlung eine ausdrückliche Freigabe verlangen.
- OCR-Ausgaben als fehleranfällig behandeln und niemals stillschweigend ergänzen.
- Originaldateien unverändert lassen.
- Temporäre Bild- und Textdateien kontrolliert verwalten.

## Erfolgskriterien

Die OCR-Vorprüfung gilt erst dann als erfolgreich, wenn:

1. Tesseract nachweislich auf dem Zielgerät installiert ist.
2. Versions- und Sprachdaten-Ausgaben protokolliert sind.
3. Ein synthetisches Testbild reproduzierbar verarbeitet wurde.
4. Der erkannte Text mit dem Solltext verglichen wurde.
5. Fehler, Laufzeit und Grenzen dokumentiert sind.

Erst danach wird der Status in der Funktionsübersicht von „zu verifizieren“ auf „erfolgreich getestet“ geändert.
