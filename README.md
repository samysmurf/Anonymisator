# Anonymisator

**Lokale Dokumentenverarbeitung auf Android – unabhängig von Student Müller**

Anonymisator ist ein eigenständiges Open-Source-Projekt. Ziel ist, Dokumente auf dem Android-Gerät vorzubereiten, bevor Nutzer sie gegebenenfalls selbst in einen externen Dienst übernehmen. Vorgesehen sind Textextraktion und lokale OCR, Erkennung sensibler Angaben, manuelle Prüfung, echte dauerhafte Schwärzung, Metadatenkontrolle und lokaler Export.

**Frühe Entwicklungsphase**

**Wichtige Einschränkung:** Eine native Android-App, eine vollständige PDF-Verarbeitungspipeline, automatische Datenerkennung und eine nachweislich dauerhafte Schwärzungsfunktion sind noch nicht implementiert. Das Repository enthält derzeit Dokumentation und technische Vorarbeiten, kein installierbares App-Paket. Es darf deshalb noch nicht zur Bearbeitung vertraulicher Originaldokumente als Sicherheitswerkzeug eingesetzt werden.

## Zielablauf

1. Dokument lokal auswählen und Original unverändert lassen.
2. Text aus textbasierten PDFs extrahieren oder gescannte Seiten lokal per OCR erkennen.
3. Mögliche sensible Angaben markieren.
4. Erkennung in einer verständlichen Vorschau manuell prüfen und korrigieren.
5. Eine separate Exportkopie technisch dauerhaft schwärzen.
6. Textlayer, Bildinhalte, Anhänge und Metadaten auf verbliebene Informationen prüfen.
7. Erst nach vollständiger Nutzerprüfung lokal exportieren.

Ein bloßes schwarzes Rechteck über dem ursprünglichen Text ist keine sichere Schwärzung.

## Dokumentierter technischer Stand

| Bestandteil | Nachgewiesener Stand |
|---|---|
| Android-/Termux-Vorarbeiten | auf einem realen Android-Gerät dokumentiert |
| Tesseract | Version 5.5.4 am 01.11.2026 unter Termux installiert |
| Sprachdaten | deu und eng am 02.11.2026 in der Tesseract-Ausgabe gelistet; Herkunft und Lizenz sind noch zu klären |
| OCR-Test | ein lokaler Testlauf mit synthetischem Testbild lieferte Text; Erkennungsqualität nicht systematisch gemessen |
| PDF-Pipeline | geplant, nicht implementiert |
| Sensitiv-Datenerkennung | geplant, nicht implementiert |
| Dauerhafte Schwärzung | geplant, nicht implementiert |
| Metadatenbereinigung und Export | geplant, nicht implementiert |
| Native Android-App | geplant; kein App-Build nachgewiesen |

Der dokumentierte erste OCR-Test ist ein realer technischer Vorversuch, aber kein Qualitätsnachweis für Bescheide oder komplexe PDFs. Versions-, Sprachdaten- und Qualitätstests müssen reproduzierbar wiederholt werden.

## Abgrenzung zu Student Müller

[Student Müller](https://github.com/samysmurf/Student-Mueller) ist ein separates ChatGPT-basiertes Informations- und Selbsthilfeprojekt. Anonymisator ist davon technisch unabhängig:

- keine direkte KI-Schnittstelle,
- keine automatische Datenübertragung zu Student Müller,
- keine gemeinsame Laufzeit,
- keine Abhängigkeit von der Fertigstellung des jeweils anderen Projekts.

Eine spätere externe Weitergabe bleibt eine bewusste Entscheidung des Nutzers. Anonymisator soll keine automatische Übermittlung auslösen.

## Einstieg in die technische Dokumentation

- [OCR mit Tesseract unter Termux](docs/OCR_TESSERACT_TERMUX.md) – ausgeführte Schritte, Testausgaben und offene Prüfungen
- [Android-/Termux-Vorarbeiten](docs/TECHNISCHE_VORARBEITEN_TERMUX.md) – Entwicklungsumgebung und dokumentierte Berechtigungsgrenzen
- [Architektur](docs/ARCHITEKTUR.md) – Zielpipeline und Sicherheitsprinzipien
- [Datenschutz und Sicherheit](docs/DATENSCHUTZ.md)
- [Funktionsstatus](docs/FUNKTIONSSTATUS.md)
- [Roadmap](ROADMAP.md)
- [Testkonzept](docs/TESTKONZEPT.md)
- [Barrierefreiheit – @Vision](docs/BARRIEREFREIHEIT.md)

## Sicherheit und Testdaten

Bis zur Implementierung und erfolgreichen Prüfung der vollständigen Verarbeitung dürfen keine vertraulichen Originaldokumente als vermeintlich anonymisierte Dateien weitergegeben werden. Automatische Erkennung ist fehleranfällig; jede Markierung muss durch einen Menschen geprüft werden.

In GitHub-Issues, Pull Requests, Commits und Testdateien dürfen ausschließlich synthetische oder wirksam anonymisierte Inhalte erscheinen. Keine echten Namen, Anschriften, Geburtsdaten, Gesundheitsdaten, Aktenzeichen, Zugangsdaten, Tokens oder privaten Schlüssel veröffentlichen.

## Lizenzmodell

- Eigener Programmcode: Apache License 2.0 – vollständiger Lizenztext in [LICENSE-CODE](LICENSE-CODE).
- Originäre Projektdokumentation: CC BY-SA 4.0 – Zuordnung und Lizenzhinweis in [LICENSE-DOCS.md](LICENSE-DOCS.md).
- [LICENSE](LICENSE) ist das Inhalts- und Zuordnungsverzeichnis; die Lizenzdateien gelten nur für Inhalte, deren Rechte die Beitragenden wirksam lizenzieren dürfen.
- Drittanbieterkomponenten, Tesseract-Sprachdaten, Bibliotheken, Modelle, Marken und Testdaten sind gesondert zu prüfen.

Derzeit enthält das Repository noch keine native Android-App und keinen nachgewiesenen App-Quellcode. Lizenzangaben für künftigen eigenen Code sind daher keine Aussage, dass eine fertige App vorliegt.

## Mitwirkung

Dokumentation, reproduzierbare Tests, technische Reviews und Hinweise auf Fehler sind willkommen. Bitte zuerst [CONTRIBUTING.md](CONTRIBUTING.md) und [SECURITY.md](SECURITY.md) lesen. Sicherheit und Integrität gehen vor Funktionsumfang.
