# Changelog

All notable changes to this project are documented in this file.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project
adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2026-11-07

### Added
- Gradle wrapper fully committed (`gradlew`, `gradlew.bat`, `gradle-wrapper.jar`) — the CI workflow
  and local Termux builds now use `./gradlew` directly; no pre-installed Gradle needed anywhere.
- `:app:testDebugUnitTest` added to the APK workflow — GeoMath unit tests run on every CI build.
- Backend `Dockerfile` (+ `.dockerignore`) honouring `$PORT` with a container health check —
  deployable to RunFlare (Docker hosting), Hugging Face Spaces, or any Docker host.
- `scripts/termux-sign.sh` — one-shot Termux script: installs `openjdk-17`/`gh`, generates the
  RSA-4096 keystore, base64-encodes it and registers all four GitHub Secrets automatically.
- `scripts/upload-to-github.sh` — Termux-friendly `git` push that preserves the hidden
  `.github/workflows` folder (which the GitHub web uploader drops).
- `docs/QUICKSTART-FA.md` — complete Persian quick-start (zip → repo → APK → backend incl. RunFlare).
- `github-workflow-backup/` — visible copies of both workflow files with web-uploader recovery
  instructions (Persian + English).
- RunFlare free-tier deployment option documented in `docs/OPERATIONS.md` (option E).

### Changed
- Version bump to 1.1.0 (app `versionCode` 2, backend package 1.1.0).
- APK workflow: `gradle/actions/setup-gradle@v4` now used for dependency caching only; the build
  itself runs through the committed wrapper.

## [1.0.0] - 2026-11-07

### Added
- Native Android app: Kotlin 2.2, Jetpack Compose (Material 3), MapLibre Native 11 interactive map.
- Region sketching: tap to add 3–10 vertices, undo, clear, live geodesic area estimate.
- Local (offline) polygon validation fallback inside the app; server validation on top.
- FastAPI backend: strict polygon validation (geometry, vertex count, area bounds, self-intersection).
- Live Sentinel-2 L2A catalog metadata search via Copernicus Data Space Ecosystem OData API
  (anonymous, no API key), with cloud-cover filter and full provenance notes.
- Real terrain analysis from AWS Terrain Tiles (Terrarium DEM): elevation statistics, slope (Horn),
  roughness (TRI), gradient-orientation consistency, nodata handling, tile-count limits.
- Documented, weighted surface terrain-anomaly score with explicit scientific caveats
  (surface indicator only — not a buried-target probability).
- Android Settings screen: runtime API base URL override + connection health check.
- GitHub Actions workflows: automatic APK build (debug + release; signed when secrets present,
  unsigned otherwise; artifacts + tag releases) and backend test suite.
- Gradle release signing driven by environment variables (`KEYSTORE_BASE64`, `KEYSTORE_PASSWORD`,
  `KEY_ALIAS`, `KEY_PASSWORD`) — no keystore ever committed.
- Documentation: architecture, science scope, operations (data collection & registration),
  Termux signing guide (فارسی/English), roadmap.
- Persian (فارسی) UI localization; RTL support.
