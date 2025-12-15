# Benötigte Tools

- Raspberry Pi Pico Visual Studio Code extension (Download: [hier](https://marketplace.visualstudio.com/items?itemName=raspberry-pi.raspberry-pi-pico))
- VS-Code-Profil (Download: [hier](https://github.com/raspberrypi/pico-vscode/blob/HEAD/scripts/Pico.code-profile))

## VS-Code-Profile

Wenn Sie mit mehreren Mikrocontroller-Toolchains arbeiten, sollten Sie in Erwägung ziehen, diese Erweiterung in ein VS-Code-Profil zu installieren, um Konflikte mit anderen Toolchains zu vermeiden. Folgen Sie diesen Schritten:

- Laden Sie das Musterprofil `Pico.code-profile` herunter von [hier](https://github.com/raspberrypi/pico-vscode/blob/HEAD/scripts/Pico.code-profile)
- Öffnen Sie die Profilverwaltung unter Menüpunkt: "Datei/Einstellungen/Profile"
- Bei der Schaltfläche "Neues Profil" auf den Punkt "Weitere Aktionen" und "Profil importieren" klicken und das herunter geladene Musterprofil auswählen
- Mit Klick auf "Erstellen" die Erstellung des Profils abschließen

Auf diese Weise lässt sich die Pico-Erweiterung von anderen Erweiterungen isolieren, was das Risiko von Konflikten verringert.

Die Erweiterung lädt nun das SDK und die Toolchain herunter, installiert sie lokal und erstellt das neue Projekt. 
Das erste Projekt kann 5-10 Minuten für die Installation der Toolchain benötigen. VS Code wird Sie fragen, ob Sie den Autoren vertrauen, da automatisch das .vscode-Verzeichnis für Sie erstellt hat. Wählen Sie Ja.

PICO_SDK_PATH is C:/Users/Andreas/.pico-sdk/sdk/2.1.1

---
#raspberry #pico #vscode