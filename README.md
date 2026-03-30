# sg-auto-refresh
Changing the Refresh Interval
Default is 60 seconds. You can change it without editing code:

Embed page: Type a new value in the interval box in the floating control bar
Extension: Right-click the extension panel → Configure → enter new seconds

To change the default (what it starts at on page load), edit line 168 in embed-auto-refresh.html:
html<input type="number" id="barInterval" value="60" .../>
Change value="60" to your preferred default (e.g. value="30" for 30 seconds).

Moving to a new GitHub repo
Only 3 lines need updating if you change the GitHub username or repo name:
FileLineValue to updatesweetgreen-auto-refresh.trex21Extension source URLroot-redirect/index.html5Meta refresh redirect URLroot-redirect/index.html11JavaScript redirect URL
embed-auto-refresh.html and index.html contain no GitHub URLs — they only reference Tableau Online and do not need changes.

embed-auto-refresh.html — The main dashboard page
This is the primary file your team actually opens in a browser. It does two things at once:
1. Embeds the Tableau dashboard
It uses the Tableau Embedding API v3 (a JavaScript library loaded from 10ay.online.tableau.com) to pull your Tableau Online dashboard into the page, exactly like an iframe but smarter. The dashboard renders fully — filters, dropdowns, charts — just as if you opened it directly on Tableau Online. Users log in through Tableau's own login screen if they're not already authenticated.
2. Runs the auto-refresh countdown
Once the dashboard finishes loading, a floating control bar appears in the bottom-right corner. It calls viz.refreshDataAsync() every 60 seconds — this is the exact same function Tableau's native "Refresh data in the view" toolbar button calls. It shows:

A circular countdown ring
Last refresh timestamp
Start / Stop / Refresh Now buttons
A configurable interval input

Who uses it: Anyone who needs to monitor the dashboard live. They bookmark https://hkr-sweetg.github.io/sg-auto-refresh/embed-auto-refresh.html instead of the Tableau Online URL.

index.html — The Tableau Extension UI
This file runs inside Tableau Desktop or Tableau Online as a dashboard extension widget. It is not opened in a browser directly — Tableau loads it inside a panel on the dashboard itself via the .trex file.
It does the following:

Shows a countdown ring widget embedded within the Tableau dashboard layout
Uses the Tableau Extensions API (datasource.refreshAsync()) to refresh data sources attached to the dashboard worksheets
Saves the refresh interval setting so it persists across sessions
Shows a "Last Refresh" timestamp and Running/Stopped badge
Lets the user right-click → Configure to change the interval

The Tableau Extension manifest
This is not a webpage — it is an XML configuration file that Tableau reads to understand what the extension is and where to load it from. Think of it as the "ID card" for the extension.
It tells Tableau:

What the extension is called — "Sweetgreen Auto Refresh"
Who made it — author, organisation, email
Where to load the UI from — points to index.html on GitHub Pages (https://hkr-sweetg.github.io/sg-auto-refresh/index.html)
What permissions it needs — full data permission so it can access and refresh data sources
The icon — the base64-encoded image shown in Tableau's extension gallery
Minimum API version — ensures compatibility with the user's version of Tableau

When a Tableau Desktop user double-clicks this .trex file or loads it through the Extension panel, Tableau reads these settings and loads index.html inside the dashboard.
Who uses it: Tableau Desktop users — they load it once when adding the extension to a dashboard, then publish the workbook. After that, it lives inside the workbook automatically.
