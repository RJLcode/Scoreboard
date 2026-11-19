# Changelog

All notable changes to Scoreboard are documented here.

This project follows [Semantic Versioning](https://semver.org/): `vMAJOR.MINOR.PATCH`

| Part | When to bump | Example |
|------|-------------|---------|
| **MAJOR** | Complete UI overhaul | `v1.0.0` → `v2.0.0` |
| **MINOR** | New sport, new view, or new feature | `v1.0.0` → `v1.1.0` |
| **PATCH** | Bug fix, label tweak, or cosmetic change | `v1.0.0` → `v1.0.1` |

---

## [v1.0.1] — 2026-11-19

- Fixed faded game cards: each card faded in from transparent, the fade replayed on every 30-second refresh, and it could stall part-way and leave logos and times dim. Cards now slide in without fading, and animations are off for people who turn on Reduce Motion
- Team records, "VS", linescore headings and other muted text are brighter (contrast was 1.9:1, now at least 4.6:1, WCAG AA)
- ESPN requests time out after 12 seconds. A sport that never loaded shows "Couldn't reach ESPN" with a **Try again** button, and the footer says which sports didn't update instead of always saying "Updated"
- Auto-refresh pauses while the page is hidden and catches up when it's back on screen
- Every string from ESPN is HTML-escaped before it's put on the page, and only `https://` logo and ESPN links are used
- Team columns can be opened with the keyboard (Tab, then Enter or Space), and focused controls show an outline
- Add to Home Screen: added a scoreboard app icon and web app manifest
- Added `.gitignore`, `CHANGELOG.md` and `CLAUDE.md`, and a version number

## [v1.0.0] — 2026-10-22

- Baseline: NFL, NCAA football, MLB and NHL scoreboards with Live / Upcoming / Final tabs, team detail sheets, and an iOS home screen layout
