# Waffenbestandsbuch mit Erwerbsrechner (Testversion)

Idee und Konzeption: Jens Rödel. © 2026 Jens Rödel. Alle Rechte vorbehalten.

Offlinefähige Browser-App mit WBK-Verwaltung, NWR-Feldern, Erwerbsrechner und PDF-Druckansicht. Die verschlüsselte Datenbank kann als JSON-Datei gesichert und über OneDrive manuell zwischen Geräten übertragen werden. Keine direkte OneDrive-API-Anbindung.

## GitHub Pages

1. Neues Repository `waffenbestandsbuch` erstellen.
2. Diese Dateien in das Stammverzeichnis hochladen, **keine persönlichen Datenbankdateien**.
3. Unter Settings → Pages → Build and deployment `Deploy from a branch`, Branch `main`, Ordner `/ (root)` auswählen.
4. Die bereitgestellte HTTPS-Adresse im iPad-Safari öffnen. Über Teilen → Zum Home-Bildschirm hinzufügen.

## Sicherheit und Einschränkungen

- AES-256-GCM mit PBKDF2 (600.000 Iterationen) und lokaler IndexedDB. Passwortverlust bedeutet Datenverlust.
- GitHub Pages veröffentlicht Programmcode, nicht die lokalen Daten. Die App muss vor dem Einsatz mit echten Daten auf allen Geräten getestet werden.
- Die verschlüsselte Datei wird über den Dateidialog geöffnet, Änderungen müssen danach erneut nach OneDrive exportiert werden.
- PDF-Druckausgaben sind **unverschlüsselt**.
- Vor dem Anlegen einer neuen Datenbank stets eine verschlüsselte Sicherung in OneDrive ablegen.
- Rechtliche Berechnung ist eine unverbindliche Orientierung; Ausnahmen und Grenztage sind nicht abschließend geprüft.
- Kein automatisches Update des Datenbankschemas garantiert. Vor Updates eine Sicherung anlegen.
- Kein produktiver Sicherheitstest oder unabhängiges Audit erfolgt.


## Version 1.1

Seitenmenü für Übersicht, Waffenbestand, Erfassung, WBK-Verwaltung, Erwerbsrechner und Datenbank.
Munitionserwerb wird je Waffe mit Ja, Nein oder Unbekannt erfasst. Vorhandene verschlüsselte
Datenbanken im Format `erwerbsrechner-v2` bleiben kompatibel.
Nach dem GitHub-Upload kann der Service Worker eine ältere Version im Cache halten.
Gegebenenfalls die App vollständig schließen und neu öffnen.

## Version 1.2
Das Dashboard zeigt das automatisch berechnete nächste Erwerbsdatum, Bestandszahlen und relevante Erwerbe. Keine Datumsauswahl.

Version 1.4: Auswahl zwischen bestehender Datenbank und Neuanlage vor der Passworteingabe.


Version V1.61: Fehlendes Filterfeld im Waffenbestand ergänzt und Versionsanzeige auf zweistellige Nachkommastellen umgestellt.


## Version 1.62
Bestehende Waffen im Waffenbestand über „Bearbeiten“ ändern. Verleihstatus, Entleiher, Verleihdatum und Rückgabedatum werden verschlüsselt gespeichert und im Druckbericht aufgeführt.


## Version 1.63
- iPad-Formular mit responsiven Eingabefeldern.
- Verleih als Checkbox; bei Deaktivierung werden Datum und Leihnehmer im Formular geleert und beim Speichern aus dem Waffeneintrag entfernt.
- Personenverwaltung für Verleiher und Leihnehmer; Angaben sind Bestandteil der verschlüsselten Datenbank.
- Druckbarer Leihschein nach der vom Nutzer bereitgestellten Vorlage. Vor dem Drucken Verleih speichern. Ausdrucke sind unverschlüsselt.

## V1.64
Beim Speichern einer bestehenden Waffe bleibt die Bearbeitungsmaske mit den aktuellen Werten geöffnet. Neue Waffen werden nach dem Speichern weiterhin zurückgesetzt.


V1.65: Menüeinträge Datenbank speichern und Abmelden. Wenn der letzte Export länger als 20 Sekunden zurückliegt oder Daten geändert wurden, startet Abmelden zunächst den Download und fragt nach erfolgreichem Ablegen. Der Browser kann das tatsächliche Ablegen in Dateien/OneDrive nicht technisch überprüfen.

## Version 1.66
- Statusmeldungen verschwinden automatisch nach 10 Sekunden.
- Der Leihschein-Druckknopf wird nach dem Speichern gültiger Verleihangaben blau und aktiv; bei nicht gespeicherten Verleihänderungen wieder grau und deaktiviert.
- Klarere Bezeichnung der Online-Web-App mit lokal verschlüsselter Datenbank.

## V1.68 Fehlerprotokoll
Fehlermeldungen bleiben sichtbar und werden mit ISO-Zeitstempel im lokalen IndexedDB-Speicher protokolliert (maximal 500 Einträge). Über die Datenbankseite lässt sich das Protokoll als JSON-Datei herunterladen. Statusmeldungen verschwinden nach 10 Sekunden. Das Fehlerprotokoll wird nicht automatisch synchronisiert oder mit der verschlüsselten Datenbank exportiert. Es liegt lokal unverschlüsselt vor; Fehlermeldungen dürfen deshalb keine Geheimnisse enthalten.


## V1.69 Leihpersonen und WBK-Zuordnung
Leihnehmer können den WBK-Typ grün/gelb erfassen. Für den Verleiher werden keine separaten WBK-Personendatensätze benötigt: Der Leihschein übernimmt die der Waffe zugeordnete WBK aus der WBK-Verwaltung. Persönliche Anschrift des Verleihers wird weiterhin im Standardverleiher-Profil verwaltet. Bereits angelegte doppelte Verleiher können nach Prüfung gelöscht werden.
