# NASA Space Explorer

> Astronomy Picture of the Day (APOD) viewer built on NASA's public API. Search by date range, save favorites locally, toggle day/night mode, and download in HD.

![Status](https://img.shields.io/badge/status-stable-success?style=flat-square)
![Stack](https://img.shields.io/badge/stack-vanilla%20JS-yellow?style=flat-square)
![API](https://img.shields.io/badge/api-NASA%20APOD-blue?style=flat-square)

---

## Overview

A single-page application that consumes the [NASA APOD API](https://api.nasa.gov/) to explore the universe one photo at a time. It started as a frontend exercise and grew into something more complete: a small but real state model, favorites persistence, theme toggle, validation rules, a modal-based detail view, and keyboard / click-outside dismissal.

**Built without frameworks** — pure HTML, CSS, and JavaScript.

## Features

- Today's APOD loaded automatically on page open
- Date-range search with validation (no future dates, no inverted ranges, no missing dates)
- Title filter applied on top of date-range results
- Random APOD button (uses the API's `&count=1` parameter)
- Detail modal with full explanation, date, HD image, favorite toggle, and HD download link
- Favorites view, persisted across sessions in `localStorage` under the key `nasa_favs`
- Day/night theme toggle, also persisted in `localStorage`
- Modal closes on `Escape` key or click-outside
- Toast notifications for errors and user feedback
- Video media types filtered out (APOD occasionally returns videos)

## Stack

| Layer | Tech |
|---|---|
| Markup & Layout | HTML5, CSS Grid, Flexbox |
| Styling | CSS3 with theme switching |
| Logic | JavaScript ES6+ (`async/await`) |
| Data | NASA APOD REST API via Fetch |
| Persistence | Browser `localStorage` (favorites + theme) |

## Project structure

```
nasa-space-explorer/
├── index.html      Markup and root layout
├── styles.css      Visual styling and theme
└── app.js          Application logic, API, rendering, favorites, theme
```

## Internal architecture

The JS is organized in clear layers even without a framework:

| Layer | Functions |
|---|---|
| Config | `API_KEY`, `BASE_URL`, DOM refs, max-date constraint |
| Service | `apiCall()` — fetch + error handling + loader |
| UI helpers | `showToast()`, `showLoading()`, `renderGallery()` |
| Components | `createCard()`, `openModal()`, `closeModal()` |
| Favorites | `getFavorites()`, `checkIfFavorite()`, `toggleFavorite()`, `showFavorites()` |
| Actions | `loadToday()`, `loadRange()`, `loadRandom()`, `filterTitle()` |
| Theme | `toggleViewMode()`, `loadViewMode()` |

## Run locally

```bash
git clone https://github.com/zappytw/Nasa-Explorer-CampusLands-FayadJoel.git
cd Nasa-Explorer-CampusLands-FayadJoel
```

Replace the API key in `app.js`:

```js
const API_KEY = "YOUR_NASA_API_KEY";
```

Open `index.html` in a browser. No build step, no dependencies.

> Get a free API key at [api.nasa.gov](https://api.nasa.gov/). **Note:** for a real deployment the key should come from an environment variable or a backend proxy, not be hardcoded in client-side JS.

## What I learned building this

- Designing a small but real state model in vanilla JS (gallery view modes, favorites, theme)
- Defensive API calls with errors surfaced to the user via toast notifications
- Building UX (modals, toasts, theme toggle, keyboard handlers) without UI libraries
- Persisting multiple independent client-side states in `localStorage`
- Filtering unsupported media types from a mixed API response

---

Built by **Joel Fayad** — Frontend Developer based in Colombia.
