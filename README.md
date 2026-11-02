<p align="center">
  <img alt="FreeTube Logo" src="/_icons/logoColor.svg" width="450" align="center">
</p>

# FreeTube (OCLP & Legacy GPU Edition)

An open-source desktop YouTube player for older Macs and legacy hardware, built with privacy in mind.

> [!IMPORTANT]
> ### ⚠️ About This Fork
> **This repository is an independent community fork of the official [FreeTube Project](https://github.com/FreeTubeApp/FreeTube).**
>
> It is maintained specifically for older systems that lost GPU hardware acceleration in **Chromium 152+** (Electron 44+), particularly older Intel Macs running modern macOS (macOS 13 Ventura, 14 Sonoma, 15 Sequoia) via **OpenCore Legacy Patcher (OCLP)**.
>
> **What this fork does:**
> - **Restores GPU Hardware Acceleration:** Pins runtime to **Electron 42.11.18 (Chromium 148 / $\le 151$)**, preserving OpenGL/ANGLE GPU rendering and preventing 100% CPU spikes during video playback.
> - **Preserves macOS 12 Monterey Support:** Retains compatibility for macOS 12 and above (which upstream dropped in v0.26.0).
> - **Syncs Upstream Improvements:** Merges all upstream FreeTube bug fixes, player enhancements (`shaka-player`), YouTube extractor updates (`youtubei.js`, `googlevideo`), Invidious fixes, and SponsorBlock improvements.
> - **Maintains Stability:** Retains Electron 42-compatible main-process clipboard and context menu APIs.
>
> 🍏 **Note for Apple Silicon (M1/M2/M3/M4) Users:** You do **not** need this fork. Apple Silicon Macs feature native Metal architecture and never lost hardware acceleration. Please use the [Official Upstream FreeTube Releases](https://github.com/FreeTubeApp/FreeTube/releases).

> [!NOTE]
> ### ☕ Hobby & Maintenance Notice
> This fork is a personal hobby project created primarily for personal use and maintained in spare time.
>
> **Please do not expect timely or regular updates.** Upstream syncing and maintenance may occur sporadically, or it might not happen at all. Anyone is completely welcome and encouraged to fork this repository, submit PRs, or adapt it for their own needs under the AGPLv3 license!

---

<p align="center">
  <a href="https://github.com/jay3oh5/FreeTube-OCLP-Edition/releases"><b>📥 Download Latest OCLP Release (macOS Intel)</b></a> &bull;
  <a href="CHANGELOG.md"><b>📋 Changelog</b></a> &bull;
  <a href="https://github.com/FreeTubeApp/FreeTube"><b>🌐 Official Upstream FreeTube Project</b></a>
</p>

---

## 📦 Download & Installation (macOS Intel)

1. Head to the [**Releases Page**](https://github.com/jay3oh5/FreeTube-OCLP-Edition/releases) and download `freetube-*-oclp-mac-x64.dmg`.
2. Open the `.dmg` and drag **FreeTube** to your **Applications** folder.

<details>
<summary><b>🛡️ First Launch / macOS Gatekeeper Help</b></summary>

<br>

Because this is an independent community build with an ad-hoc signature, macOS Gatekeeper may prompt on first launch:
* **Option A:** Right-click (or Control-click) **FreeTube.app** in `/Applications`, select **Open**, and click **Open** in the dialog.
* **Option B:** Run this command in Terminal:
  ```bash
  xattr -cr /Applications/FreeTube.app
  ```

</details>

---

## 🖥️ Supported Legacy Hardware & Dropped GPUs

In Chromium 152+, Google removed the legacy OpenGL backend on macOS, mandating a strict Metal-only pipeline via ANGLE. Because legacy GPU drivers patched via OpenCore Legacy Patcher (OCLP) lack compliant Metal 3 support, newer Chromium/Electron builds crash the GPU process or fall back to unaccelerated software rendering.

<details>
<summary><b>📋 Click to expand full list of supported Mac models & GPUs</b></summary>

<br>

### 1. Intel Integrated Graphics
* **Intel HD Graphics 4000 (Ivy Bridge):**
  * MacBook Pro (13" & 15", Mid 2012 / Late 2012 Retina / Early 2013 Retina) (`MacBookPro9,1`, `MacBookPro9,2`, `MacBookPro10,1`, `MacBookPro10,2`)
  * MacBook Air (11" & 13", Mid 2012) (`MacBookAir5,1`, `MacBookAir5,2`)
  * Mac mini (Late 2012) (`MacMini6,1`, `MacMini6,2`)
  * iMac (21.5" & 27", Late 2012 / Early 2013) (`iMac13,1`, `iMac13,2`, `iMac13,3`)
* **Intel HD Graphics 5000 / Iris 5100 / Iris Pro 5200 (Haswell):**
  * MacBook Pro (13" & 15", Late 2013 / Mid 2014) (`MacBookPro11,1`, `MacBookPro11,2`, `MacBookPro11,3`)
  * MacBook Air (11" & 13", Mid 2013 / Early 2014) (`MacBookAir6,1`, `MacBookAir6,2`)
  * Mac mini (Late 2014) (`MacMini7,1`)
  * iMac (21.5", Mid 2014) (`iMac14,4`)
* **Intel HD Graphics 6000 / Iris 6100 / Iris Pro 6200 (Broadwell):**
  * MacBook Pro (13", Early 2015) (`MacBookPro12,1`)
  * MacBook Air (13", Early 2015 – 2017) (`MacBookAir7,1`, `MacBookAir7,2`)
  * iMac (21.5" & 27", Late 2015) (`iMac16,1`, `iMac16,2`)
  * MacBook (12", Early 2015) (`MacBook8,1`)
* **Intel HD Graphics 515 / 530 (Skylake):**
  * MacBook Pro (Late 2016) (`MacBookPro13,1`, `MacBookPro13,2`)
  * MacBook (12", Early 2016) (`MacBook9,1`)
  * iMac (Late 2015) (`iMac17,1`)
* **Pre-Metal Legacy Intel (HD 3000 / Sandy Bridge & older):**
  * MacBook Pro (2011), MacBook Air (2011), Mac mini (2011), MacBook (2010)

### 2. NVIDIA Dedicated Graphics
* **NVIDIA Kepler Architecture (GeForce GT 640M, GT 650M, GTX 660M, GTX 675MX, GTX 680MX, GT 750M):**
  * MacBook Pro (15" Retina, Mid 2012 / Early 2013 / Late 2013 / Mid 2014) (`MacBookPro10,1`, `MacBookPro11,3`)
  * iMac (21.5" & 27", Late 2012 / Late 2013) (`iMac13,1`, `iMac13,2`, `iMac14,2`, `iMac14,3`)
* **Pre-Metal NVIDIA (Tesla / Fermi: GeForce 9400M, 320M, 330M):**
  * MacBook Pro (2008–2010), Mac mini (2009–2010), MacBook (2009–2010)

### 3. AMD / ATI Dedicated Graphics
* **AMD GCN 1st – 3rd Gen (HD 7000 / 8000 series, R9 M290X, M370X, FirePro D300 / D500 / D700):**
  * Mac Pro ("Trash Can", Late 2013) (`MacPro6,1`)
  * MacBook Pro (15" Retina, Mid 2015) (`MacBookPro11,5`)
  * iMac (Retina 5K 27", Late 2014 / Mid 2015) (`iMac15,1`)
* **Pre-Metal TeraScale 1 & 2 (Radeon HD 2000–6000 series):**
  * iMac (2007–2011), MacBook Pro (Late 2011), Mac Pro (2008–2012)

</details>

---

## ✨ Features & Browser Extensions

<details>
<summary><b>✨ View FreeTube Core Features</b></summary>

<br>

* **Ad-Free Video Playback:** Watch YouTube without commercial interruptions.
* **Privacy First:** YouTube can see video requests, but cannot track you across videos using cookies or user JavaScript.
* **Local Subscriptions & History:** Subscriptions, playlists, profiles, and history are stored locally on your device.
* **Multiple Extractors:** Choose between the built-in Local API extractor (`youtubei.js`) or an [Invidious](https://github.com/iv-org/invidious) backend.
* **SponsorBlock & DeArrow Integration:** Automatically skip sponsored segments and replace clickbait thumbnails/titles.
* **External Players:** Play videos through MPV, VLC, or other media players if desired.
* **Distraction-Free Mode:** Hide comments, recommended videos, live chats, or trending tabs to maintain focus.

</details>

<details>
<summary><b>🔗 Browser Extensions (Open Videos directly in FreeTube)</b></summary>

<br>

Automatically redirect YouTube links from your browser into FreeTube:
* **[LibRedirect](https://libredirect.manerakai.com/):** Redirects YouTube links directly to FreeTube (select *FreeTube* as Frontend in the extension's Services settings). Available for [Firefox](https://addons.mozilla.org/firefox/addon/libredirect/) and [Chromium browsers](https://libredirect.manerakai.com/download_chromium.html).
* **[RedirectTube](https://github.com/MStankiewiczOfficial/RedirectTube):** Adds toolbar and context-menu buttons to open YouTube links in FreeTube. Available for [Firefox](https://addons.mozilla.org/firefox/addon/redirecttube/) and [Chrome Web Store](https://chromewebstore.google.com/detail/redirecttube/jpbaggklodpddjcadlebabhiopjkjfjh).

</details>

---

## 🤖 AI Assistance Disclaimer

This fork—including dependency adaptations, build pipeline setup, documentation, and compatibility patches for Electron 42—was created and maintained with the assistance of Artificial Intelligence (AI).

This disclosure is provided for complete transparency for anyone in the open-source community who wishes to know how this repository is maintained.

---

## 👏 Credits & Attribution

All credit for the FreeTube application, design, user interface, and original codebase belongs to the **[FreeTube Team and Contributors](https://github.com/FreeTubeApp/FreeTube)**. 

If you are looking for the official project, documentation, or want to contribute to upstream development:
* **Official Website:** [freetubeapp.io](https://freetubeapp.io/)
* **Official GitHub Repository:** [github.com/FreeTubeApp/FreeTube](https://github.com/FreeTubeApp/FreeTube)
* **Official Documentation & FAQ:** [docs.freetubeapp.io](https://docs.freetubeapp.io/)
* **Official Discussions:** [FreeTube GitHub Discussions](https://github.com/FreeTubeApp/FreeTube/discussions)

---

## 📄 License

FreeTube is Free Software: You can use, study, share, and improve it under the terms of the **[GNU Affero General Public License (AGPLv3)](https://www.gnu.org/licenses/agpl-3.0.html)** as published by the Free Software Foundation.
