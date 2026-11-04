# Datenschutz und Sicherheit – Anonymisator

**Leitprinzip: lokale Verarbeitung, Datenminimierung und vollständige Nutzerkontrolle.**

Anonymisator soll Dokumente auf dem Android-Gerät verarbeiten. Das ist ein Entwicklungsziel, kein Nachweis einer bereits funktionsfähigen oder geprüften App. Die native App und die vollständige lokale Pipeline sind derzeit noch nicht implementiert.

## Verbindliche Architekturziele

- Keine direkte KI-Schnittstelle.
- Keine automatische Übertragung von Dokumentinhalten an Student Müller oder andere externe Dienste.
- Verarbeitung möglichst vollständig lokal.
- Keine Überschreibung des Originals.
- Vorschau und manuelle Prüfung vor jeder Ausgabe.
- Eine spätere externe Nutzung darf nur durch eine eigenständige, bewusste Nutzerhandlung erfolgen; eine automatische Übermittlung ist nicht vorgesehen.

## Datenlebenszyklus

Importierte Dokumente sollen nur so lange und in dem Umfang gespeichert werden, wie es für den konkreten Verarbeitungsschritt erforderlich ist. Temporäre Bilder, OCR-Texte, Vorschaudaten und Exportdateien benötigen ein nachvollziehbares Speicher- und Löschkonzept. Zugriffsrechte und Speicherorte sind zu dokumentieren.

## Echte Schwärzung

Eine schwarze Fläche über Text reicht nicht aus. Die Exportkopie muss den ursprünglichen Text oder Bildinhalt tatsächlich entfernen. Zusätzlich sind Textlayer, Copy/Paste, Suchfunktionen, OCR, Metadaten, Anhänge und eingebettete Objekte zu prüfen. Das Ergebnis darf nicht als vollständig anonym bezeichnet werden, solange rekonstruierbare Informationen gefunden werden können.

## Umgang mit Testdaten

- In GitHub ausschließlich synthetische oder wirksam anonymisierte Dateien verwenden.
- Keine echten Bescheide, Gesundheitsdaten, Personalausweise, Aktenzeichen, Anschriften oder Kontodaten in Issues, Commits, Testsets oder Logs übernehmen.
- Testfälle müssen so konstruiert sein, dass Solltext und erwartete Treffer ohne Rückgriff auf echte Personen feststehen.
- OCR-Ergebnisse sind fehleranfällig und müssen manuell geprüft werden.

## Statusgrenze

Bis die vollständige Verarbeitung implementiert und unabhängig getestet ist, darf Anonymisator nicht als sicheres Schwärzungs- oder Anonymisierungswerkzeug für vertrauliche Originalunterlagen beworben oder verwendet werden. Dokumentierte Anforderungen sind kein technischer Sicherheitsnachweis.
