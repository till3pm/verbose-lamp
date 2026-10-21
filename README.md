# MC Server – Minecraft-Server auf dem Handy

Android-App (Java), die lokal einen Minecraft-Java-Server startet. Beim ersten Start führt ein
Setup durch Software (Vanilla / Paper), Version, Spiel-Einstellungen, RAM und Port.
Design: schwarzer Hintergrund, Terminal-Konsole als Gestaltungselement.

## APK bauen
1. Inhalt des ZIP in ein GitHub-Repo entpacken und pushen.
2. Tab **Actions → Build APK → Run workflow** (nur manueller Start).
3. Fertige APK im Lauf unter **Artifacts → MC-Server-apk**.

## Java-Laufzeit
Android bringt keine Java-VM für Server-JARs mit. Die App braucht eine **Android-kompatible (bionic) JRE für aarch64**
als `.tar.xz` / `.tar.gz` mit `bin/java`. Im Setup (Schritt „Installation“) entweder die Download-URL einfügen
oder die heruntergeladene Datei über „Datei wählen“ auswählen. Die App prüft sie mit `java -version`.
Für Minecraft ab 1.20.5 wird Java 21 benötigt, ab 1.17 Java 17.

## Schriftart
Die Claude-Schrift ist proprietär und deshalb nicht enthalten. Standard ist die System-Serifenschrift.
Eigene Schrift: Datei als `app/src/main/res/font/claude_font.ttf` ablegen – sie wird automatisch verwendet.

## Hinweise
- `targetSdk` ist bewusst 28, weil Android ab 29 das Ausführen von Programmen aus dem App-Speicher blockiert.
- Server-Daten liegen im App-Speicher (`files/server`).
- Server läuft als Vordergrunddienst; Akku-Optimierung für die App ausschalten.
