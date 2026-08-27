# Car-Log

A personal Progressive Web App for tracking fuel, maintenance, and running costs for a car. Built as a lightweight, single-file PWA with no frameworks, no backend, and no dependencies — just HTML, CSS, and vanilla JavaScript.

Live at: **[iadeelsarwar.github.io/Car-Log](https://iadeelsarwar.github.io/Car-Log/)**

---

## Features

### Fuel Log
- Record each fill-up: date, odometer reading, litres, and total cost
- Live preview of pence-per-litre and MPG as you type
- MPG calculated using UK imperial gallons (litres × 4.54609)
- Previous mileage auto-populated from the last fill-up

### Maintenance / Service Log
- Log any service job with date, mileage, cost, and notes
- Preset service types: Oil Change, MOT, Tyres, Brakes, Air Filter, Spark Plugs, Battery, Full/Interim Service, and more
- Free-text notes field for recording parts, specs, or supplier details

### Summary Dashboard
- Toggle between **This Month**, **This Year**, and **All Time** views
- Total spend, fuel cost, service cost, and average MPG at a glance
- Cost breakdown table showing fuel vs maintenance split
- MPG bar chart across the last 8 fill-ups with data

### Odometer
- Tap the mileage pill in the header to update the current reading at any time
- Auto-updates whenever a fill-up or service is logged at a higher mileage

---

## Technical Details

| | |
|---|---|
| **Type** | Progressive Web App (PWA) |
| **Stack** | HTML5, CSS3, Vanilla JS — no frameworks |
| **Storage** | `localStorage` — all data stays on device |
| **Offline** | Service worker caches all assets on first load |
| **Installable** | Web App Manifest included — add to home screen on iOS and Android |
| **Hosting** | GitHub Pages (static, no server required) |
| **Bundle size** | Single `index.html` (~29 KB), `manifest.json`, `sw.js` |

### File structure

```
Car-Log/
├── index.html       # Entire app — markup, styles, and logic
├── manifest.json    # PWA manifest (name, theme, icons)
├── sw.js            # Service worker for offline caching
└── icons/
    ├── icon-192.png
    └── icon-512.png
```

### Data model

All data is stored as a single JSON object in `localStorage` under the key `qashqai-log`:

```json
{
  "mileage": 88000,
  "fuel": [
    {
      "id": "abc123",
      "date": "2026-08-27",
      "mileage": 88000,
      "litres": 45.2,
      "cost": 68.50,
      "prevMileage": 87620,
      "mpg": 38.4,
      "notes": "Shell, full tank"
    }
  ],
  "maint": [
    {
      "id": "def456",
      "date": "2026-08-01",
      "mileage": 87500,
      "type": "Oil Change",
      "cost": 35.00,
      "notes": "Castrol Edge 5W-30 A3/B4, 4.2L"
    }
  ]
}
```

### MPG calculation

MPG is calculated in **UK imperial gallons**:

```
MPG = (miles driven / litres used) × 4.54609
```

---

## Deployment

Hosted as a static site on GitHub Pages. No build step, no CI pipeline — files are edited and committed directly.

To run locally, just open `index.html` in a browser. Service worker offline caching requires a local server (e.g. `npx serve .`).

---

## Roadmap

- [ ] Icon assets for PWA install
- [ ] CSV export of fuel and maintenance logs
- [ ] Next service reminder (by mileage or date)
- [ ] Cost-per-mile calculation

---

## License

MIT
