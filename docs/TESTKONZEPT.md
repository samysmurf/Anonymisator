# Testkonzept – Anonymisator

**Ziel:** Reproduzierbare Tests für lokale Textextraktion, OCR, Datenerkennung, dauerhafte Schwärzung, Metadatenbereinigung, Export und Barrierefreiheit. Bis zur Implementierung gelten alle Punkte als Testanforderungen, nicht als bereits bestandene Prüfungen.

## 1. Testdaten und Testumgebung

- Ausschließlich synthetische oder wirksam anonymisierte Dokumente verwenden.
- Für jeden Test Solltext, erwartete Treffer, Dateityp, Seitenzahl und Testdatum dokumentieren.
- Android-Version, Gerätemodell, Termux- und Paketversionen sowie verfügbare Ressourcen festhalten.
- Testdaten dürfen keine realen Personen oder vertraulichen Verwaltungsunterlagen abbilden.

## 2. Text- und OCR-Tests

- Textbasierte PDFs und gescannte Bildseiten getrennt prüfen.
- Deutsche Umlaute, Zahlen, Datumsangaben, Aktenzeichen-ähnliche Muster und mehrzeilige Anschriften testen.
- Tabellen, Spalten, Kopf-/Fußzeilen, gedrehte Seiten, geringe Auflösung und schlechte Kontraste berücksichtigen.
- Soll-/Ist-Text vergleichen und Zeichen- bzw. Wortfehlerrate dokumentieren.
- Laufzeit, Speicherbedarf, Abbrüche und Fehlermeldungen festhalten.
- OCR-Qualität darf nicht allein anhand eines erfolgreichen Einzelbilds bewertet werden.

## 3. Sensitiv-Datenerkennung

- Treffer und Nichttreffer mit einem festgelegten Sollsatz vergleichen.
- Falsch-positive und falsch-negative Ergebnisse getrennt dokumentieren.
- Namen, Anschriften, Geburtsdaten, Kontaktdaten, Identifikationsnummern und frei formulierte sensible Angaben in synthetischen Fällen testen.
- Prüfen, ob jede Markierung manuell korrigierbar ist.
- Keine automatische Freigabe eines Dokuments allein aufgrund der Erkennungsrate.

## 4. Dauerhafte Schwärzung

Vor Freigabe müssen mindestens folgende Negativtests bestanden sein:

- geschwärzten Text per Suche nicht finden,
- Text nicht per Markieren und Copy/Paste wiederherstellen,
- keine ursprünglichen Textfragmente im Textlayer,
- Bildinhalt nicht durch Entfernen einer Overlay-Ebene wiederherstellbar,
- keine rekonstruierbaren Inhalte durch erneute OCR,
- keine ungeschwärzten Inhalte in Anhängen, Formularfeldern oder eingebetteten Objekten,
- keine vertraulichen Informationen in Metadaten.

Ein Testfehler blockiert den Release der Schwärzungsfunktion.

## 5. Original, Export und Datenfluss

- Prüfsumme des Originals vor und nach Verarbeitung vergleichen.
- Sicherstellen, dass das Original unverändert bleibt.
- Exportkopie in einem getrennten Speicherziel erzeugen.
- Temporäre Dateien und Fehlerabbrüche testen.
- Netzwerkverkehr während lokaler Verarbeitung kontrollieren; vor einer ausdrücklich vorgesehenen externen Nutzerhandlung darf keine Übertragung von Dokumentinhalten stattfinden.
- Nutzer muss erkennen, welche Datei exportiert wird und welche Inhalte entfernt wurden.

## 6. Barrierefreiheit und Bedienbarkeit

- TalkBack-Beschriftungen und Fokusreihenfolge prüfen.
- Schriftvergrößerung, Kontrast und Quer-/Hochformat testen.
- Bedienung ohne ausschließlich gestenbasierte Aktionen sicherstellen.
- OCR-Markierungen zusätzlich textuell ausgeben.
- Fehlermeldungen und Statusänderungen müssen verständlich und assistiv erfassbar sein.

## 7. Release-Gates

Ein Release mit Dokumentenexport ist erst zulässig, wenn die Tests für Originalintegrität, dauerhafte Schwärzung, Metadaten, eingebettete Inhalte, Netzwerkverhalten und Nutzerprüfung reproduzierbar bestanden und dokumentiert sind. Ein einzelner erfolgreicher OCR-Test genügt nicht für die Freigabe der gesamten Pipeline.
