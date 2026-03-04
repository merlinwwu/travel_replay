# Travel Replay

An open-source travel animation tool built on top of the AMap JavaScript API.

`travel_replay.html` helps you create cinematic route-replay videos with:
- satellite map rendering
- driving route planning (with optional waypoints)
- flight path animation
- camera/altitude tuning
- per-segment duration and timing control

You only need to register an AMap API account, then fill in `CODE` and `KEY` to run it.

## Demo

GitHub README does not allow runnable `iframe` embeds, so this project uses a cover-image fallback:

[![Travel Replay Demo](./docs/travel_fly.png)](https://www.bilibili.com/video/BV1GsPPz4EkV/?vd_source=41447eb6fd0c223019b86d19ff895fd5)

Click the image to watch the full video on Bilibili.

## Quick Start

1. Register for AMap Open Platform credentials:
   - JS API `KEY`
   - Security `CODE` (`securityJsCode`)
2. Open [`travel_replay.html`](./travel_replay.html) and update:

```js
const CONFIG = {
  securityCode: 'CODE',
  apiKey: 'KEY',
  debug: false,
  startDelay: 1800,
  earthCenter: [105, 35]
};
```

3. Run with a local static server (recommended):

```bash
python3 -m http.server 8000
```

4. Open:

```text
http://localhost:8000/travel_replay.html
```

## What You Can Configure

- `JOURNEY_PLAN`: sequence of drive/fly segments
- `start` / `end` / `waypoints`: route nodes
- `timing`: travel duration, waypoint stop, destination stop
- `camera.intro` / `camera.drive` / `camera.fly`: zoom, pitch, heading behavior
- `flight`: arc or straight flight path with density/height control
- `icons`: vehicle and node icon overrides

## Tech Notes

- Core map engine: AMap JS API v2.0 (`@amap/loader`)
- Driving path source: `AMap.Driving` route planning
- Rendering mode: 3D + satellite tile layer
- Single-file implementation: no build step required

## File Structure

```text
.
├── travel_replay.html
└── docs/
    └── travel_fly.png
```

## Disclaimer

Please make sure your API key usage, attribution, and deployment setup comply with AMap's latest terms and policies.
