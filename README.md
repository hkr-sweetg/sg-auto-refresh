# Sweetgreen – Tableau Auto-Refresh Embed

## About `tableau_autorefresh_embed.html`
This is a self-contained HTML file built to embed the **Today's Frontline Throughput** Tableau dashboard directly in a browser — with automatic page refresh built in.

## About `tableau_autorefresh_embed_DS_Refresh'
This is a self-contained HTML file built to embed the **Today's Frontline Throughput** Tableau dashboard data sources will be refreshed and retain the selected store — with automatic page refresh built in.
## About `tableau_autorefresh_embed_Page_Refresh'
This is a self-contained HTML file built to embed the **Today's Frontline Throughput** Tableau dashboard webpage will be refreshed (not Data source) and retain the selected store  — with automatic page refresh built in.
**Their is a 4 seconds delay to render the page**

The file solves a common operations need: keeping a Tableau dashboard visible on a screen (such as a store monitor or ops display) and ensuring it always shows the latest data without anyone manually refreshing the page.

### What It Does

When opened in a browser, the file loads the Frontline Throughput dashboard inside the page and gives the user controls to set how often it should automatically reload. The user picks a refresh interval — anywhere from 1 minute to 15 minutes, or a custom value — and clicks Start. From that point, the page reloads the dashboard on that schedule automatically, with a progress bar counting down to the next refresh. A **Refresh Now** button is also available to trigger an instant reload at any time.

The entire solution is a single HTML file with no external dependencies, no installation, and no backend required. It loads the Tableau dashboard using the official Tableau Embedding API v3 and works in any modern browser as long as the user is already signed into Sweetgreen's Tableau Cloud site.

### Key Controls

- **Refresh every** — dropdown to set the auto-refresh interval (1 min · 2 min · 3 min · 5 min · 10 min · 15 min · Custom)
- **▶ Start Auto-Refresh** — begins the automatic reload cycle
- **⏹ Stop** — pauses the auto-refresh
- **↻ Refresh Now** — reloads the dashboard immediately on demand

### Requirements

- A modern browser (Chrome, Edge, Firefox, Safari)
- An active Sweetgreen Tableau Cloud session (`10ay.online.tableau.com`) open in the same browser
