# RADAR TEŞKILAT — HAMDANE OPERATION

A responsive local command-center demo built with HTML, CSS, and vanilla JavaScript. No build system or external runtime dependencies are required.

## Run locally

Open `index.html` for the local radar simulation, manually managed device inventory, logs, and preferences. Camera APIs require a secure context: HTTPS, or `localhost` during development. For example:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000`, choose **Camera wall**, and press **Start camera**. The browser will ask for camera permission after that operator action; each stream can be stopped individually. Android Chrome needs a secure HTTPS deployment and camera permission for the site.

## Features

- Dashboard and local status/activity counters.
- Animated radar with clearly labelled synthetic DEMO DATA, selectable targets, zoom, range, pause/resume, and full-screen.
- Four explicitly operator-started browser camera streams, per-camera motion detection switches, sensitivity setting, permission/error messages, and visual frame-difference events.
- Add/edit/delete/search/filter manually registered authorized devices. No nearby device or network discovery.
- Filterable/searchable operation log and CSV export.
- Local theme/operator/settings, notifications, and a UI lock (not authentication).
- Responsive desktop/mobile layout and Netlify deployment configuration.

## Storage and privacy

Settings, devices, notifications, logs, and motion events are stored in the browser's `localStorage` and are not synchronized across browsers/devices. Camera video is displayed in the page; motion sampling uses a small in-memory canvas and no upload is implemented. No camera starts in the background. Radar contacts are simulated and are not real tracking data.

This demo has no backend, user authentication, or access control. The local console lock is only a UI affordance. Do not use it to protect sensitive or operational data.

## Netlify deployment

Deploy the repository root as a static site. `netlify.toml` sets the publish directory to `.` and applies basic security/privacy headers, including camera-only Permissions Policy. No build command is needed. The site must be served over HTTPS for camera access (Netlify provides HTTPS after deployment).

## Optional backend

Supabase is not configured and no credentials are included. If adding a backend, use only a public anon/publishable browser key, enable Row Level Security on exposed tables, and keep service-role secrets on a trusted server. Authentication must be backed by database/server access policies.
