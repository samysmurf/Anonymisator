# Barrierefreiheit – @Vision

**Ziel:** Eine spätere native Android-App soll mit TalkBack und unterschiedlichen Bedienformen nutzbar sein. Dieses Dokument beschreibt Anforderungen; es bestätigt keine bestehende App oder Konformität.

## Bedienung und Orientierung

- Semantische Beschriftungen und aussagekräftige Namen für Schaltflächen, Felder und Statusmeldungen.
- Logische Fokusreihenfolge; Fokus darf nicht unerwartet springen.
- Alle Kernfunktionen ohne alleinige Gestensteuerung erreichbar.
- Skalierbare Schrift, ausreichender Kontrast und nutzbare Darstellung bei vergrößerter Anzeige.
- Touch-Ziele und Abstände so gestalten, dass sie zuverlässig bedienbar sind.
- Fehler, Wartezeiten und Verarbeitungsschritte verständlich mitteilen.

## Dokumentenprüfung

- Jede erkannte sensible Angabe muss nicht nur farblich, sondern auch textuell und durch Screenreader identifizierbar sein.
- Markierungen müssen sich eindeutig auf Seite, Position und Text beziehen.
- Korrekturen müssen per zugänglichen Bedienelementen möglich sein.
- Nutzer müssen die gesamte Datei seitenweise überprüfen können.
- Status „nicht geprüft“, „geprüft“ und „Export blockiert“ darf nicht ausschließlich farblich vermittelt werden.

## Tests

Vor einer Konformitätsaussage sind Tests auf realen Geräten mit TalkBack, Textvergrößerung, unterschiedlichen Schriftgrößen, Kontrast-Einstellungen sowie Hoch- und Querformat erforderlich. Die Tests müssen dokumentiert und bei wesentlichen UI-Änderungen wiederholt werden.

Die Leitlinie orientiert sich an WCAG 2.2 und den Android Accessibility-Prinzipien. Eine Orientierung an Standards ist kein Nachweis, dass die App diese Standards erfüllt.
