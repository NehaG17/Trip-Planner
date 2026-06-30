# 🧭 Waypoint — Trip Planner

A complete, **backend-free** trip planning web app. Plan trips, build day-by-day itineraries with drag-and-drop, split expenses between travelers, track a packing list, check the weather, convert currencies, and find attractions on an interactive map — all running entirely in your browser with **no server, no database, and no sign-up**.

Built with plain HTML, CSS, and JavaScript (no build step required) so it deploys directly to **GitHub Pages**.

## ✨ Features

- **Multiple trips** — create and manage as many trips as you like
- **Day-wise itinerary planner** with **drag-and-drop** reordering (powered by SortableJS) — drag activities within a day or between days
- **Interactive map** (Leaflet + OpenStreetMap tiles) centered on your destination
- **Attraction search** using the OpenStreetMap Overpass API — find museums, parks, cafes, restaurants and more, then add them straight to your itinerary
- **Budget planner** with categorized expenses
- **Dynamic expense splitting** between travelers, with an automatic "who owes whom" settlement calculator (debt simplification)
- **Packing checklist** with progress bar and one-click suggested items
- **Weather forecast** (10-day) via the free Open-Meteo API — no API key required
- **Currency converter** via the free Frankfurter API — no API key required
- **Dashboard** with trip statistics (total trips, days planned, expenses tracked, upcoming activities)
- **Dark / light mode** toggle, persisted across sessions
- **Export itinerary as PDF** (jsPDF)
- Smooth animations, fully responsive layout (desktop, tablet, mobile)
- **All data stored locally** in your browser via `localStorage` — nothing leaves your device except anonymous, keyless requests to OpenStreetMap / Open-Meteo / Frankfurter for maps, attractions, weather, and FX rates

## 🗂️ Project structure

```
trip-planner/
├── index.html          # App shell & all view markup
├── css/
│   └── style.css       # Design system + all styles (light/dark themes)
├── js/
│   ├── storage.js       # localStorage persistence layer
│   ├── util.js           # Formatting & helper functions
│   ├── modal.js           # Generic modal dialog controller
│   ├── map.js              # Leaflet map, geocoding & Overpass attraction search
│   ├── weather.js          # Open-Meteo forecast integration
│   ├── currency.js         # Frankfurter FX conversion
│   ├── pdf.js               # jsPDF itinerary export
│   └── app.js                # Main app controller (routing, rendering, CRUD)
├── .nojekyll            # Tells GitHub Pages to skip Jekyll processing
├── .gitignore
└── README.md
```

No `package.json`, no build tools, no bundler — open `index.html` directly in a browser, or serve the folder with any static file server.

## 🚀 Run locally

Just open `index.html` in a browser, **or** serve it (recommended, so the map/geocoding requests behave normally):

```bash
# Python
python3 -m http.server 8080

# Node (if you have it)
npx serve .
```

Then visit `http://localhost:8080`.

## ☁️ Deploy to GitHub Pages

### 1. Push the project to GitHub

From inside the `trip-planner` project folder:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/NehaG17/Trip-Planner.git
git push -u origin main
```

### 2. Enable GitHub Pages

1. Go to your repository on GitHub: `https://github.com/NehaG17/Trip-Planner`
2. Click **Settings** (top right of the repo).
3. In the left sidebar, click **Pages**.
4. Under **Build and deployment** → **Source**, choose **Deploy from a branch**.
5. Under **Branch**, select **`main`** and folder **`/ (root)`**, then click **Save**.
6. Wait a minute or two — GitHub will publish your site. The URL will appear at the top of the Pages settings panel, typically:

   ```
   https://NehaG17.github.io/Trip-Planner/
   ```

That's it — no build pipeline, no server, no environment variables needed.

> If you ever restructure the project to use a `dist` folder (e.g. you migrate to a React + Vite build), set the **Branch** to `main` with folder `/docs`, or use a `gh-pages` branch / GitHub Actions workflow that publishes the `dist` output instead. This project, as shipped, is plain static HTML/CSS/JS, so deploying straight from `main` → `/ (root)` is all that's required.

## 🔌 Free APIs used (no keys required)

| Purpose | Service |
|---|---|
| Map tiles | [OpenStreetMap](https://www.openstreetmap.org/) tile servers |
| Geocoding (destination search) | [Nominatim](https://nominatim.org/) |
| Attraction search | [Overpass API](https://overpass-api.de/) |
| Weather forecast | [Open-Meteo](https://open-meteo.com/) |
| Currency conversion | [Frankfurter](https://www.frankfurter.app/) |

All requests are made client-side directly from the browser — there is no backend proxy. Please be considerate of these free public services' usage policies (the app keeps requests minimal and on-demand).

## 🧠 How data is stored

Everything (trips, itineraries, expenses, packing lists, notes, theme preference) is saved to your browser's `localStorage` under the key `waypoint_trips_v1`. This means:

- Your data is private to your device/browser and persists across visits.
- Clearing your browser data will erase your trips.
- There is no cross-device sync (no backend!) — this is by design for a fully static, zero-cost deployment.

## 🛠️ Tech stack

- HTML5 / CSS3 (custom design system, CSS variables for theming)
- Vanilla JavaScript (ES6+, no framework)
- [Leaflet.js](https://leafletjs.com/) for maps
- [SortableJS](https://sortablejs.github.io/Sortable/) for drag-and-drop
- [jsPDF](https://github.com/parallax/jsPDF) for PDF export
- Open-Meteo, Frankfurter, Nominatim & Overpass APIs (all free, keyless)

## 📄 License

MIT — use this freely for your own travels.
