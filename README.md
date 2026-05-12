# NASA Space Explorer

> Astronomy Picture of the Day (APOD) viewer built on top of NASA's public API. Search by date range, save favorites locally, and download images in HD.

![Status](https://img.shields.io/badge/status-stable-success?style=flat-square)
![Stack](https://img.shields.io/badge/stack-vanilla%20JS-yellow?style=flat-square)
![API](https://img.shields.io/badge/api-NASA%20APOD-blue?style=flat-square)

---

## Overview

A single-page application that consumes the [NASA APOD API](https://api.nasa.gov/) to explore the universe one photo at a time. It started as a frontend exercise and grew into a small but complete product: it has its own state model, a favorites system persisted in `localStorage`, validation rules, and a modal-based detail view.

**Built without frameworks** — pure HTML, CSS, and JavaScript.

## Features

- View today's astronomy picture automatically on load
- Search any date range (validated against future dates and inverted ranges)
- Detail modal with full explanation, title, date, and HD download
- Save and remove favorites with persistence between sessions
- Toast notifications for user feedback and errors
- Responsive grid layout, mobile-friendly

## Stack

| Layer | Tech |
|---|---|
| Markup & Layout | HTML5, CSS Grid, Flexbox |
| Styling | CSS3 with glassmorphism and custom animations |
| Logic | JavaScript ES6+ |
| Data | NASA APOD REST API via Fetch |
| Persistence | Browser `localStorage` |

## Project structure

```
nasa-space-explorer/
├── index.html      Markup and root layout
├── styles.css      Visual styling and animations
└── app.js          Application logic, API, rendering, favorites
```

## Internal architecture

The JS is organized in clear layers, even without a framework:

| Layer | Responsibility |
|---|---|
| Config | `API_KEY`, `BASE_URL`, DOM references |
| Service | `apiCall()` — fetch, normalization, error handling, loader |
| UI helpers | `showToast()`, `showLoading()`, `renderGallery()` |
| Components | `createCard()`, `openModal()`, `closeModal()` |
| Actions | `loadToday()`, `loadRange()`, `toggleFavorite()` |

## Run locally

```bash
git clone https://github.com/zappytw/Nasa-Explorer-CampusLands-FayadJoel.git
cd Nasa-Explorer-CampusLands-FayadJoel
```

Add your NASA API key in `app.js`:

```js
const API_KEY = "YOUR_NASA_API_KEY";
```

Open `index.html` in a browser. No build step, no dependencies.

> Get a free API key at [api.nasa.gov](https://api.nasa.gov/).

## Roadmap

- [x] Day/night theme toggle
- [x] Keyword search
- [ ] Video support (currently images only)
- [ ] Cloud-synced favorites
- [ ] Pagination for large date ranges
- [ ] Social sharing

## What I learned building this

- Designing a small but real state model in vanilla JS
- Defensive API calls and user-facing error handling
- Building UX (modals, toasts, animations) without UI libraries
- Persisting client-side state cleanly with `localStorage`

---

Built by **Joel Fayad** — Frontend Developer based in Colombia.
