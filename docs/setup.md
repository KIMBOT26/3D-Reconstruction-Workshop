# Setup & Installation

Diese Anleitung beschreibt zwei Wege zur Nutzung der Modelle im Workshop:

1. **🚀 Hugging Face Space** – Sofort starten, keine Installation
2. **💻 Lokale Installation** – Volle Kontrolle, offline-fähig

---

## Variante 1: Hugging Face Space (Empfohlen für Workshop)

!!! success "Schnellste Option"
    Keine Installation nötig. Internetzugang und ein moderner Browser genügen.

### Schritte

1. **Browser öffnen** und zu einem der folgenden Spaces navigieren:

    | Modell | URL |
    |--------|-----|
    | DUSt3R | https://huggingface.co/spaces/croco/DUSt3R |
    | MASt3R | https://huggingface.co/spaces/croco/MASt3R |
    | VGGT   | https://huggingface.co/spaces/facebook/vggt |
    | Depth Anything V3 | https://huggingface.co/spaces/depthanything/Depth-Anything-V3 |

2. **Bilder hochladen**

    - Auf „Click to Upload" oder „Drag & Drop" klicken
    - 5–20 Bilder auswählen (achte auf Überlappung, siehe [Foto-Guide](fototipps.md))

3. **Inferenz starten**

    - „Run Inference" klicken
    - Wartezeit: 30 Sekunden bis 5 Minuten (je nach Modell und Bildanzahl)

4. **Ergebnis herunterladen**

    - Punktwolke als `.glb` oder `.ply`
    - Im 3D-Viewer betrachten oder in Blender importieren

!!! warning "Einschränkungen"
    - Dateigröße pro Bild: meist max. 10–20 MB
    - Maximale Bildanzahl: je nach Space 5–50 Bilder
    - Queue-Zeiten bei hoher Auslastung möglich
    - Läuft auf Hugging Face Servern – keine Daten verlassen den eigenen Rechner, aber Bilder werden temporär auf HF verarbeitet

---

## Variante 2: Lokale Installation

### Voraussetzungen

- Python 3.9–3.11 (nicht 3.12+ wegen torch-Kompatibilität)
- Git
- CUDA-fähige NVIDIA-GPU (empfohlen, für CPU-only siehe Hinweise unten)
- Mindestens 8 GB RAM, besser 16 GB+
- ~10 GB freier Speicherplatz

### Allgemeine Setup-Schritte

```bash
# Schritt 1: Python-Umgebung erstellen (empfohlen)
python3 -m venv ~/3d-workshop-env
source ~/3d-workshop-env/bin/activate

# Schritt 2: Grundpakete installieren
pip install --upgrade pip wheel setuptools

# Schritt 3: PyTorch mit CUDA installieren
# Für CUDA 12.1:
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

# Für CPU-only (langsam, aber funktioniert):
# pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

### DUSt3R – Lokale Installation

```bash
cd ~/workspace  # oder gewünschtes Arbeitsverzeichnis

git clone https://github.com/naver/dust3r.git
cd dust3r

# Abhängigkeiten installieren
pip install -r requirements.txt
pip install -r requirements_optional.txt  # für GUI-Visualisierung

# Modell-Checkpoint herunterladen
mkdir -p checkpoints
huggingface-cli download naver/DUSt3R \
  DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth \
  --local-dir checkpoints

# Demo starten (GPU)
python3 demo.py \
  --weights checkpoints/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth

# Oder CPU-Modus
python3 demo.py \
  --weights checkpoints/DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth \
  --device cpu
```

### MASt3R – Lokale Installation

```bash
cd ~/workspace

git clone https://github.com/naver/mast3r.git
cd mast3r

pip install -r requirements.txt

# Checkpoint laden
huggingface-cli download naver/MASt3R \
  MASt3R_ViTLarge_BaseDecoder_512_catmlp.pth \
  --local-dir checkpoints

# Demo starten
python3 demo.py \
  --weights checkpoints/MASt3R_ViTLarge_BaseDecoder_512_catmlp.pth \
  --device cuda
```

### VGGT – Lokale Installation

```bash
cd ~/workspace

git clone https://github.com/facebookresearch/vggt.git
cd vggt

pip install -r requirements.txt

# Automatischer Download beim ersten Start
python3 demo.py --input ~/meine-bilder/ --output output/
```

!!! danger "VGGT Warnung"
    VGGT benötigt mindestens 16 GB VRAM, besser 24 GB (RTX 3090/4090).
    Auf Laptops oder mittleren GPUs ist die Hugging Face Space-Variante 
    dringend empfohlen.

### Depth Anything V3 – Lokale Installation

```bash
cd ~/workspace

