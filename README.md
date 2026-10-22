# The Midterm Desk · US Midterms 2026

A bilingual (English and French) dashboard for following the November 3, 2026 US midterm elections: Senate and House control, the 36 governor races, and every race as results come in.

## Open the app

Open the app via a local web server for the full PWA experience, such as:

```bash
cd /path/to/US-halfterm-elections26-claude
python3 -m http.server 8000
```

Then visit `http://localhost:8000/` in a modern browser. The app is installable as a PWA on supported browsers and loads the cached app shell offline after the first visit. An internet connection is still needed for live results.

## Live results

The dashboard reads the public, AP-sourced results JSON that The New York Times publishes for each office:

```
https://static01.nyt.com/elections-assets/pages/data/2026-11-03/results-senate.json
https://static01.nyt.com/elections-assets/pages/data/2026-11-03/results-house.json
https://static01.nyt.com/elections-assets/pages/data/2026-11-03/results-governor.json
```

These files go live on election night. Until then they return 404 and the app shows an "awaiting results" state with a countdown, Senate seats not up this year, the states on the ballot and poll-closing times. It checks every 5 minutes while waiting, then every 60 seconds once polls are about to close and results are flowing.

Race calls come from the Associated Press. Vote counts are unofficial until certified by each state.

## Replay a past election

Append `?date=YYYY-MM-DD` to replay any general election that uses the same feed format, for example:

```
http://localhost:8000/?date=2024-11-05
```

The language toggle defaults to the browser's language and remembers the selected language.
