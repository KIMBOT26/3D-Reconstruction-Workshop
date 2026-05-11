# Modelle-Übersicht

Hier findest du eine strukturierte Übersicht aller im Workshop behandelten Foundation Models – mit Stärken, Schwächen, Hardware-Anforderungen und konkreten Startbefehlen.

---

## DUSt3R

| Attribut | Details |
|---------|---------|
| **Herausgeber** | NAVER LABS Europe (Jingwen Wang et al., 2024) |
| **Paper** | [DUSt3R: Geometric 3D Vision Made Easy](https://arxiv.org/abs/2312.14132) |
| **Code** | https://github.com/naver/dust3r |
| **HF Space** | https://huggingface.co/spaces/croco/DUSt3R |
| **Ausgabe** | Punktwolke, Kameraposen, Tiefenkarte |
| **Eingabe** | 2+ beliebige, unkalibrierte Bilder |
| **Lizenz** | CC BY-NC-SA 4.0 (non-commercial) |

### Beschreibung

DUSt3R ist das Einstiegsmodell für diesen Workshop. Es nimmt zwei beliebige Bilder, berechnet deren relative Kameraposen und erzeugt eine gemeinsame Punktwolke – ganz ohne vorherige Kalibrierung.

### Stärken

- :white_check_mark: Keine Kamerakalibrierung nötig
- :white_check_mark: Funktioniert mit beliebigen, ungeordneten Bildern
- :white_check_mark: Gute Ergebnisse bei strukturierten Innenräumen
- :white_check_mark: Große Community, viele Tutorials

### Schwächen

- :x: Non-commercial Lizenz (nur für Lehre/Forschung)
- :x: Bei sehr großen Szenen kann der Speicher knapp werden
- :x: Keine Texturierung im Original

### Schnellstart (Lokal)

```bash
# Repository klonen
git clone https://github.com/naver/dust3r.git
cd dust3r

# Hugging Face Hub für Download installieren
pip install huggingface-hub

# Checkpoint herunterladen (ViT-Large, 512px)
mkdir -p checkpoints
huggingface-cli download naver/DUSt3R \
  DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth \
  --local-dir checkpoints

# Demo starten
python3 demo.py \
  --weights checkpoints/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth \
  --device cuda  # oder cpu
```

### Schnellstart (Hugging Face)

```bash
# Keine Installation nötig – nur Browser:
# 1. https://huggingface.co/spaces/croco/DUSt3R öffnen
# 2. Bilder hochladen
# 3. „Run Inference“ klicken
```

---

## MASt3R (Master)

| Attribut | Details |
|---------|---------|
| **Herausgeber** | NAVER LABS Europe (same team) |
| **Paper** | [MASt3R: Matching And Stereo 3D Reconstruction](https://arxiv.org/abs/2406.09756) |
| **Code** | https://github.com/naver/mast3r |
| **HF Space** | https://huggingface.co/spaces/croco/MASt3R |
| **Ausgabe** | Punktwolke, Kameraposen, Tiefenkarte, Schnelle Rekonstruktion |
| **Eingabe** | 2+ beliebige, unkalibrierte Bilder |
| **Lizenz** | CC BY-NC-SA 4.0 (non-commercial) |

### Beschreibung

MASt3R ist der direkte Nachfolger von DUSt3R. Es nutzt ein verbessertes Matching-Verfahren, ist deutlich schneller und liefert konsistentere Ergebnisse – besonders bei großen Bildsammlungen.

### Stärken

- :white_check_mark: ~5× schneller als DUSt3R
- :white_check_mark: Deutlich besseres Feature-Matching
- :white_check_mark: Bessere Skalierung auf große Szenen
- :white_check_mark: Verbesserte Punktwolken-Dichte

### Schwächen

- :x: Non-commercial Lizenz
- :x: Höhere VRAM-Anforderungen (12 GB empfohlen)
- :x: Neue Architektur, weniger Zusatztools als DUSt3R

### Schnellstart (Lokal)

```bash
git clone https://github.com/naver/mast3r.git
cd mast3r

pip install -r requirements.txt
huggingface-cli download naver/MASt3R \
  MASt3R_ViTLarge_BaseDecoder_512_catmlp.pth \
  --local-dir checkpoints

python3 demo.py \
  --weights checkpoints/MASt3R_ViTLarge_BaseDecoder_512_catmlp.pth \
  --device cuda
```

---

## VGGT

| Attribut | Details |
|---------|---------|
| **Herausgeber** | Visual Geometry Group (VGG), Oxford / Meta AI |
| **Paper** | [VGGT: Visual Geometry Grounded Transformer](https://arxiv.org/abs/2503.01151) |
| **Code** | https://github.com/facebookresearch/vggt |
| **HF Space** | https://huggingface.co/spaces/facebook/vggt |
| **Ausgabe** | Punktwolke, Kameraposen, Tiefenkarte, Tracks |
| **Eingabe** | Mehrere Bilder (idealerweise > 5) |
| **Lizenz** | Apache 2.0 |

### Beschreibung

VGGT ist eines der aktuellsten und leistungsfähigsten Modelle für geometrisches 3D Vision. Es kombiniert einen Transformer mit geometrischen Zielsetzungen und erreicht State-of-the-Art Ergebnisse auf vielen Benchmarks.

### Stärken

- :white_check_mark: Apache 2.0 Lizenz (vollständig Open Source, kommerziell nutzbar)
- :white_check_mark: State-of-the-Art Genauigkeit
- :white_check_mark: Hervorragendes Feature-Matching über viele Bilder
- :white_check_mark: Gut für große, komplexe Szenen

### Schwächen

- :x: Sehr hoher VRAM-Verbrauch (24 GB empfohlen)
- :x: Installation aufwendiger als DUSt3R/MASt3R
- :x: Relativ neues Modell, weniger Community-Ressourcen

### Schnellstart (Lokal)

```bash
git clone https://github.com/facebookresearch/vggt.git
cd vggt
pip install -r requirements.txt

# Modell wird automatisch beim ersten Start heruntergeladen
python3 demo.py --input images/ --output output/
```

!!! tip "Hinweis zu VGGT"
    VGGT benötigt deutlich mehr Rechenleistung. Für den Workshop ist die 
    Hugging Face Space-Version oder die VM stark empfohlen.

---

## Depth Anything V3

| Attribut | Details |
|---------|---------|
| **Herausgeber** | HKU & TikTok / ByteDance |
| **Paper** | [Depth Anything V3](https://arxiv.org/abs/2501.06878) |
| **Code** | https://github.com/DepthAnything/Depth-Anything-V3 |
| **HF Space** | https://huggingface.co/spaces/depthanything/Depth-Anything-V3 |
| **Ausgabe** | Tiefenkarte (pro Bild) |
| **Eingabe** | Einzelbild oder Video |
| **Lizenz** | Apache 2.0 |

### Beschreibung

Depth Anything V3 spezialisiert sich auf **monokulare Tiefenschätzung** aus einem einzigen Bild oder Video. Im Gegensatz zu den anderen Modellen liefert es keine vollständige 3D-Punktwolke, sondern eine Tiefenkarte – perfekt für AR-Anwendungen, Fokus-Effekte oder als Vorbereitung für weitere Prozesse.

### Stärken

- :white_check_mark: Funktioniert mit einem einzigen Bild
- :white_check_mark: Echtzeit-fähig auf moderner Hardware
- :white_check_mark: Video-Tiefenschätzung möglich
- :white_check_mark: Sehr einfache Bedienung

### Schwächen

- :x: Keine absolute Skalierung (relative Tiefe)
- :x: Keine vollständige 3D-Rekonstruktion (nur Tiefenkarte)
- :x: Keine Kameraposen
- :x: Für Voll-3D muss man es mit SfM kombinieren

### Schnellstart (Lokal)

```bash
git clone https://github.com/DepthAnything/Depth-Anything-V3.git
cd Depth-Anything-V3
pip install -r requirements.txt

# Einzelbild
python3 run.py --encoder vitl --img-path image.jpg --outdir output/

# Video
python3 run_video.py --encoder vitl --video-path video.mp4 --outdir output/
```

---

## Vergleichsübersicht

| Kriterium | DUSt3R | MASt3R | VGGT | Depth Anything V3 |
|-----------|--------|--------|------|-------------------|
| **Eingabe** | 2+ Bilder | 2+ Bilder | 2+ Bilder | 1 Bild / Video |
| **Ausgabe** | Punktwolke + Posen | Punktwolke + Posen | Punktwolke + Posen | Tiefenkarte |
| **Min. VRAM** | 6 GB | 12 GB | 24 GB | 4 GB |
| **CPU-fähig** | :white_check_mark: (langsam) | :white_check_mark: (langsam) | :x: | :white_check_mark: |
| **Geschwindigkeit** | Mittel | Schnell | Langsam | Sehr schnell |
| **Genauigkeit** | Gut | Sehr gut | Ausgezeichnet | Gut |
| **Lizenz** | CC BY-NC-SA | CC BY-NC-SA | Apache 2.0 | Apache 2.0 |
| **Kommerziell** | :x: | :x: | :white_check_mark: | :white_check_mark: |
| **Empfohlen für...** | Einstieg, Lehrzwecke | Bessere Qualität, mittlere Szenen | Beste Qualität, große Szenen | AR, Echtzeit, Video |

---

## Weiterführende Links

- :material-file-document: [DUSt3R Paper](https://arxiv.org/abs/2312.14132)
- :material-file-document: [MASt3R Paper](https://arxiv.org/abs/2406.09756)
- :material-file-document: [VGGT Paper](https://arxiv.org/abs/2503.01151)
- :material-file-document: [Depth Anything V3 Paper](https://arxiv.org/abs/2501.06878)
- :material-github: [DUSt3R GitHub](https://github.com/naver/dust3r)
- :material-github: [MASt3R GitHub](https://github.com/naver/mast3r)
- :material-github: [VGGT GitHub](https://github.com/facebookresearch/vggt)
- :material-github: [Depth Anything V3 GitHub](https://github.com/DepthAnything/Depth-Anything-V3)
- :material-microsoft-azure: Awesome-3D-Reconstruction: https://github.com/open-mmlab/awesome-3d-reconstruction