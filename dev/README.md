# Präsentation: 3D-Rekonstruktion – Kurze Theorie

## Dateien

| Datei | Format | Beschreibung |
|-------|--------|-------------|
| `theorie-folien.md` | Marpit Markdown | Quelldatei – bearbeitbar |
| `theorie-folien.html` | HTML (Marpit Rendered) | Präsentation im Browser |

## Nutzung

### 1. Im Browser öffnen (empfohlen)

```bash
# Lokal öffnen
open theorie-folien.html        # macOS
xdg-open theorie-folien.html    # Linux
start theorie-folien.html        # Windows
```

Oder einfach die HTML-Datei per Doppelklick öffnen. Die Präsentation läuft im Browser mit Pfeiltasten (← →) oder Mausklick.

### 2. Vor dem Workshop anpassen

Die `theorie-folien.md` kann beliebig editiert werden. Dann neu rendern:

```bash
# HTML neu generieren
marp theorie-folien.md --html -o theorie-folien.html

# Optional: PDF (benötigt Chromium/Chrome)
# Falls Chrome installiert:
marp theorie-folien.md --pdf -o theorie-folien.pdf

# Oder mit global installiertem Chrome:
marp theorie-folien.md --pdf --chrome-path /usr/bin/google-chrome -o theorie-folien.pdf
```

## Inhalt der Folien

- Titelfolie: „Foundation Models für 3D-Rekonstruktion"
- Was bedeutet 3D-Rekonstruktion?
- Anwendungen heute
- Traditioneller Workflow
- Probleme des traditionellen Ansatzes
- Foundation Models als Game Changer
- Grundidee: Funktionsweise
- Vier Modelle: DUSt3R, MASt3R, VGGT, Depth Anything V3
- Vergleichstabelle
- Zwei Wege zur Nutzung (Hugging Face / Lokal)
- Workshop-Ablauf
- Foto-Aufnahme: Goldene Regeln
- Hardware-Empfehlungen
- Ausblick
- Abschlussfolie

## Notizen

- Seitenverhältnis: 16:9
- Dark Theme (invertiert)
- Autopaginierung eingeschaltet
- Emoji-Support