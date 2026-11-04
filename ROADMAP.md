# Roadmap – Anonymisator

## Phase 1 – Reproduzierbare OCR

- [x] Tesseract 5.5.4-Installation unter Termux am 01.11.2026 dokumentiert.
- [x] Ausgabe von tesseract --list-langs mit deu und eng am 02.11.2026 protokolliert.
- [x] Ersten lokalen OCR-Test mit einem Testbild ausgeführt und Ergebnis dokumentiert.
- [ ] Aktuellen Paket-, Android- und Termux-Stand erneut erfassen.
- [ ] Herkunft und Lizenz der konkreten deu-/eng-Sprachdaten klären.
- [ ] Synthetischen Testsatz mit festem Solltext anlegen.
- [ ] OCR-Qualität, Laufzeit und Ressourcenverbrauch systematisch messen.
- [ ] PDF-Vorverarbeitung evaluieren.

## Phase 2 – Dokumentenpipeline

- [ ] Import und Integritätsprüfung des Originals.
- [ ] Textextraktion aus textbasierten PDFs und lokaler OCR-Fallback.
- [ ] Lokale Erkennung möglicher sensibler Angaben.
- [ ] Vorschau, manuelle Korrektur und vollständige Nutzerprüfung.

## Phase 3 – Sicherer Export

- [ ] Echte dauerhafte Schwärzung einer separaten Kopie.
- [ ] Metadaten-, Textlayer- und eingebettete-Inhalte-Prüfung.
- [ ] Negative Wiederherstellbarkeitstests.
- [ ] Kontrollierter lokaler Export und Löschkonzept.

## Phase 4 – Native Android-App

- [ ] Technologieentscheidung und modulare Architektur.
- [ ] Barrierearme Oberfläche mit TalkBack-Tests.
- [ ] Offline- und Netzwerkprüfungen.
- [ ] Reproduzierbare Builds und Release-Prozess.

**Projektgrenze:** Keine direkte KI-Schnittstelle und keine automatische Übertragung von Dokumentinhalten zu Student Müller oder anderen externen Diensten.
