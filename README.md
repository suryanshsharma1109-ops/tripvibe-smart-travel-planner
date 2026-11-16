# TripVibe — Smart Travel Planner

A responsive first-page prototype for planning road trips from Lovely Professional University (LPU). It currently covers Manali and Amritsar.

## What is included

- Destination and trip-length selection with a day-wise itinerary draft.
- Approximate one-way route distances and driving times.
- Fuel search links for towns along each suggested corridor.
- Round-trip fuel estimates based on editable mileage and fuel price.
- A rental estimate that adds the listed daily rental rate to estimated fuel.
- A light/dark theme switch that remembers the user's selection in the browser.
- A small travel-chat interface with sample replies.

## Run it

Open `index.html` in a modern browser. The project uses plain HTML, CSS, and JavaScript and has no build step or package dependencies.

## Public website

The repository includes a GitHub Actions workflow at `.github/workflows/deploy-pages.yml`. It publishes the site from the repository root whenever code is pushed to `main`.

For the first deployment, set the repository's Pages source to **GitHub Actions** in **Settings → Pages → Build and deployment**. Later pushes deploy automatically. The expected site address is `https://suryanshsharma1109-ops.github.io/tripvibe-smart-travel-planner/`.

## Data and estimate notes

The figures in this first prototype are reference estimates checked on 16 November 2026. Fuel and rental prices can change. Route distance and travel time vary with the precise start/end point, road conditions, traffic, and diversions.

- LPU to Amritsar: approximately 95 km one way.
- Phagwara/LPU to Manali: approximately 327 km one way; allow around 8–9 hours before breaks.
- Fuel price inputs start with Jalandhar listings as a nearby reference for LPU. Users can edit the rate and vehicle mileage.
- Rental examples use published starting/day rates from a provider near LPU. The estimate adds rental days and fuel; it does not include tolls, parking, extra-kilometre charges, deposits, outstation fees, meals, or accommodation. Confirm a written quote and availability with the provider.
- Fuel links open map searches for corridor towns. They do not represent a verified list of specific pumps or guarantee opening hours.

Sources:

- [LPU to Amritsar route distance](https://fromto.travel/en/india/lovely-professional-university/pe-amritsar)
- [Phagwara/LPU to Manali route guide](https://pjcarrentals.com/blog/manali-kasol-road-trip-from-phagwara-lpu/)
- [Jalandhar fuel rates](https://www.ndtv.com/fuel-prices/petrol-price-in-jalandhar-city)
- [Nearby rental listings and rates](https://pjcarrentals.com/car-rental-jalandhar/)

## Prototype status

The chat interface uses local sample replies; it is not connected to an AI model or a live itinerary-generation service yet. Route and price values are static starting points, not live data feeds. Connect a travel-data source and an AI service before presenting those features as live AI functionality.

### API key safety

Do not put an AI API key in `index.html`, browser JavaScript, or any public repository file. GitHub Pages serves static files publicly, so a key placed in the page would be visible to every visitor. A real AI chat needs a separate server-side endpoint; store the provider key as a secret on that backend host and have the page call the endpoint. No AI key was supplied for this project, and none is included here.

