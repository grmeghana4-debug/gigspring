# GigSpring v2 — Automatic opportunity discovery

## What is included
- Single-page web app (`index.html`).
- Fetches public JSON feeds from Remote OK and Jobicy directly in the browser.
- Normalises job fields, removes duplicates, filters by keyword/work type/location/source.
- Direct Apply links open the original listing in a new tab.
- Source attribution and source links are shown on each card.
- Save opportunities using browser localStorage.
- No account, backend, API key, database or paid hosting required for this prototype.

## Run
Open `index.html` in a modern browser while connected to the internet. Public feeds may be unavailable due to CORS, network limits or provider changes. The page reports per-source errors instead of pretending a feed succeeded.

## Deploy for free
Upload `index.html` to a public GitHub repository. Enable Settings → Pages → Deploy from branch → `main` → `/root`. GitHub Pages gives a free `username.github.io/repository` URL. A static hosting provider can also host this file for free under its current free-tier terms.

## Source and reuse notes
- Remote OK: public JSON feed `https://remoteok.com/api`. Its feed guidance asks aggregators to credit Remote OK and link to each original post. See https://remoteok.com/faq.
- Jobicy: public remote-jobs API `https://jobicy.com/api/jobs?count=100`. This prototype credits Jobicy and sends users to the returned original listing URL. Review current API guidance/terms before commercial scale-up: https://jobicy.com/jobs-rss-feed.
- Himalayas is not connected in this browser-only build because its official API documentation says browser JavaScript requests are blocked by CORS. It can be added through a same-origin serverless proxy that caches results and uses the required `applicationLink` unchanged. See https://himalayas.app/api and https://himalayas.app/terms.

This is a prototype implementation, not a legal opinion or a guarantee that every source permits every commercial use. Before monetising, re-check each provider's current terms, honour rate limits, caching/attribution requirements and takedown requests. Do not scrape sites or bypass access controls.

## Known limitations
- The feeds focus on remote opportunities; India-only and exact job-type filters depend on the data supplied by each provider and may not be complete.
- Some providers may block browser requests through CORS. If so, a small server-side proxy would be needed; that would add operational complexity and must obey provider terms and rate limits.
- Refresh is user-triggered; no background polling.
- Saved jobs are local to one browser/device and are not synchronised.
- Deduplication is based on normalised title + company + location, so it is pragmatic rather than perfect.
- No AI resume matching, user accounts, application submission, payment processing or income guarantee.
\n## Why only two live sources in this browser-only version\nHimalayas explicitly documents that its API does not send CORS headers, so direct browser fetches fail. Do not pretend it is connected. A free serverless proxy can be added later if needed, subject to free-tier limits.\n