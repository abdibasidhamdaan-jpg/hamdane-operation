# RADAR TEŞKILAT — HAMDANE OPERATION

A responsive, browser-local command-center demo built with plain HTML, CSS, and JavaScript. No build step or external runtime dependencies are required.

## Run locally

- Open `index.html` in a current desktop or mobile browser for the radar simulator, device inventory, logs, settings, and other local demo features.
- To use camera streams, serve the files from **HTTPS** or `localhost` (camera APIs are normally unavailable from an insecure network origin). For example, with Python installed:

  ```sh
  python3 -m http.server 8000
  ```

  Then visit `http://localhost:8000` and select **Camera wall → Start camera**. The browser asks for permission. Each stream is stopped when its Stop button is used; closing the page also stops active tracks.

## Included features

- Dashboard with live clock, local system status, activity feed, and counters.
- Animated 360-degree radar with selectable, explicitly synthetic `DEMO DATA` targets, zoom, range, pause/resume, and full-screen controls.
- Four operator-started camera panels using `getUserMedia({ video: true, audio: false })`. Permission denials, missing hardware, unsupported contexts, and stream errors are shown in the UI.
- In-browser visual frame-difference motion detection for active streams, with sensitivity adjustment, local timestamped event history, and notifications.
- Manually maintained authorized-device inventory with add/edit/delete, search, status filter, and local persistence. It does not scan for nearby devices or networks.
- Searchable/filterable local activity logs and CSV download.
- Admin preferences, operator display profile, and local console lock/unlock.

## Data and privacy

The app stores settings, manual device records, notifications, and logs in `localStorage` on the current browser profile. Clearing browser site data removes them. Camera frames are compared in memory in the page for visual motion detection; no frame upload is implemented. No camera starts without an operator click and browser permission. The radar contacts are simulated and are not real tracking data.

## Optional backend

This version intentionally runs without a backend and contains no credentials. Supabase is not configured or required. If adding a backend later, use a public anon/publishable key only in the browser, enforce Row Level Security on every exposed table, and keep service-role or other privileged secrets on a trusted server. Add authentication only alongside server-side/database policies that enforce the authenticated user's access.

## Deploy

The site is static and can be deployed from the repository root to GitHub Pages, Netlify, or another static host. Ensure the deployment is HTTPS for camera access. No build command or publish directory beyond the repository root is needed.
