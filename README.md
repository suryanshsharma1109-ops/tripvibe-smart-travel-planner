# TripVibe — Smart Travel Planner

A responsive first-page prototype for planning road trips from Lovely Professional University (LPU). It currently covers Manali and Amritsar.

## What is included

- Destination and trip-length selection with a day-wise itinerary draft.
- Approximate one-way route distances and driving times.
- Fuel search links for towns along each suggested corridor.
- Round-trip fuel estimates based on editable mileage and fuel price.
- A rental estimate that adds the listed daily rental rate to estimated fuel.
- A light/dark theme switch that remembers the user's selection in the browser.
- A travel-chat interface that sends the loaded page data to a server-side AI endpoint when deployed on Vercel.
- A page-grounded OpenAI Responses API handler at `api/chat.js`, with an exact out-of-scope fallback and request limits.

## Run it

Open `index.html` in a modern browser for the static demo. The project uses plain HTML, CSS, and JavaScript and has no build step or package dependencies. The AI endpoint requires server-side hosting.

## Public website

The live site is [TripVibe Smart Travel Planner](https://suryanshsharma1109-ops.github.io/tripvibe-smart-travel-planner/).

The repository's Pages source is configured for **GitHub Actions**. The workflow at `.github/workflows/deploy-pages.yml` publishes the repository root on pushes to `main`; it can also be run manually from the Actions tab. GitHub Pages only serves static files, so the existing Pages URL continues to show the clearly labeled travel-chat demo until the API is deployed on a serverless host.

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

## AI chat deployment

`api/chat.js` is a Vercel Node.js Function that calls the OpenAI Responses API. It receives the current webpage text, planner data, selected trip settings, and a short conversation history. The model is instructed to answer only from those supplied facts. If a question is outside the loaded page or the requested fact is missing, the endpoint returns exactly: `Please ask the questions according to the loaded webpage`.

To make the AI version live:

1. Import this GitHub repository into a Vercel project and deploy from the repository root.
2. In the Vercel project's server-side Environment Variables, add `OPENAI_API_KEY` using a key from your OpenAI API account. Optionally set `OPENAI_MODEL` (defaults to `gpt-4.1-mini`).
3. Redeploy after saving the environment variables. Open the resulting Vercel URL; that URL serves the same planner with `/api/chat` enabled.

The currently published GitHub Pages URL remains static and cannot run `api/chat.js`. No API key is included in the repository. Route and price values are static planning estimates, not live data feeds.

### API key safety

Do not put an AI API key in `index.html`, browser JavaScript, or any public repository file. Store it only in the hosting provider's encrypted server-side environment variables. `.env.example` contains variable names only. No API key was supplied or available in this workspace.

