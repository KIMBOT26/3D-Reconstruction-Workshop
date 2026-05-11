# Foto-Guide für 3D-Rekonstruktion

Gute Fotos sind der Schlüssel zu guten 3D-Modellen. Mit diesen Tipps bekommst du schon mit einem Smartphone brauchbare Ergebnisse.

---

## Die goldenen Regeln

### 1. Überlappung (60–80 %)

!!! tip "Wichtigste Regel"
    Jedes Bild muss ca. 60–80 % Inhalt mit dem vorherigen Bild teilen.
    Das Modell braucht gemeinsame Merkmale, um die Position zu berechnen.

```
Falsch:     [Bild 1]    [Bild 2]    [Bild 3]   (nur 20 % Overlap)
Richtig:    [Bild 1]
               [Bild 2]
                  [Bild 3]             (70 % Overlap)
```

**Praxistipp:** Stell dir vor, du machst eine Serie für ein Panorama – nur dass du dich langsam vorwärts bewegst anstatt nur zu schwenken.

### 2. Bewegung statt Zoom

!!! failure "Nicht tun"
    Auf dem Fleck stehen und nur heranzoomen oder nur schwenken. Das Modell braucht echte Parallaxen.

!!! success "Stattdessen"
    Physisch durch den Raum laufen und aus verschiedenen Positionen fotografieren.

| :x: Falsch | :white_check_mark: Richtig |
|------------|-----------------------------|
| Zoom statt Bewegung | Vorwärts seitwärts bewegen |
| Nur Drehen auf der Stelle | Mehrere Positionen einnehmen |
| Tele-Objektiv | Weitwinkel oder normale Brennweite |

### 3. Bildanzahl

- **Minimum:** 5–8 Bilder (für sehr kleine, einfache Szenen)
- **Empfohlen:** 10–20 Bilder
- **Maximum:** 50+ (je nach Modell, mehr ist nicht immer besser – Rechenzeit!)

### 4. Beleuchtung

!!! tip "Gute Beleuchtung verbessert Ergebnisse erheblich"

- :white_check_mark: Gleichmäßige, diffuse Beleuchtung
- :white_check_mark: Tageslicht ohne starke Schatten
- :x: Vermeiden: Blitz, starkes Gegenlicht, wechselnde Lichtverhältnisse
- :x: Vermeiden: Bewegliche Lichtquellen (Laternen, Bildschirme)

### 5. Kameraführung

!!! tip "Für DUSt3R/MASt3R/VGGT"

- **Höhe:** Brust- bis Augenhöhe, konstant halten
- **Winkel:** Geradeaus (leicht nach unten okay)
- **Absolut vermeiden:** Starke Neigungen, „Dutch Angle"
- **Bewegung:** Langsam und gleichmäßig, keine schnellen Drehungen

### 6. Was darf sich bewegen?

!!! failure "Bewegliche Objekte verfälschen die Rekonstruktion"

:heavy_check_mark: **Fest:** Wände, Möbel, Türen (geschlossen), Bücherregale
:x: **Vermeiden:** Menschen, Vorhänge im Wind, Bildschirme, offene Türen, Pflanzen im Luftzug

!!! note "Tipp"
    Wenn etwas sich bewegt: Entweder warten oder Bereich auslassen.
    Besser ein Loch im Modell als ein verzerrtes Artefakt.

---

## Beispielhafter Weg durch einen Raum

Hier ein beispielhafter Weg durch einen kleinen Besprechungsraum mit Tisch und Stühlen:

```
                    [EINGANG]
                       |
    ┌─────────────────┼─────────────────┐
    │                 │                 │
    │   (1)          (2)          (3)   │  ← Erste Reihe: breit von vorne
    │                 │                 │
    │    ┌──────────┴──────────┐       │
    │    │      TISCH          │       │
    │    └──────────┬──────────┘       │
    │                 │                 │
    │   (4)          (5)          (6)   │  ← Zweite Reihe: näher am Tisch
    │                 │                 │
    │    ┌──┐      ┌──┐      ┌──┐      │
    │    │S1│      │S2│      │S3│      │
    │    └──┘      └──┘      └──┘      │
    │                 │                 │
    │   (7)          (8)          (9)   │  ← Dritte Reihe: Ecke links bis rechts
    │                 │                 │
    └─────────────────┴─────────────────┘
```