git clone https://github.com/DepthAnything/Depth-Anything-V3.git
cd Depth-Anything-V3

pip install -r requirements.txt

# Einzelbild
python3 run.py --encoder vitl --img-path bild.jpg --outdir output/

# Alle Bilder in einem Ordner
python3 run.py --encoder vitl --img-path meine-bilder/ --outdir output/

# Video
python3 run_video.py --encoder vitl --video-path video.mp4 --outdir output/
```

---

## Variante 3: VM-Nutzung (falls verfügbar)

Falls im Lab oder Institut eine GPU-VM zur Verfügung steht:

### SSH-Zugriff vorbereiten

```bash
# SSH-Schlüssel generieren (falls noch nicht vorhanden)
ssh-keygen -t ed25519 -C "deine-email@hsbi.de"

# Public Key an VM-Admin senden oder kopieren
ssh-copy-id benutzer@vm-adresse
```

### Auf der VM

```bash
ssh benutzer@vm-adresse

# Git, Python, CUDA prüfen
git --version
python3 --version
nvidia-smi

# Dann Variante 2 (lokale Installation) auf der VM durchführen
# Bilder per scp oder rsync hochladen:
scp -r meine-bilder/ benutzer@vm-adresse:~/workshop/
```

### Alternativ: Jupyter auf VM

Falls JupyterHub/JupyterLab auf der VM läuft:

```bash
# Port-Forwarding für Jupyter
ssh -L 8888:localhost:8888 benutzer@vm-adresse
```

Dann im Browser `http://localhost:8888` öffnen.

---

## Troubleshooting

### Problem: `torch.cuda.is_available()` ist `False`

!!! bug "Ursachen & Lösungen"

    **Ursache 1:** PyTorch CPU-Version installiert
    ```bash
    pip uninstall torch torchvision
    pip install torch torchvision --index-url https://download.pytorch.org/whl/cu121
    ```

    **Ursache 2:** CUDA nicht installiert oder falsche Version
    ```bash
    nvidia-smi  # Zeigt CUDA-Version
    # PyTorch muss zur CUDA-Version passen
    ```

    **Ursache 3:** NVIDIA-Treiber fehlen oder sind veraltet
    ```bash
    # Linux: Neuen Treiber installieren
    sudo apt update
    sudo apt install nvidia-driver-XXX
    sudo reboot
    ```

### Problem: `Out of Memory` beim Start

!!! bug "Ursachen & Lösungen"

    - Weniger Bilder verwenden (max. 5–10 statt 20+)
    - Bilder vorher verkleinern (max. 512 px lange Kante)
    - `device cpu` verwenden (langsamer, aber mehr RAM verfügbar)
    - Für MASt3R/VGGT: kleineres Modell wählen (ViT-Base statt ViT-Large)

### Problem: `huggingface-cli` nicht gefunden

```bash
pip install huggingface-hub
huggingface-cli login  # optional, für private Repos
```

### Problem: Installation dauert zu lange im Workshop

!!! tip "Workaround"
    Sofort auf Hugging Face Space umsteigen! Das ist der Fallback für alle Fälle.

---

## Checkliste vor dem Workshop

- [ ] Python 3.9–3.11 installiert
- [ ] Git installiert
- [ ] Virtuelle Umgebung erstellt und aktiviert
- [ ] Mindestens ein Modell erfolgreich getestet
- [ ] Hugging Face Space als Fallback probiert
- [ ] Bilder für Testlauf bereit

---

## Nützliche Tools

### 3D-Viewer für Ergebnisse

| Tool | Plattform | Nutzung |
|------|-----------|---------|
| [MeshLab](https://www.meshlab.net/) | Win/Mac/Linux | Punktwolken (.ply) öffnen und bearbeiten |
| [Blender](https://www.blender.org/) | Win/Mac/Linux | .glb-Dateien importieren, vollständige 3D-Software |
| [Online 3D Viewer](https://3dviewer.net/) | Browser | Schnelles Ansehen von .glb/.ply ohne Installation |
| Windows 3D Viewer | Windows 10/11 | Standard-App für .glb |

### Bildvorverarbeitung

```bash
# Alle Bilder auf 512px lange Kante verkleinern (spart Speicher)
mkdir resized
mogrify -path resized -resize 512x512\> *.jpg

# oder mit Python
python3 -c "from PIL import Image; [Image.open(f).resize((512, int(Image.open(f).size[1]*512/Image.open(f).size[0]))).save('resized/'+f) for f in ['img1.jpg', 'img2.jpg']]"
```