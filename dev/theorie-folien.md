---
marp: true
theme: default
class: invert
paginate: true
backgroundColor: #1a202c
style: |
  section {
    font-family: 'Segoe UI', 'Helvetica Neue', Helvetica, Arial, sans-serif;
    color: #f7fafc;
    font-size: 28px;
    padding: 40px 60px;
  }
  h1 {
    color: #63b3ed;
    font-size: 48px;
    margin-bottom: 0.5em;
  }
  h2 {
    color: #68d391;
    font-size: 36px;
    margin-top: 0.3em;
  }
  strong {
    color: #f6ad55;
  }
  ul, ol {
    line-height: 1.6;
  }
  li {
    margin-bottom: 0.3em;
  }
  code {
    background-color: #2d3748;
    color: #fbd38d;
    padding: 2px 8px;
    border-radius: 4px;
    font-size: 0.85em;
  }
  blockquote {
    border-left: 6px solid #63b3ed;
    padding-left: 20px;
    color: #a0aec0;
    font-style: italic;
    background-color: #2d3748;
    padding: 15px 20px;
    border-radius: 0 8px 8px 0;
  }
  table {
    width: 100%;
    border-collapse: collapse;
    font-size: 0.85em;
    margin-top: 1em;
  }
  th, td {
    padding: 12px 16px;
    border: 1px solid #4a5568;
    text-align: left;
  }
  th {
    background-color: #2d3748;
    color: #63b3ed;
    font-weight: 600;
  }
  tr:nth-child(even) {
    background-color: #2d3748;
  }
  .center {
    text-align: center;
  }
  .small {
    font-size: 0.8em;
  }
  .highlight-box {
    background-color: #2d3748;
    border: 2px solid #68d391;
    border-radius: 12px;
    padding: 20px;
    margin: 1em 0;
  }
---

# From Photos to 3D Model

## Foundation Models für 3D-Rekonstruktion

**Workshop Einführung | 90 Minuten**

*Uwe Hahne – Computer Vision / Deep Learning*

---

## Was bedeutet „3D-Rekonstruktion"?

> Aus **2D-Fotos** → **3D-Modell**

Die Berechnung von Tiefe und Geometrie aus Bildern – ohne Laser, ohne LiDAR.

---

## Anwendungen heute

- 🏠 **Immobilien** – Virtuelle Rundgänge
- 🏛️ **Kultur** – Digitalisierung von Bauwerken
- 🤖 **Robotik** – SLAM, Navigation
- 🎮 **Gaming** – Photogrammetrie für Assets
- 🕶️ **AR/VR** – Realitätsnahe Umgebungen

---

## Traditioneller Workflow

```
📷  Kalibrierte Kameras
 →  🔍  Feature Detection (SIFT, ORB)
 →  🔄  Feature Matching zwischen Bildpaaren
 →  🧮  Bundle Adjustment (Kameraposen)
 →  🏗️  Dense Reconstruction (MVS)
 →  🌫️  Punktwolke / Mesh
```

<style scoped>section {font-size: 24px;}</style>

---

## Probleme beim traditionellen Ansatz

<div class="highlight-box">

- **Kamerakalibrierung** nötig (Brennweite, Distortion)
- **Aufwandiges Matching** bei schwierigen Texturen
- **Sensitiv** gegenüber: Spiegelungen, Bewegung, ähnlichen Objekten
- **Lange Rechenzeiten** bei großen Szenen
</div>

---

## Foundation Models = Game Changer

<div class="highlight-box">

- **Vortrainiert** auf Millionen von Bildpaaren
- **Keine Kalibrierung** nötig – funktioniert mit beliebigen Bildern
- **Ein Forward-Pass** statt mehrerer Pipeline-Schritte
- **Robust** gegenüber realen Aufnahmebedingungen

</div>

<blockquote>
„One model to reconstruct them all"
</blockquote>

---

## Grundidee: Wie funktioniert das?

<div class="highlight-box">

**Eingabe:** 2 oder mehr beliebige, unkalibrierte Bilder

**Trainiert auf:** Große Datensätze mit bekannten 3D-Ground-Truth

**Ausgabe:**
- Punktwolke (Punkte im 3D-Raum)
- Kameraposen (wie war die Kamera positioniert?)
- Tiefenkarte (Abstand jedes Pixels)

</div>

---

## Modell 1: DUSt3R

**NAVER LABS Europe | 2024**

- **Eingabe:** 2 beliebige Bilder → gemeinsame Punktwolke
- **Besonderheit:** Keine Kalibrierung, keine Kameraposen
- **Nutzen:** Sofortiges Ergebnis, einfachster Einstieg

```bash
demo.py --weights DUSt3R_ViTLarge_BaseDecoder_512_dpt.pth
```

