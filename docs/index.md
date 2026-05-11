# From Photos to 3D Model

**90-Minuten-Workshop: 3D Raumrekonstruktion mit Foundation Models**

Willkommen zum Workshop! Hier lernst du, wie du aus einfachen Smartphone-Fotos im Handumdrehen 3D-Modelle von Räumen erstellen kannst – ganz ohne spezielle Hardware oder teure Software.

## Was erwartet dich?

!!! tip "Ziel des Workshops"
    Am Ende dieses Workshops hast du:

    - :camera: Eine Serie von Fotos eines Raumes aufgenommen
    - :robot: Mit Foundation Models ein 3D-Modell erstellt
    - :eyeglasses: Das Ergebnis in einem 3D-Viewer betrachtet

## Übersicht der Modelle

| Modell | Stärke | Einsatzgebiet | Hardware |
|--------|--------|---------------|----------|
| **DUSt3R** | Schnell, robust | Erster Einstieg, kleine Szenen | CPU bis GPU |
| **MASt3R** | Nachfolger von DUSt3R | Bessere Rekonstruktion, größere Szenen | GPU empfohlen |
| **VGGT** | State-of-the-art | Hohe Genauigkeit, komplexe Geometrien | GPU empfohlen |
| **Depth Anything V3** | Monokulare Tiefe | Einzelbild-Tiefenschätzung | CPU bis GPU |

## Schnellstart

Wenn du schon alles installiert hast:

```bash
# Beispiel: DUSt3R Demo starten
cd dust3r
curl -L https://github.com/naver/dust3r/releases/download/beta/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth \
  -o checkpoints/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth
python3 demo.py --weights checkpoints/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth
```

Oder nutze direkt die [🤗 Hugging Face Spaces](https://huggingface.co/croco): Alle Modelle sind dort als Web-Demos verfügbar.

## Workshop-Struktur

```
├─ 00:00 – 00:10  Einführung & Theorie (Seite: Ablaufplan)
├─ 00:10 – 00:20  Fotoaufnahme im Gebäude (Seite: Foto-Guide)
├─ 00:20 – 00:50  Hands-on: 3D-Rekonstruktion (Seite: Modelle)
├─ 00:50 – 01:15  Ergebnisse vergleichen & diskutieren
└─ 01:15 – 01:30  Ausblick & Fragen
```

## Ressourcen

- :material-github: [GitHub Repository](https://github.com/KIMBOT26/3D-Reconstruction-Workshop)
- :material-book-open-variant: [Workshop-Ablaufplan](ablaufplan.md)
- :material-cube-outline: [Modelle-Übersicht](modelle.md)
- :material-download: [Setup & Installation](setup.md)
- :material-camera: [Foto-Guide](fototipps.md)

!!! info "Voraussetzungen"
    - Laptop mit aktuellem Browser
    - Smartphone mit Kamera
    - Optional: Python-Umgebung für lokale Nutzung