**Für diesen Raum:**

1. Vor der Tür (Eingang)
2. Links neben der Tür, Richtung Mitte
3. Rechts neben der Tür, Richtung Mitte
4. Links am Tisch, leicht von vorn
5. Tischmitte von vorn
6. Rechts am Tisch, leicht von vorn
7. Ecke links hinten, Richtung Raummitte
8. Hinten mittig, Richtung Tür
9. Ecke rechts hinten, Richtung Raummitte

**Aus jeder Position:** 1–2 Bilder (unterschiedliche Höhen: stehend + leicht gebeugt)

---

## Technische Kameraeinstellungen

### Smartphone

!!! tip "Moderne Smartphones funktionieren gut auf „Automatik""

- **Auflösung:** 4K oder höchste verfügbar (für Details)
- **Format:** JPG (ausreichend, raw ist überflüssig)
- **HDR:** Aus – HDR kann Artefakte verursachen
- **Blitz:** Aus
- **Fokus:** Automatisch (tippen zum Scharfstellen)
- **Brennweite:** Hauptkamera (nicht Tele, nicht Ultra-Weitwinkel)

### Spiegelreflex / Systemkamera (falls vorhanden)

- **Brennweite:** 24–50 mm (Kleinbildäquivalent)
- **Blende:** f/5.6–f/8 (scharfe Abbildung, gute Schärfentiefe)
- **ISO:** Automatisch mit Max. 1600
- **Verschlusszeit:** Automatisch, mindestens 1/60s
- **Fokus:** Einzel-AF, auf Raummitte
- **Weißabgleich:** Automatisch oder Tageslicht (bei Tageslicht)

---

## Checkliste vor der Aufnahme

- [ ] Akku des Smartphones voll (oder Powerbank dabei)
- [ ] Genug Speicherplatz frei
- [ ] Blitz ausgeschaltet
- [ ] HDR ausgeschaltet
- [ ] Räumlichkeiten frei von beweglichen Personen
- [ ] Gleichmäßige Beleuchtung vorhanden
- [ ] Testbild gemacht und geprüft (scharf? ausreichend hell?)

---

## Nach der Aufnahme: Schnell-Check

Bevor du die Bilder ins Modell lädst, überprüfe kurz:

1. **Anzahl:** 10–20 Bilder?
2. **Qualität:** Keine verwackelten, überbelichteten oder zu dunklen Bilder?
3. **Vielfalt:** Von mehreren Positionen aufgenommen?
4. **Inhalt:** Keine beweglichen Objekte drauf?
5. **Format:** JPG oder PNG?

!!! tip "Dateinamen"
    Benenne die Bilder fortlaufend: `01_eingang.jpg`, `02_links.jpg`, ...
    Das hilft später beim Zuordnen.

---

## Häufige Fehler und wie man sie vermeidet

| Fehler | Folge | Lösung |
|--------|-------|--------|
| Nur 2–3 Bilder | Modell kann keine stabile Rekonstruktion berechnen | Mindestens 8–10 Bilder, besser 15 |
| Zu schnell bewegt | Bilder verwackelt, keine scharfen Features | Langsam gehen, bei jedem Bild 2 Sekunden stehenbleiben |
| Gegenlicht/Fenster | Bereiche total überbelichtet | Seitwärts zum Fenster fotografieren, oder Gardinen schließen |
| Spiegelungen | Falsche Tiefenwerte bei glänzenden Flächen | Winkel ändern, glänzende Flächen vermeiden |
| Identische Objekte | Mehrere identische Stühle verwirren das Matching | Ausreichende Überlappung und unterschiedliche Blickwinkel |
| Aufgelöste Verbindung | Bildserie unterbrochen, dann wieder aufgenommen | Kontinuierliche Serie ohne lange Pausen |

---

## Weiterführende Ressourcen

- :material-video: [YouTube: How to take photos for Photogrammetry](https://www.youtube.com/results?search_query=photogrammetry+photo+tutorial)
- :material-book-open-variant: [Meshroom Photogrammetry Guide](https://meshroom-manual.readthedocs.io/en/latest/)
- :material-file-document: [RealityCapture – Capturing Reality Best Practices](https://www.capturingreality.com/BestPractice)