# 🐾 Fährten Tracker

Eine mobile-first Web-App für die Fährtenarbeit im Hundesport (IGP/IFH). Fährte legen, den Hund beim Ausarbeiten verfolgen, Gegenstände markieren und das Training auswerten und speichern – direkt im Browser, ohne App-Store-Installation.

## Features

- 📍 **GPS-Tracking** für "Fährte legen" (Mensch) und "Hund sucht" (separater Track), inkl. Distanz- und Zeitmessung
- 🗺️ **Karte** (Satellit/Straße umschaltbar) via [Leaflet](https://leafletjs.com/)
- 📌 Gegenstände während der Fährte markieren
- 🌡️ Live-Wetter (Temperatur, Wind) über [Open-Meteo](https://open-meteo.com/)
- ⏱️ Liegezeit-Stoppuhr
- 📖 FCI-Prüfungsordnung 2025 als Nachschlagewerk (IGP 1–3, IFH 1–3)
- 🕓 Trainings-Historie mit Mini-Karte pro Fährte, lokal gespeichert (`localStorage`)
- 📅 Seminar-Übersicht auf einer Karte
- 📱 Als PWA installierbar (Manifest inklusive)

## Nutzung

Einfach `index.html` im Browser öffnen — oder über GitHub Pages hosten (siehe unten). Es gibt keinen Build-Schritt, keine Abhängigkeiten außer Leaflet (wird per CDN geladen).

### Lokal testen

```bash
git clone https://github.com/<dein-name>/<dein-repo>.git
cd <dein-repo>
# einfacher lokaler Server, z.B.:
python3 -m http.server 8000
```

Dann `http://localhost:8000` im Browser öffnen.

> ⚠️ **Wichtig:** Der Browser gibt Standortdaten (GPS) nur auf `https://`- oder `localhost`-Seiten frei. Beim direkten Öffnen der Datei per Doppelklick (`file://`) funktioniert die Standortabfrage nicht.

### Auf GitHub Pages veröffentlichen

1. Repo auf GitHub erstellen und den Code pushen (siehe Befehle weiter unten)
2. **Settings → Pages** öffnen
3. Unter **Source** den Branch `main` und Ordner `/ (root)` auswählen
4. Nach kurzer Zeit ist die App unter `https://<dein-name>.github.io/<dein-repo>/` erreichbar (HTTPS ✅, GPS funktioniert)

## Projektstruktur

```
.
├── index.html        # Die komplette App (HTML, CSS, JS in einer Datei)
├── manifest.json      # PWA-Manifest ("Zum Home-Bildschirm hinzufügen")
├── icons/
│   ├── icon-192.png
│   └── icon-512.png
├── LICENSE
└── README.md
```

## Bekannte Einschränkungen

- Die Kartenkacheln nutzen inoffizielle Google-Maps-Endpunkte (`mt1.google.com/vt/...`). Das funktioniert meist, ist aber nicht offiziell für diesen Zweck freigegeben. Für den produktiven/dauerhaften Einsatz empfiehlt sich ein offizieller Anbieter (z. B. [MapTiler](https://www.maptiler.com/), [Mapbox](https://www.mapbox.com/) oder die offizielle Google Maps Platform API mit eigenem API-Key).
- Die Trainings-Historie wird nur lokal im Browser (`localStorage`) gespeichert — kein Cloud-Sync, kein Export. Bei Löschen der Browserdaten geht die Historie verloren.
- Kein Service Worker → die App funktioniert nicht komplett offline, lädt aber bis auf Karte/Wetter aus dem Cache.

## Lizenz

MIT — siehe [LICENSE](LICENSE). Bitte `[DEIN NAME]` darin durch deinen Namen ersetzen.
