# 🏠 From Photos to 3D Model

**90-Minuten-Workshop: 3D Raumrekonstruktion mit Foundation Models**

Dieses Repository enthält die vollständige Dokumentation für einen interaktiven Workshop, in dem Studierende aus Smartphone-Fotos mithilfe moderner Foundation Models 3D-Modelle von Räumen erstellen.

## 📖 Dokumentation

Die Dokumentation ist auf GitHub Pages verfügbar:

➡️ **https://KIMBOT26.github.io/3D-Reconstruction-Workshop/**

## 🚀 Workshop-Ziele

- 10 Min Theorie: Wie funktioniert 3D-Rekonstruktion mit Foundation Models?
- 10 Min Praxis: Fotos im Gebäude aufnehmen
- 30 Min Hands-on: 3D-Modell aus eigenen Fotos erzeugen
- 25 Min Vergleich & Diskussion der Ergebnisse
- 15 Min Ausblick & Fragen

## 🤖 Behandelte Modelle

| Modell | Einsatzgebiet | Hardware |
|--------|-------------|----------|
| **DUSt3R** | Einstieg, schnelle Ergebnisse | CPU/GPU |
| **MASt3R** | Bessere Qualität, größere Szenen | GPU empfohlen |
| **VGGT** | State-of-the-art Genauigkeit | GPU (24 GB) |
| **Depth Anything V3** | Einzelbild-Tiefe, Echtzeit | CPU/GPU |

## 📁 Repository-Struktur

```
3D-Reconstruction-Workshop/
├── docs/                    # MkDocs Quelldateien
│   ├── index.md            # Startseite
│   ├── ablaufplan.md       # 90-Minuten Ablaufplan
│   ├── modelle.md          # Modelle-Übersicht
│   ├── setup.md           # Installationsanleitungen
│   └── fototipps.md       # Foto-Guide für Teilnehmende
├── mkdocs.yml              # MkDocs Konfiguration
└── README.md               # Diese Datei
```

## 🛠️ Lokale Entwicklung

```bash
# Repository klonen
git clone https://github.com/KIMBOT26/3D-Reconstruction-Workshop.git
cd 3D-Reconstruction-Workshop

# Python-Umgebung erstellen (optional)
python3 -m venv venv
source venv/bin/activate

# MkDocs Material installieren
pip install mkdocs-material

# Lokaler Server
mkdocs serve

# Deployment auf GitHub Pages
mkdocs gh-deploy
```

## 📋 Lizenz

Die Workshop-Dokumentation steht unter [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## 👤 Autor

**Ein Bot von Uwe Hahne** – Professor für Computer Vision / Deep Learning und AI in Media Applications
