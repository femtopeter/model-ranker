# 🪂 Paragliding Model Ranker

**Welches Wettermodell trifft aktuell den Wind am besten — für dein Fluggebiet?**

Eine PWA (Progressive Web App) die automatisch alle verfügbaren Prognosemodelle für einen Standort in Europa vergleicht und nach Treffsicherheit rankt. Optimiert fürs iPhone.

## Was es tut

1. Du wählst ein Fluggebiet (50+ europäische Paragliding-Spots, durchsuchbar)
2. Die App holt für **alle dort verfügbaren Wettermodelle** die gestrige Prognose
3. Vergleicht diese mit den quasi-Messwerten (assimilierte Daten)
4. Rankt die Modelle nach **Wind-Treffsicherheit** (RMSE)
5. Zeigt dir: *"Für Interlaken vertrau heute ICON-CH1, für Annecy AROME France"*

## Verfügbare Modelle

| Modell | Auflösung | Abdeckung |
|---|---|---|
| ECMWF IFS HRES | 9 km | Global |
| ECMWF AIFS | 25 km | Global (KI-Modell) |
| ICON Global | 11 km | Global |
| GFS | 25 km | Global |
| ICON-EU | 7 km | Europa |
| ICON-D2 | 2 km | Zentraleuropa |
| MeteoSwiss ICON-CH1 | 1 km | Schweiz |
| MeteoSwiss ICON-CH2 | 2 km | Schweiz |
| AROME France / HD | 1–1.3 km | Frankreich |
| ARPEGE Europe | 11 km | Europa |
| KNMI HARMONIE | 5.5 km | Europa |
| DMI HARMONIE | 5.5 km | Europa |
| MET Norway Nordic | 1 km | Skandinavien |
| GeoSphere AROME | 2.5 km | Österreich |
| ItaliaMeteo ICON-2I | 2 km | Italien |
| UKMO Global | 10 km | Global |
| GEM Global | 25 km | Global |

Je nach Standort werden nur die relevanten Modelle angezeigt — ein Spot in der Schweiz bekommt z.B. 15+ Modelle, ein Spot in der Türkei nur die Globalmodelle.

## Methodik

- **Ground Truth:** Open-Meteo "Best Match" — assimilierte Daten aus Stationen, Radar, Satelliten (nahe an echten Messwerten)
- **Prognose:** Previous Day 1 je Modell (was gestern für heute vorhergesagt wurde)
- **Score:** Gewichteter RMSE aus Windgeschwindigkeit (40%), Windrichtung (45%), Böen (15%)
- **Vergleichszeitraum:** Letzte 24 Stunden

## Installation (iPhone)

1. Öffne `https://femtopeter.github.io/model-ranker/` in Safari
2. Tippe auf ⬆️ (Teilen)
3. Wähle **"Zum Home-Bildschirm"**
4. Fertig — öffnet sich wie eine eigenständige App

## Setup (GitHub Pages)

Dieses Repo ist so konfiguriert, dass es direkt via GitHub Pages gehostet wird:

- **Settings → Pages → Source:** Deploy from branch `main`, folder `/`
- Live unter: `https://femtopeter.github.io/model-ranker/`

## Dateien

```
index.html      ← Die komplette App (HTML + CSS + JS, standalone)
manifest.json   ← PWA-Manifest (App-Name, Icon, Theme)
sw.js           ← Service Worker (App-Shell-Caching)
README.md       ← Diese Datei
```

## Datenquelle

[Open-Meteo API](https://open-meteo.com/) — kostenlos, kein API-Key, CORS-unterstützt, open source.

## Lizenz

MIT
