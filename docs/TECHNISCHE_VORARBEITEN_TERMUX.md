# Technische Vorarbeiten auf Android mit Termux

**Stand: 04.11.2026**

## Ziel

Die Android-Local-Agent-Entwicklung wird direkt auf einem realen Android-Gerät vorbereitet. Das Smartphone dient dabei als lokale Linux-nahe Entwicklungs- und Testumgebung. Die Arbeiten sind praktische System- und Geräteuntersuchungen; sie sind nicht mit Root-Entwicklung, Kernel-Modifikation oder direkter Treiberprogrammierung gleichzusetzen.

## Entwicklungsgerät laut Projektstand

- Xiaomi Redmi 17
- Android 16 / HyperOS 3
- 4 GB RAM
- Termux als lokale Arbeitsumgebung

Geräte- und Versionsangaben müssen bei Änderungen neu geprüft werden.

## Bereits eingerichtet bzw. erprobt

- Termux als Kommandozeilen- und Entwicklungsumgebung.
- Python als Entwicklungsgrundlage.
- Wireless Debugging.
- Shizuku gekoppelt und gestartet.
- `rish` für Shell-Zugriffe im Rahmen der Shizuku-Umgebung.
- Untersuchung von Android-Systempfaden und Konfigurationsdateien.
- Analyse installierter und vorinstallierter Android-/Xiaomi-Pakete.
- Paketfilterungen und Untersuchung von Systemkomponenten.
- Untersuchung der Android-Berechtigungsgrenzen.

## Beispiel für eine dokumentierte Systemuntersuchung

Es wurde unter anderem eine Android-Konfigurationsdatei für Handschrift-/Eingabekomponenten ausgelesen. Das zeigt, dass Systemkonfigurationen direkt auf dem Gerät untersucht werden. Das Auslesen einer Konfigurationsdatei bedeutet nicht, dass die zugehörige Systemfunktion verändert oder implementiert wurde.

## Dokumentierte Berechtigungsgrenze

Ein Aufruf von `settings --user 0` führte zu einer `SecurityException`. Die Fehlermeldung nannte fehlende Berechtigungen wie `MANAGE_USERS`, `CREATE_USERS` oder `QUERY_USERS`. Android beschränkt bestimmte Benutzerverwaltungsoperationen auch innerhalb einer über Shizuku gestarteten Shell.

## Arbeitsweise

Für jeden neuen technischen Schritt werden festgehalten:

1. Ziel und Hypothese.
2. Exakter Befehl oder Skript.
3. Geräte-/Android-/Termux-Version.
4. Ausgabe und Exit-Code.
5. Erwartetes und tatsächliches Ergebnis.
6. Berechtigungs- und Sicherheitsfolgen.
7. Status: erfolgreich, fehlgeschlagen, teilweise erfolgreich oder noch offen.

Keine Zugangsdaten, Tokens, privaten Schlüssel oder personenbezogenen Dokumente in Terminalprotokolle oder GitHub übernehmen.

## Nächste Schritte

- Ein reproduzierbares Protokollverzeichnis für Tests anlegen.
- Paketversionen und Termux-Quellen erfassen.
- OCR-Installation und -Tests getrennt protokollieren.
- Berechtigungsgrenzen dokumentieren, ohne unnötig privilegierte Zugriffe anzustreben.
