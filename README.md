# Travel-Planner
# Travel Planner (TravelMate)

A small, responsive front-end **travel planner** built with vanilla HTML, CSS, and JavaScript.  
It lets you quickly pick a US destination, choose transport, preview travel time and cost, and see hotels and highlight spots in that city.

The app is designed as a mini demo of:

- A holiday-style UI with a soft pastel theme
- Basic trip planning interactions
- A simple API layer using `fetch()` with graceful fallback to mock data

---

## Features

- **Quick Planner panel**
  - Choose transport: ✈️ Flight, 🚆 Train, 🚌 Bus
  - Select destination from a dropdown
  - Set dates and passenger count
  - Get a rough time / price estimate

- **Explore highlights**
  - Responsive gallery of places (attractions, restaurants, parks)
  - Filter by type and sort by popularity / rating / (mock) distance

- **Hotel search**
  - Filter hotels by minimum rating and maximum price
  - See a list of matching hotels for the chosen destination
  - “Select” button per hotel (demo alert)

- **Itinerary card**
  - Save basic trip details (destination, dates, passengers, transport) to `localStorage`
  - Clear and re-save as needed

- **Accessibility & layout**
  - Keyboard-focus styles for buttons and inputs
  - Skip-to-content link
  - Responsive two-column -> single-column layout

---

## Tech Stack

- **HTML5** – semantic layout and ARIA attributes
- **CSS3** – custom pastel theme, responsive grid and flexbox
- **JavaScript (ES6+)**
  - Centralized API service that uses `fetch()` to load destinations
  - Async/await and unified error handling
  - Local storage for itinerary persistence

---

## Data & API Layer

The app now uses a small API wrapper defined in `app.js`:

- `ApiService.getDestinations()` – loads destination data via `fetch('data/destinations.json')`
- `ApiService.getHotels(cityId)` – returns hotels for a given destination
- `ApiService.getTrips()` – placeholder for future real trip data

### How it works

1. On load, the app tries to fetch `data/destinations.json`.
2. If the request **succeeds**, the JSON data is used as the source of truth.
3. If it **fails** (for example, when running from a plain file URL), the app falls back to internal mock data so the UI still works.

Example structure of `data/destinations.json`:

```json
[
  {
    "id": "nyc",
    "name": "New York City, NY",
    "img": "https://…",
    "desc": "Iconic skyline, museums, Broadway shows.",
    "hotels": [
      { "name": "Central Boutique", "rating": 4.5, "price": 240 }
    ],
    "places": [
      { "type": "attractions", "name": "Statue of Liberty", "rating": 4.8 }
    ]
  }
]