| Lizenz | Non-commercial (CC BY-NC-SA) |
| Hardware | 6 GB VRam empfohlen, CPU okay |

---

## Modell 2: MASt3R

**NAVER LABS Europe | 2024 (Nachfolger)**

- **Fast wie DUSt3R**, aber schneller und genauer
- **Besseres Matching** – auch bei größeren Bildsammlungen
- **~5× schneller** bei gleicher/besserer Qualität

```bash
demo.py --weights MASt3R_ViTLarge_BaseDecoder_512_catmlp.pth
```

| Lizenz | Non-commercial (CC BY-NC-SA) |
| Hardware | 12 GB VRam empfohlen |

---

## Modell 3: VGGT

**VGG Oxford / Meta AI | 2025**

- **State-of-the-Art** Genauigkeit auf Benchmarks
- **Apache 2.0** – kommerziell nutzbar
- **Herausforderung:** Hoher VRam-Verbrauch (~24 GB)

```bash
python demo.py --input images/ --output output/
```

| Lizenz | **Apache 2.0** (kommerziell nutzbar) |
| Hardware | 24 GB VRam ideal |

---

## Modell 4: Depth Anything V3

**HKU / ByteDance | 2025**

- **Spezialfall:** Keine vollständige 3D-Rekonstruktion
- **Nur Tiefenkarte** aus **einem einzigen Bild**
- **Sehr schnell**, echtzeitfähig
- Perfekt für AR-Anwendungen und Fokus-Effekte

```bash
python run.py --encoder vitl --img-path bild.jpg --outdir output/
```

| Lizenz | **Apache 2.0** |
| Hardware | 4 GB VRam |

---

## Vergleich der 4 Modelle

| Kriterium | DUSt3R | MASt3R | VGGT | Depth Any V3 |
|-----------|--------|--------|------|-------------|
| **Eingabe** | 2+ Bilder | 2+ Bilder | 2+ Bilder | 1 Bild |
| **Ausgabe** | Punktwolke | Punktwolke | Punktwolke | Tiefenkarte |
| **Geschwindigkeit** | Mittel | Schnell | Langsam | Sehr schnell |
| **Genauigkeit** | Gut | Sehr gut | Ausgezeichnet | Gut |
| **Lizenz** | NC | NC | **Apache 2.0** | **Apache 2.0** |
| **Kommerziell** | ❌ | ❌ | ✅ | ✅ |

<style scoped>section {font-size: 22px;}</style>

---

## Zwei Wege zur Nutzung

<div class="highlight-box">

**🤗 Hugging Face Space (5 Minuten)**
- Browser öffnen → Bilder hochladen → „Run Inference"
- Keine Installation, sofort startklar

**💻 Lokale Installation (20–30 Minuten)**
- Python, PyTorch, Repository klonen
- Volle Kontrolle, offline nutzbar, keine Upload-Limits

</div>

---

## Was machen wir heute?

1. **10 Min** | Theorie *(gerade eben passiert)*
2. **10 Min** | Fotos aufnehmen (im Gebäude)
3. **30 Min** | Hands-on: 3D-Rekonstruktion mit gewähltem Modell
4. **25 Min** | Ergebnisse vergleichen & diskutieren
5. **15 Min** | Ausblick & Fragen

---

## Foto-Aufnahme: Die 3 goldenen Regeln

<div class="highlight-box">

1. **60–80% Überlappung** zwischen allen Bildern
2. **Nicht zoomen** – sich physisch bewegen!
3. **Mindestens 10–20 Bilder** aufnehmen

</div>

→ Detaillierte Tipps: *Workshop-Website → Foto-Guide*

---

## Ein Wort zur Hardware

| Szenario | Empfehlung |
|----------|-----------|
| **Workshop heute** | Hugging Face Space im Browser |
| **Laptop mit GPU** | Lokale Installation (DUSt3R) |
| **VM/Cloud GPU** | Lokale Installation (MASt3R/VGGT) |
| **CPU-only Laptop** | DUSt3R mit `--device cpu` (langsam aber möglich) |

---

## Ausblick: Was kommt als Nächstes?

- **Gaussian Splatting** – Neuer Standard für 3D-Rendering
- **4D-Rekonstruktion** – Bewegte Szenen in Raum und Zeit
- **Text-zu-3D** – „Ein 3D-Modell der Eiffelturm generieren"
- **Mixed Reality** – Real-time 3D Scanning in AR-Brillen

---

# Vielen Dank!

## Fragen? Dann los geht's!

📷 **Nächster Schritt:** Fotos aufnehmen

🔗 **Ressourcen:** https://KIMBOT26.github.io/3D-Reconstruction-Workshop/