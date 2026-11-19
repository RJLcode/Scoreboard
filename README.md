# 🏆 Sports Scoreboard

**Current version: v1.0.1**

A fast, mobile-first sports scoreboard built for the iOS home screen. Tracks live, upcoming, and completed games across **NFL, NCAA football, MLB, and NHL** — all from a single HTML file with no dependencies or build step.

## Features

- **Four sports in one** — switch via the bottom nav on mobile or the sidebar on desktop
- **Live / Upcoming / Final tabs** — filter games by status, with counts for each
- **Auto-refresh** every 30 seconds while the page is on screen (a background tab pauses and catches up when you come back), plus a manual refresh button
- **Live indicators** — a red dot on any sport with a game in progress
- **Sport-specific game cards**
  - 🏈 **NFL** — score, quarter, game clock, down & distance, possession, timeouts
  - 🎓 **NCAA** — every FBS game on the NFL-style card, plus AP Top 25 rankings (ranked matchups listed first)
  - ⚾ **MLB** — inning (top/bottom), count, outs, on-base diamond, linescore (R/H/E), probable starters
  - 🏒 **NHL** — period, game clock, shots on goal, OT/SO indicators, probable goalies
- **Team details** — tap any team for its standing, home/away splits, streak, scoring averages, last 5 results, next game, and a link to ESPN
- **Team logos and season records** on every card
- **Responsive** — single column on phones, 2–3 column grid with a sidebar on desktop
- **iOS PWA ready** — add to the home screen for a full-screen, app-like experience, with its own scoreboard icon
- **Handles outages** — each ESPN request gives up after 12 seconds; a sport that can't load says so with a **Try again** button, the last scores stay up if a refresh fails, and the footer says which sports didn't update
- **Accessible** — team columns open with Enter or Space, focus is outlined, muted text meets WCAG AA contrast, and animations are off with Reduce Motion

## Getting started

No install or build is required. Open `index.html` in a browser:

```bash
open index.html
```

Or serve the folder locally (useful for testing on a phone on the same network):

```bash
python3 -m http.server 8000
```

Then visit `http://<your-computer's-ip>:8000`.

### Add to iPhone home screen

1. Host `index.html` somewhere reachable (e.g. GitHub Pages).
2. Open it in Safari.
3. Tap **Share → Add to Home Screen**.

It launches full-screen with a dark status bar, like a native app.

## Data source

All data comes from ESPN's public site API — no API key needed.

| Data | Endpoint |
| --- | --- |
| Scoreboards | `site.api.espn.com/apis/site/v2/sports/{sport}/{league}/scoreboard` |
| Team schedule + basic info | `…/{sport}/{league}/teams/{id}/schedule` |
| Team detail (best-effort) | `…/{sport}/{league}/teams/{id}` |

The NCAA feed uses `groups=80` to include all FBS games (ESPN's default is Top 25 only). This is an unofficial API, so endpoints or fields may change without notice. Every string in ESPN's answers is HTML-escaped as it arrives, and only `https://` links and logo URLs from the feed are used. The team detail endpoint currently doesn't send CORS headers, so browsers block it; the team sheet falls back to the schedule endpoint and derives streak and scoring averages from completed games.

## Project structure

```
index.html             # Markup, styles, and JavaScript — the whole app
manifest.webmanifest   # Home screen name and icons
apple-touch-icon.png   # iPhone home screen icon (also icon-192.png, icon-512.png)
README.md
CHANGELOG.md
CLAUDE.md              # Conventions for Claude Code
LICENSE                # Proprietary license — all rights reserved
```

Inside `index.html`, each sport has a `parse*` function (ESPN JSON → game objects) and a `build*Card` function (game object → HTML). To add a sport:

1. Add its scoreboard URL to `APIS`, plus entries in `PREFIX`, `TEAM_API`, and `SCORE_UNIT`.
2. Register its parser in `loadSport` and its card builder in `renderSport`.
3. Add a sidebar button, a bottom-nav button, and a `view-{sport}` container.

## Versioning

This project follows [Semantic Versioning](https://semver.org/): `vMAJOR.MINOR.PATCH`. Bug fixes and cosmetic changes are PATCH, new features are MINOR. Update the version line at the top of this README and the comment at the top of `index.html`, and add an entry to [CHANGELOG.md](CHANGELOG.md).

## License

Copyright © 2026 RJLcode (https://github.com/RJLcode). All rights reserved.

This project is **proprietary and not open source**. No part of the source code, data, design, or documentation may be copied, modified, distributed, or used without explicit written permission. See [LICENSE](LICENSE) for the full terms.
