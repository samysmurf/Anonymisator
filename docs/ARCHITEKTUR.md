# Architektur

Anonymisator ist ein eigenständiges Android-Projekt ohne direkte KI-Schnittstelle. Zielpipeline: lokaler Import → Text-PDF-Extraktion oder lokale OCR → Erkennung sensibler Angaben → Vorschau/manuelle Korrektur → dauerhafte Schwärzung einer separaten Kopie → Metadaten- und Textlayer-Prüfung → lokaler Export.

Originale bleiben unverändert. Eine schwarze Überlagerung reicht nicht als Schwärzung. Die native App und vollständige Pipeline sind noch nicht implementiert.
