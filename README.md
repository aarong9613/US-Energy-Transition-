# US-Energy-Transition-
D3 visualization to track energy transition in the US using EIA and EPA data.


README - US Green Energy Transition Tracker (Team 046)


$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
                            DESCRIPTION
$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
The US Green Energy Transition Tracker is an interactive, browser-based
dashboard that visualizes historical electricity generation, capacity, and
emissions data across all 50 US states from 2010 to 2024, and extends those
trends into the future with forecasts through 2030.

The dashboard is built as a single HTML file using D3.js and TopoJSON. It loads
plant-level data from a merged EIA Form 860 / eGRID CSV dataset and aggregates
it by state and year. Users can explore metrics including raw
totals (capacity in MW, net generation in MWh, CO2 emissions), derived rates
(capacity utilization, heat rate, emissions intensity), year-over-year growth
figures, and fuel-mix percentages (solar, wind, coal, gas, nuclear, hydro, etc.).

Forecasts for 2025-2030 are generated automatically using non-linear polynomial
regression (degree 2 or 3 selected by AIC) fit to each state-metric pair. A
national aggregate trend is also modeled and displayed. Forecasted values are
visually distinguished from historical data throughout the dashboard.

Key features include:
  - Choropleth map of the US with a year slider (2010-2030) and auto-play
  - Automatic k-means state clustering with elbow-method k selection
  - A national trend chart with historical and forecast segments
  - Three configurable line charts comparing up to 4 states or national averages
  - A free-text notes/annotations panel for analyst observations

$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
                            INSTALLATION
$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

No build tools, package managers, or server-side setup are required. The only
dependency is a modern web browser (Chrome, Firefox, Edge, or Safari).

Prerequisites:
  - A modern web browser with JavaScript enabled
  - The data file: data.csv (must be placed in the same directory
    as the HTML file)
  - An active internet connection (CDN libraries are loaded at runtime)

The following libraries are fetched automatically from CDN at runtime:
  - D3.js v7      (https://cdn.jsdelivr.net/npm/d3@7/dist/d3.min.js)
  - TopoJSON v3   (https://cdn.jsdelivr.net/npm/topojson-client@3/dist/topojson-client.min.js)
  - US Atlas      (https://cdn.jsdelivr.net/npm/us-atlas@3/states-10m.json)

Steps:
  1. Download or clone the project folder.
  2. Ensure the following two files are in the same directory:
       - index.html  (or the provided HTML file)
       - data.csv
  3. Open a terminal in that directory and start a local HTTP server, e.g.:
       Python 3:  python -m http.server 8000
       Node.js:   npx serve .
  4. Open your browser and navigate to:
       http://localhost:8000



$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$
                             EXECUTION
$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$

Once the page loads in your browser, the dashboard is ready to use immediately.
The following steps walk through a basic demo:

  Step 1 - Explore the Map
    The left panel shows a choropleth map of the US defaulting to "Capacity (MW)"
    for the year 2010. Use the "Map metric" dropdown to switch to a different
    metric (e.g., "Solar Generation Mix (%)").

  Step 2- Animate Through Time
    Press the Play button below the map to auto-advance the year slider from
    2010 through 2030. Years beyond 2024 are shown with an amber color scheme
    and a "FORECAST" banner to distinguish them from historical data.

  Step 3 - Enable State Clustering
    Check the "State clusters (k-means elbow)" checkbox to overlay color-coded
    cluster borders on the map. The optimal number of clusters (k) is chosen
    automatically and a legend is displayed below the checkbox.

  Step 4 - Inspect the National Chart
    The national trend chart at the bottom-left shows historical totals (solid
    blue line) and forecasted values (dashed amber line). A red cursor line
    tracks the currently selected year.

  Step 5 - Compare States in the Line Charts
    In the right panel, click "+ Add state" to select up to 4 states (or the
    national average) for comparison. Each of the three line charts can be set
    to a different metric using its own dropdown. Hover over any data point to
    see a tooltip with the exact value.

  
