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
