# SkaterBoy – Musikvideo-Exposé

Planungsgrundlage für ein **2:55-min-Musikvideo** (Pop-Punk, Coming-of-Age), das vollständig mit **lokalen KI-Modellen** generiert werden soll. Verbindlicher Tonträger ist der finale Song [`songs/song3.mp3`](songs/song3.mp3) – das Video wird auf den Song geschnitten, nie umgekehrt.

## Handlung in zwei Sätzen

Ein Punk-Skaterjunge liebt das Mädchen aus der anderen Welt (Ballett, reich, beliebt). Als sie ihn vor der ganzen Schule abblitzen lässt, macht er aus der Abfuhr einen Song – und zehn Jahre später sitzt sie vor dem Röhrenfernseher und sieht ihn auf MTV.

## Repo-Struktur

```
.
├── expose.md          # Ausführliches Exposé (verbindliche Arbeitsgrundlage)
├── expose-pres.md     # Präsentation im Marp-Format (14 Folien)
├── expose-spec.md     # Ursprüngliche Aufgabenstellung (unverändert)
└── songs/
    ├── song3.mp3      # FINALER Song "SkaterBoy" (2:55, ≈150 BPM) – verbindlich
    └── fake/          # song1.mp3, song2.mp3 – nur Dummy/Platzhalter, NICHT verwenden
```

## Inhalt des Exposés (`expose.md`)

| Kapitel | Inhalt |
|---|---|
| 1–4 | Logline, Thema, Story & Plot mit Timecodes auf die reale Songstruktur |
| 5 | Figuren (Johnny, Blair, 7 Nebenfiguren) inkl. **Konsistenzanker** und Auftrittsmatrix |
| 6 | 11 Locations mit Licht-Basisstimmung und KI-Plate-Plan |
| 7 | Visuelle Sprache (Teil 1: Super-16mm/1996 · Teil 2: digital-beige/Vorstadt) |
| 8 | **Shot-by-Shot: 79 Einstellungen** – je Dauer, Kameraposition, Kamerabewegung, Licht |
| 9 | Analyse des Song-Masters (Struktur-Marken) & Sounddesign |
| 10–13 | Lokale KI-Pipeline, Risiken, Produktionsplan (~6–7 Wochen), Prompt-Templates |

## Audio-Fakten (per Loudness-/Onset-Analyse gemessen)

- **175,0 s (2:55)** · **≈ 150 BPM** (148–152) · MP3, 48 kHz Stereo, 128 kbit/s
- Struktur-Marken für den Schnitt: Band-Einsatz 5,6 s · Chorus-Peak ab 30 s · Stille-Loch (Count-off) 1:15–1:18.3 · leiseste Stelle 2:08.6–2:22.6 („TEN YEARS LATER") · lauteste Stelle 2:22.6–2:47.2 (MTV-Erkennung) · Final-Hit ≈ 2:47.2

> Lyrics/-Overlays sind nicht Teil des Projekts – der Master trägt den Gesang.

## Präsentation rendern (Marp)

```bash
npm i -g @marp-team/marp-cli

# HTML / PDF / PPTX
marp expose-pres.md
marp expose-pres.md --pdf
marp expose-pres.md --pptx

# Live-Preview im Browser
marp expose-pres.md --watch
```

## Grobe Produktions-Pipeline (alles lokal)

```
Character-Sheets (Flux.1-dev) → LoRAs je Figur → Location-Plates
→ 79 Keyframes → Wan 2.1 I2V (≤ 4 s/Clip) → Face-Fix → Upscale (Real-ESRGAN)
→ RIFE (24 fps) → Schnitt (Resolve/Kdenlive, Kapitelmarker auf Song-Marken)
→ CRT-Compositing & Typografie in Post → Color/Grain → Master (1080p24)
```

- Musik: fertig – nur Conform, Loudness-Master (−9 LUFS) und Sounddesign-Transienten
- Hardware-Richtwert: GPU ≥ 24 GB VRAM, ComfyUI
- Grundregel: **kein KI-Text im Bild** – Graffiti, Titel, MTV-Logo etc. kommen erst in der Post dazu

## Nächste Schritte

1. **P1:** Character-Sheets & LoRAs für die 9 benannten Figuren
2. **P2:** `song3.mp3` ins Schnittprojekt, Kapitelmarker auf die Struktur-Marken, Location-Plates
3. **P3:** Keyframes gemäß Shot-Tabelle (Kap. 8 des Exposés), befüllt in `shotlog.csv`

## Lizenz

Noch nicht festgelegt. Inhalte (Exposé, Präsentation) © 2026 die Projektautor:innen – bis auf Weiteres nur für die interne Produktion gedacht.
