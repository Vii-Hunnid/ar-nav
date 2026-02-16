# AR Navigation

GPS-based augmented reality navigation app. Search for any place, save it as a tag, and follow AR waypoints through your phone's camera to get there.

Built with [A-Frame](https://aframe.io/), [AR.js](https://ar-js-org.github.io/AR.js-Docs/), [OSRM](https://project-osrm.org/) (free routing), and [Nominatim](https://nominatim.org/) (free geocoding).

## Live Demo

**https://vii-hunnid.github.io/ar-nav/**

Open on a mobile device with camera and GPS access.

## Features

- **Place search** — Search for any place worldwide using OpenStreetMap/Nominatim (free, no API key). Results are biased towards your current location
- **Save as tag** — Tap **+ Save** on any search result to add it to your saved destinations. Tags persist across sessions via localStorage
- **Remove tags** — User-added tags can be removed with the x button; default locations stay
- **Default JHB locations** — Ships with destinations around Johannesburg (Rosebank Mall, Melrose Arch, Sandton City, Nelson Mandela Square, The Zone @ Rosebank)
- **Live distance on list** — Each destination shows real-time distance from your current position
- **Walking route via OSRM** — Fetches real walking paths (sidewalks, crossings) using the free OSRM API
- **Turn-by-turn HUD** — Shows next maneuver (turn left/right, continue) with distance and ETA
- **AR waypoint path** — Blue spheres along the route in the camera view; turn green when close
- **AR destination pin** — 3D marker appears when facing the destination
- **Step auto-advance** — Navigation progresses automatically as you walk
- **iOS support** — Handles DeviceOrientationEvent.requestPermission() for iOS 13+
- **Stop & return** — Back button to stop navigation and pick a different destination

## How It Works

1. **Search** for a place or pick from your saved destinations
2. Tap **+ Save** to add a search result as a persistent tag
3. Select a destination and tap **Navigate**
4. Grant camera, GPS, and compass permissions
5. A walking route is fetched from OSRM
6. Follow the blue AR waypoint spheres through your camera
7. The HUD shows turn-by-turn directions and live ETA
8. Tap **Stop navigation** to go back and pick another destination

## Configuration

### Default locations

Edit `DEFAULT_LOCATIONS` in `index.html` to change the built-in destinations:

```js
var DEFAULT_LOCATIONS = [
    { name: 'Rosebank Mall',          lat: -26.1460, lng: 28.0436 },
    { name: 'Melrose Arch',           lat: -26.1340, lng: 28.0690 },
    { name: 'Sandton City',           lat: -26.1076, lng: 28.0567 },
    { name: 'Nelson Mandela Square',  lat: -26.1070, lng: 28.0530 },
    { name: 'The Zone @ Rosebank',    lat: -26.1468, lng: 28.0445 }
];
```

### User-added tags

Tags added via search are stored in `localStorage` under the key `ar_nav_locations`. They persist across browser sessions on the same device. Users can remove their added tags with the x button on each entry.

## Local Development

```bash
npm install
npm start
```

Starts a local server on port 8080. Open on your phone (same Wi-Fi) to test. Camera and GPS require HTTPS — use `localhost` or a self-signed cert.

## Tech Stack

| Component | What it does |
|-----------|-------------|
| [A-Frame](https://aframe.io/) | 3D/WebXR scene rendering |
| [AR.js](https://ar-js-org.github.io/AR.js-Docs/) | Camera passthrough AR |
| [OSRM](https://project-osrm.org/) | Free walking route API (no key) |
| [Nominatim](https://nominatim.org/) | Free place search / geocoding (no key) |
| Geolocation API | GPS tracking |
| DeviceOrientation API | Compass heading |
| localStorage | Persistent user-added tags |

## Requirements

- A modern mobile browser (Chrome, Safari, Firefox)
- Camera access
- GPS / Location Services enabled
- Device orientation / compass (for direction)
- Internet connection (to load libraries, search places, and fetch routes)

## License

MIT
