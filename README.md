# AR Navigation

GPS-based augmented reality navigation app. Point your phone's camera and get real-time directions to a destination with distance, bearing, and a 3D AR marker overlay.

Built with [A-Frame](https://aframe.io/) and [AR.js](https://ar-js-org.github.io/AR.js-Docs/).

## Live Demo

**https://vii-hunnid.github.io/ar-nav/**

Open on a mobile device with camera and GPS access.

## Features

- **GPS tracking** — Continuously tracks your location using the Geolocation API
- **Haversine distance** — Calculates real-world distance to the destination in meters/km
- **Compass bearing** — Uses device orientation to determine which way you're facing
- **HUD overlay** — Shows distance and turn instructions (left / right / in view)
- **AR pin** — A 3D marker (sphere + cylinder + label) appears in the camera view when you're facing the destination
- **iOS support** — Handles `DeviceOrientationEvent.requestPermission()` for iOS 13+

## How It Works

1. Tap **Start AR** to grant camera, location, and motion permissions
2. The app tracks your GPS coordinates and compares them to the destination
3. A heads-up display shows the distance and which direction to turn
4. When the destination is within your camera's field of view (~40°), a 3D pin appears in the AR scene

## Local Development

```bash
npm install
npm start
```

This starts a local server on port 8080. Open it on your phone (same Wi-Fi network) to test with real GPS and camera. Note: camera and GPS require HTTPS — for local testing you may need to use `localhost` or set up a self-signed cert.

## Configuration

To change the destination, edit the coordinates in `index.html`:

```js
this.setDestination(40.7128, -74.0060, 0, 'Shopping Mall');
//                  lat      lon        alt  name
```

## Requirements

- A modern mobile browser (Chrome, Safari, Firefox)
- Camera access
- GPS / Location Services enabled
- Device orientation / compass (for direction)

## License

MIT
