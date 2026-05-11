# Workshop-Ablaufplan

**Dauer: 90 Minuten | Teilnehmerzahl: ca. 15–25 Studierende**

---

## Phase 1: Einführung (10 Min)

| Zeit | Inhalt | Material |
|------|--------|----------|
| 0–5 min | Vorstellung des Sprechers und der Workshop-Ziele | Folien |
| 5–10 min | Kurze Theorie: Wie funktioniert 3D-Rekonstruktion aus Bildern? | Diagramm, Folie |

**Kernbotschaften:**

- Structure-from-Motion (SfM) vs. NeRF vs. Foundation Models
- Foundation Models sind vortrainierte Netze, die „out-of-the-box“ funktionieren
- Kein Mathe-Hintergrund nötig – die Modelle machen das meiste automatisch

!!! abstract "Theorie auf einen Blick"
    Traditionell brauchte man für 3D-Rekonstruktion:

    1. Kalibrierte Kameras
    2. Markante Punkte finden (SIFT, ORB)
    3. Punkte zwischen Bildern matchen
    4. Bundle Adjustment für Kameraposen
    5. Dichte Rekonstruktion (Multi-View Stereo)

    **Foundation Models** wie DUSt3R machen all das in einem einzigen Forward-Pass – 
    trainiert auf Millionen von Bildpaaren und liefern direkt Punktwolken und Tiefenkarten.

---

## Phase 2: Fotoaufnahme (10 Min)

Die Studierenden verlassen den Raum und fotografieren:

- Einen Flur, Treppenhaus oder kleinen Raum
- 10–20 Bilder mit ca. 60–80 % Overlap
- Verschiedene Höhenwinkel
- Keine beweglichen Objekte im Bild

!!! tip "Organisationstipp"
    Teams zu je 2–3 Personen bilden. Eine Person fotografiert, 
    die anderen geben Hinweise zur Überlappung und Kameraführung.

**Detaillierte Hinweise siehe:** [→ Foto-Guide](fototipps.md)

---

## Phase 3: Hands-on 3D-Rekonstruktion (30 Min)

Die Studierenden wählen **eines** der folgenden Modelle aus und laden ihre Fotos hoch:

### Option A: Hugging Face Space (einfach, keine Installation)

```text
1. Browser öffnen → https://huggingface.co/spaces/croco/DUSt3R
2. „Click to Upload“ → eigene Fotos auswählen
3. „Run Inference“ klicken
4. Ergebnis als .glb herunterladen
```

### Option B: Lokale Installation (volle Kontrolle)

Siehe [→ Setup-Anleitung](setup.md) für Schritt-für-Schritt-Anleitungen.

!!! warning "Zeithinweis"
    Wenn die lokale Installation nicht klappt: Sofort auf Hugging Face Space umsteigen!
    Das Ziel ist eine funktionierende Rekonstruktion, nicht das Debuggen von Abhängigkeiten.

**Parallel-Sessions:**

| Tisch | Modell | Empfohlene Zielgruppe |
|-------|--------|----------------------|
| 1–2   | DUSt3R | Erste Erfahrung, schnelle Ergebnisse |
| 3–4   | MASt3R | Etwas ambitionierter, bessere Qualität |
| 5–6   | VGGT   | Experimentierfreudig, bester aktueller Stand |
| 7     | Depth Anything V3 | Interesse an Tiefenkarten und AR-Anwendungen |

---

## Phase 4: Ergebnisse vergleichen & diskutieren (25 Min)

**Ablauf:**

1. **5 min** – Jede Gruppe zeigt ihr Ergebnis (Screenshare oder Dateiweitergabe)
2. **10 min** – Gemeinsame Diskussion: Was hat gut funktioniert? Wo sind Artefakte?
3. **10 min** – Vergleich der Modelle: Wie unterscheiden sich die Ergebnisse?

!!! question "Diskussionsfragen"
    - Warum hat Modell X bessere/schlechtere Ergebnisse als Modell Y?
    - Welche Fotoaufnahme-Technik hat sich bewährt?
    - Wo könnte man solche Technologien in der Praxis einsetzen?
    - Was sind die Grenzen aktueller Foundation Models?

---

## Phase 5: Ausblick & Fragen (15 Min)

| Thema | Inhalt |
|-------|--------|
| Weiterführende Ressourcen | Links zu Tutorials, Papers, Communities |
| Praxisanwendungen | Immobilien, Kultur-e, Robotik, AR/VR |
| Ausblick | Gaussian Splatting, 4D-Rekonstruktion |
| Q&A Zeit | Offene Fragen |

---

## Checklist für Dozent (Vor dem Workshop)

- [ ] VM / Rechner mit Internetzugang getestet
- [ ] Alle Hugging Face Spaces erreichbar
- [ ] Alternative: Lokale Testinstallation durchgeführt
- [ ] Beispielbilder als Fallback bereitgelegt
- [ ] Projektion / Bildschirm funktioniert
- [ ] Uhr sichtbar oder Timer gestellt
- [ ] Team-Einteilung vorbereitet

## Checklist für Teilnehmende (Vor dem Workshop)

- [ ] Smartphone-Kamera funktioniert
- [ ] Ladegerät / Powerbank dabei
- [ ] Laptop mit Internetzugang
- [ ] Google Drive / USB-Stick für Dateitransfer bereit