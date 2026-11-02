# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.26.0-oclp.1] - 2026-11-02

### Added
- **Full Legacy GPU Hardware Acceleration:** Pinned runtime to Electron 42.11.18 (Chromium 148 / $\le 151$) to restore full OpenGL/ANGLE hardware rendering on Macs using OpenCore Legacy Patcher (OCLP).
- **macOS 12 Monterey Compatibility:** Retained compatibility for macOS 12+ (which upstream FreeTube dropped in v0.26.0).
- **GitHub Actions Cloud Release Pipeline:** Added automated CI/CD workflow (`.github/workflows/release-build.yml`) to compile and package standalone macOS x86_64 DMGs, ZIPs, and 7Z archives in the cloud.
- **Hardware Compatibility Documentation:** Added comprehensive breakdown in `README.md` and `RELEASE_NOTES.md` documenting all dropped Intel, NVIDIA, and AMD legacy GPUs.
- **Upstream Feature Ingestion:** Merged all 616 commits from upstream FreeTube v0.26.0:
  - Added SponsorBlock channel exclusions list (`#9508`).
  - Added player crash recovery button in the video info bar (`#9722`).
  - Added current/default Invidious instance information (`#9464`).
  - Added experimental setting toggle for hardware acceleration.

### Changed
- **Electron Main Process Clipboard API:** Adapted the link-copying routines in `src/main/index.js` to use Electron 42's stable clipboard API instead of the breaking `ClipboardItem` API introduced in Electron 44.
- **Dependency Locking:** Locked `electron` to `^42.5.2` (resolving to `42.11.18`), `electron-context-menu` to `^4.1.2`, and `electron-builder` to `^26.15.7`.

### Fixed
- **YouTube Playback Throttling:** Updated `youtubei.js` to `^18.3.0` and `googlevideo` to `^4.1.1` to resolve video stream buffering and format parsing failures.
- **Live Stream DVR Playback:** Updated `shaka-player` to `^5.3.3` to fix live and post-live DVR playback and font rendering issues.
- **Live Chat Auto-Scroll:** Fixed intermittent live chat auto-scrolling issues (`#10027`).
- **Invidious Playlist Limits:** Fixed playlist fetching being capped at 200 videos (`#9564`).
- **UI Tooltip Clipping:** Added automatic positioning for tooltips to prevent cutoff and unwanted scrollbars (`#9944`).
- **Database Decimal Precision:** Fixed default playback rate decimal-place overflow when reading from database (`#9997`).
