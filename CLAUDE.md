# Claude Code Instructions

- Always bump the patch version in index.html (the `<!-- Scoreboard vX.Y.Z | YYYY-MM-DD -->` comment at the top), README.md, and CHANGELOG.md when making changes
- Add a dated entry to CHANGELOG.md for every index.html change
- Update README.md's Features section if a change affects how the page behaves
- Keep it a single `index.html` with vanilla JavaScript: no frameworks, build steps or dependencies
- Escape anything from ESPN before it goes into the page (data from `fetchJSON` is already escaped; use `safeUrl` for links and images)
- .gitignore is present — do not commit node_modules or other ignored files
- Version format is `vMAJOR.MINOR.PATCH` — bug fixes and cosmetic changes are PATCH only
