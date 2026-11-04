# Architektur – Anonymisator

**Status: dokumentierte Zielarchitektur; native App und vollständige Pipeline noch nicht implementiert.**

Anonymisator ist ein eigenständiges Android-Projekt für lokale Dokumentenverarbeitung. Die Architektur ist auf Datenminimierung, nachvollziehbare Nutzerentscheidungen und die Integrität des Originals ausgerichtet.

## Zielpipeline

1. **Import:** Nutzer wählt eine lokale Datei über die Android-Dateiauswahl aus. Das Original bleibt unverändert.
2. **Analyse:** Bei textbasierten PDFs wird zuerst vorhandener Text geprüft und extrahiert. Bei Bildseiten erfolgt lokales Rendering und OCR.
3. **Erkennung:** Mögliche personenbezogene und andere sensible Angaben werden markiert. Automatische Treffer sind Vorschläge, keine abschließende Bewertung.
4. **Prüfung:** Nutzer erhält eine seitenbezogene Vorschau, kann Treffer korrigieren, ergänzen oder entfernen und muss alle Seiten kontrollieren.
5. **Schwärzung:** Eine separate Exportkopie wird erzeugt. Die Schwärzung muss den zugrunde liegenden Text und Bildinhalt entfernen; eine bloße grafische Überdeckung genügt nicht.
6. **Bereinigung:** Metadaten, Textlayer, eingebettete Inhalte und sonstige rekonstruierbare Informationen werden untersucht und soweit erforderlich entfernt.
7. **Validierung und Export:** Vor dem Export werden Negativtests durchgeführt. Erst nach erfolgreicher Prüfung wird eine lokale Arbeitskopie ausgegeben.

## Sicherheits- und Integritätsregeln

- Das Original wird nicht überschrieben.
- Import, Verarbeitung und Export müssen als getrennte Schritte erkennbar sein.
- Temporäre Dateien benötigen ein dokumentiertes Speicher- und Löschkonzept.
- Vor einer späteren Netzwerk- oder KI-Funktion darf keine Dokumentenübertragung stattfinden.
- Eine Erkennungsmarkierung ist kein Beweis für vollständige Anonymität.
- Der Export muss nachträglich auf Textsuche, Copy/Paste, OCR, Metadaten und eingebettete Inhalte geprüft werden.
- Fehler, unleserliche Passagen und nicht unterstützte Dateitypen müssen verständlich gemeldet werden.

## Nicht-Ziele

Keine direkte KI-Schnittstelle, keine automatische Datenübertragung zu Student Müller und keine autonome rechtliche Bewertung von Dokumenten. Anonymisator bereitet Dateien lokal vor; über eine spätere Verwendung entscheidet allein der Nutzer.

## Nachgewiesener Stand

Tesseract 5.5.4 wurde am 01.11.2026 in Termux installiert. Am 02.11.2026 wurden deu und eng in der Sprachenliste angezeigt und ein erster lokaler Bild-OCR-Test ausgeführt. Eine systematische Qualitätsmessung, PDF-Pipeline, Sensitiv-Datenerkennung, echte dauerhafte Schwärzung, Metadatenbereinigung und native Android-App sind nicht nachgewiesen.
