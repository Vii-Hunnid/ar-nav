# AR Navigation

GPS-based augmented reality navigation app. Pick a destination from a list, get a walking route, and follow AR waypoints through your phone's camera in real time.

Built with [A-Frame](https://aframe.io/), [AR.js](https://ar-js-org.github.io/AR.js-Docs/), and [OSRM](https://project-osrm.org/) (free routing).

## Live Demo

**https://vii-hunnid.github.io/ar-nav/**

Open on a mobile device with camera and GPS access.

## Features

- **Tagged destinations** — A configurable list of locations with name, latitude, and longitude
- **Live distance on list** — Each destination shows its distance from you, updated in real time
- **Walking route via OSRM** — Fetches a real walking path (sidewalks, crossings) using the free OSRM API — no API key needed
- **Turn-by-turn HUD** — Shows next maneuver (turn left, turn right, continue straight) with distance and ETA
- **AR waypoint path** — Blue spheres rendered along the route in the camera view so you can visually follow the path
- **AR destination pin** — A 3D marker (red sphere + yellow cylinder + label) appears when facing the destination
- **Step auto-advance** — Navigation automatically progresses to the next step as you walk
- **iOS support** — Handles `DeviceOrientationEvent.requestPermission()` for iOS 13+
- **Stop & return** — A back button lets you stop navigation and pick a different destination

## How It Works

1. The start screen shows a list of tagged destinations with live distances
2. Tap a destination to select it, then tap **Navigate**
3. The app requests camera, GPS, and compass permissions
4. A walking route is fetched from OSRM
5. The AR camera view shows blue waypoint spheres along the route path
6. The HUD shows your next turn, distance remaining, and ETA
7. As you walk, steps auto-advance and waypoints update in real time

## Adding / Editing Destinations

Edit the `LOCATIONS` array near the top of `index.html`:

```js
var LOCATIONS = [
    { name: 'Empire State Building', lat: 40.748817, lng: -73.985428 },
    { name: 'Times Square',          lat: 40.758896, lng: -73.985130 },
    { name: 'Central Park',          lat: 40.785091, lng: -73.968285 },
    { name: 'Brooklyn Bridge',       lat: 40.706086, lng: -73.996864 },
    { name: 'Statue of Liberty',     lat: 40.689247, lng: -74.044502 }
];
```

Each entry needs:
| Field  | Description                        |
|--------|------------------------------------|
| `name` | Display name shown in the list/HUD |
| `lat`  | Latitude (decimal degrees)         |
| `lng`  | Longitude (decimal degrees)        |

## Local Development

```bash
npm install
npm start
```

Starts a local server on port 8080. Open on your phone (same Wi-Fi) to test. Camera and GPS require HTTPS — use `localhost` or a self-signed cert for local testing.

## Tech Stack

| Component | What it does |
|-----------|-------------|
| [A-Frame](https://aframe.io/) | 3D/WebXR scene rendering |
| [AR.js](https://ar-js-org.github.io/AR.js-Docs/) | Camera passthrough AR |
| [OSRM](https://project-osrm.org/) | Free walking route API (no key required) |
| Geolocation API | GPS tracking |
| DeviceOrientation API | Compass heading |

## Requirements

- A modern mobile browser (Chrome, Safari, Firefox)
- Camera access
- GPS / Location Services enabled
- Device orientation / compass (for direction)
- Internet connection (to load libraries and fetch routes)

## License

MIT
