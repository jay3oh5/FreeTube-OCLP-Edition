<p align="center">
 <img alt="" src="/_icons/logoColor.svg" width=500 align="center">
</p>

# FreeTube (Legacy GPU & OCLP Edition)

FreeTube is an open source desktop YouTube player built with privacy in mind.
Use YouTube without advertisements and prevent Google from tracking you with their cookies and JavaScript.
Available for Windows (10 and later), Mac (macOS 12 and later) & Linux thanks to Electron.

> [!IMPORTANT]
> ### ⚠️ About This Fork
> **This repository is a specialized fork of [FreeTube](https://github.com/FreeTubeApp/FreeTube)** maintained specifically for machines that lost GPU hardware acceleration in **Chromium 152+** (Electron 44+).
> 
> Starting in Chromium 152, the Chromium team removed the legacy OpenGL graphics backend on macOS, enforcing a strict Metal-only (Metal 3 / modern Metal) pipeline via ANGLE. On older Intel Macs running modern macOS (macOS 13 Ventura, 14 Sonoma, 15 Sequoia) via **OpenCore Legacy Patcher (OCLP)**, these older GPUs rely on root-patched drivers that lack compliant Metal 3 support. In upstream Chromium 152+, this causes the GPU process to crash or permanently fall back to unaccelerated software rendering, creating severe UI lag, frame drops, and heavy CPU usage during YouTube video playback (especially with VP9 and AV1 codecs).
> 
> **What this fork does:**
> - Pins **Electron to 42.x** (running **Chromium 148 / $\le 151$**) to retain full OpenGL/ANGLE hardware acceleration, smooth video playback, and low CPU usage.
> - Preserves compatibility for **macOS 12 Monterey** (which upstream FreeTube dropped in v0.26.0).
> - Adapts the main-process clipboard and context-menu APIs for Electron 42 stability.
> - Tracks and merges all upstream YouTube extraction updates (`youtubei.js`, `shaka-player`, `googlevideo`), Invidious instance fixes, SponsorBlock enhancements, and UI bug fixes.
>
> 🍏 **Note for Apple Silicon (M1/M2/M3/M4) Users:** You do **not** need this fork. Apple Silicon features native Metal architecture and never lost hardware acceleration in Chromium 152+. Please download the official upstream FreeTube releases.

---

### 🖥️ Machines & GPUs Dropped from Hardware Acceleration (Chromium 152+)

This fork is designed for Mac hardware relying on OpenCore Legacy Patcher (OCLP) root patches for GPU acceleration, including:

#### 1. Intel Integrated Graphics
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
* **Pre-Metal Intel Legacy (HD 3000 / Sandy Bridge & older):**
  * MacBook Pro (Early / Late 2011) (`MacBookPro8,1`, `MacBookPro8,2`, `MacBookPro8,3`)
  * MacBook Air (Mid 2011) (`MacBookAir4,1`, `MacBookAir4,2`)
  * Mac mini (Mid 2011) (`MacMini5,1`, `MacMini5,2`)
  * MacBook (Mid 2010) (`MacBook7,1`)

#### 2. NVIDIA Dedicated Graphics
* **NVIDIA Kepler Architecture (GeForce GT 640M, GT 650M, GTX 660M, GTX 675MX, GTX 680MX, GT 750M):**
  * MacBook Pro (15" Retina, Mid 2012 / Early 2013 / Late 2013 / Mid 2014) (`MacBookPro10,1`, `MacBookPro11,3`)
  * iMac (21.5" & 27", Late 2012 / Late 2013) (`iMac13,1`, `iMac13,2`, `iMac14,2`, `iMac14,3`)
* **Pre-Metal NVIDIA (Tesla / Fermi: GeForce 9400M, 320M, 330M):**
  * MacBook Pro (2008–2010)
  * Mac mini & MacBook (2009–2010)

#### 3. AMD / ATI Dedicated Graphics
* **AMD GCN 1st – 3rd Gen (HD 7000 / 8000 series, R9 M290X, M370X, FirePro D300 / D500 / D700):**
  * Mac Pro ("Trash Can", Late 2013) (`MacPro6,1`)
  * MacBook Pro (15" Retina, Mid 2015) (`MacBookPro11,5`)
  * iMac (Retina 5K 27", Late 2014 / Mid 2015) (`iMac15,1`)
* **Pre-Metal TeraScale 1 & 2 (Radeon HD 2000–6000 series):**
  * iMac (2007–2011)
  * MacBook Pro (Late 2011 HD 6750M / HD 6770M)
  * Mac Pro (2008–2012 with legacy ATI cards)

---

<p align="center"><a href="https://github.com/FreeTubeApp/FreeTube/releases">Download FreeTube</a></p>
<p align="center">
  <a href="https://github.com/FreeTubeApp/FreeTube/actions/workflows/build.yml">
    <img alt='Build status' src="https://github.com/FreeTubeApp/FreeTube/actions/workflows/build.yml/badge.svg?branch=development" />
  </a>
  <a href="https://hosted.weblate.org/engage/free-tube/">
    <img src="https://hosted.weblate.org/widgets/free-tube/-/svg-badge.svg" alt="Translation status" />
  </a>
</p>

<hr>
<p align="center"><a href="#screenshots">Screenshots</a> &bull; <a href="#how-does-it-work">How does it work?</a> &bull; <a href="#features">Features</a> &bull; <a href="#download-links">Download Links</a> &bull; <a href="#contributing">Contributing</a> &bull; <a href="#localization">Localization</a> &bull; <a href="#contact">Contact</a> &bull; <a href="#donate">Donate</a> &bull; <a href="#license">License</a></p>
<p align="center"><a href="https://freetubeapp.io/">Website</a> &bull; <a href="https://docs.freetubeapp.io/">Documentation</a> &bull; <a href="https://docs.freetubeapp.io/faq/">FAQ</a> &bull; <a href="https://github.com/FreeTubeApp/FreeTube/discussions">Discussions</a></p>
<hr>

> [!NOTE] 
> FreeTube is currently in Beta. While it should work well for most users, there are still bugs and missing features that need to be addressed.
>
> If you have an idea or if you found a bug, please submit a [GitHub issue](https://github.com/FreeTubeApp/FreeTube/issues/new/choose) so that we can track it.  Please [search the existing issues](https://github.com/FreeTubeApp/FreeTube/issues?q=is%3Aissue+sort%3Arelevance-desc) before submitting to prevent duplicates!

## Screenshots
| The main FreeTube window                                                                         |
|--------------------------------------------------------------------------------------------------|
| ![](https://raw.githubusercontent.com/FreeTubeApp/FreeTubeApp.io/master/src/images/FreeTube1.png)|

| Watching a video                                                                                 |
|--------------------------------------------------------------------------------------------------|
| ![](https://raw.githubusercontent.com/FreeTubeApp/FreeTubeApp.io/master/src/images/FreeTube2.png)|

| Settings                                                                                         |
|--------------------------------------------------------------------------------------------------|
| ![](https://raw.githubusercontent.com/FreeTubeApp/FreeTubeApp.io/master/src/images/FreeTube3.png)|

## How does it work?
FreeTube uses a built in extractor to grab and serve data / videos. The [Invidious API](https://github.com/iv-org/invidious) can also optionally be used. FreeTube does not use any official APIs to obtain data. While YouTube can still see your video requests, it can no
longer track you using cookies or JavaScript. Your subscriptions, playlists and history are stored locally on your computer and never sent out.

> [!IMPORTANT]  
> Using a VPN or Tor is highly recommended to hide your IP while using FreeTube.

## Features
* Watch videos without ads
* Use YouTube without Google tracking you using cookies and JavaScript
* Two extractor APIs to choose from (Built in or Invidious)
* Subscribe to channels without an account
* Connect to an externally setup proxy such as Tor
* View and search your local subscriptions, playlists and history
* Organize your subscriptions into "Profiles" to create a more focused feed
* Export & import subscriptions
* YouTube Trending
* YouTube Chapters
* Most popular videos page based on the set Invidious instance
* SponsorBlock
* DeArrow
* Open videos from your browser directly into FreeTube (with extension)
* Watch videos using an external player
* Full Theme support
* Make a screenshot of a video
* Multiple windows
* Mini Player (Picture-in-Picture)
* Keyboard shortcuts
* Option to show only family friendly content
* Show/hide functionality or elements within the app using the distraction free settings
* View channel posts

### Browser Extensions
The following extensions open YouTube links directly in FreeTube:

- [LibRedirect](https://libredirect.manerakai.com/)
- [RedirectTube](https://github.com/MStankiewiczOfficial/RedirectTube)

LibRedirect automatically redirect YouTube links to FreeTube.
> [!IMPORTANT]
> To ensure proper functionality, select FreeTube as Frontend in the Services settings of the extension.

RedirectTube, doesn’t automatically open YouTube links in FreeTube (although this feature can be enabled in the settings). Instead, it adds buttons to the toolbar and context menu, which you can click to open videos in FreeTube manually.

- Download LibRedirect from [Mozilla Add-ons](https://addons.mozilla.org/firefox/addon/libredirect/) (for Firefox based-browsers) or [developer's website](https://libredirect.manerakai.com/download_chromium.html) (for Chrome and Chromium-based browsers).

- Download RedirectTube from [Mozilla Add-ons](https://addons.mozilla.org/firefox/addon/redirecttube/) (for Firefox based-browsers) or [Chrome Web Store](https://chromewebstore.google.com/detail/redirecttube/jpbaggklodpddjcadlebabhiopjkjfjh) (for Chrome and Chromium-based browsers).

> [!NOTE]
> These extensions do not work on Linux portable builds!
>
> If you have issues with the extension working with FreeTube, please create an issue in this repository instead of the extension repository.

## Download Links
### Official Downloads

> [!CAUTION]
> This fork is supported on Windows 10 and later, macOS 12 and above (including legacy Metal and non-Metal Macs running OCLP), and various Linux distributions. Upstream FreeTube v0.26.0+ dropped macOS 12 and dropped legacy OpenGL GPU acceleration in Chromium 152+.

* [GitHub Releases](https://github.com/FreeTubeApp/FreeTube/releases)

* [FreeTube Website](https://freetubeapp.io/#download)

* Flatpak on Flathub: [Download](https://flathub.org/apps/details/io.freetubeapp.FreeTube) and [Source Code](https://github.com/flathub/io.freetubeapp.FreeTube)

#### Automated Builds (Nightly / Weekly)
> [!WARNING]
> Use these builds at your own risk. These are pre-release versions and are only intended for people that want to test changes early and are willing to accept that things could break from one build to another. 

Builds are automatically created from changes to our development branch via [GitHub Actions](https://github.com/FreeTubeApp/FreeTube/actions?query=workflow%3ABuild).

The first build with a green check mark is the latest build.  

> [!IMPORTANT]
> You will need to have a GitHub account to download these builds.

### Projects maintained by individual FreeTube team members
* Homebrew FreeTube (Apple Silicon only): [Install](https://github.com/PikachuEXE/homebrew-FreeTube)

* FreeTubeAndroid (FreeTube port for Android and PWA): [Download](https://github.com/MarmadileManteater/FreeTubeAndroid/releases) and [Source Code](https://github.com/MarmadileManteater/FreeTubeAndroid)

> [!IMPORTANT]
> These projects are related to FreeTube and are maintained by individual members of the FreeTube team. While they are not part of the main FreeTube project, they may be useful to FreeTube users. There may be issues when using these projects compared to the official builds. Any issues specific to these builds should be reported to their respective maintainers. Make sure you always try an [official download](https://github.com/freetubeapp/freetube/#official-downloads) before reporting your issue to us!

## Contributing
Thank you very much to the [People and Projects](https://docs.freetubeapp.io/credits/) that make FreeTube possible!

If you like to get your hands dirty and want to contribute, we would love to
have your help.  Send a pull request and someone will review your code. 

> [!IMPORTANT]
> Please follow the [Contribution Guidelines](https://github.com/FreeTubeApp/FreeTube/blob/development/CONTRIBUTING.md) before sending your pull request.

## Localization
<a href="https://hosted.weblate.org/engage/free-tube/">
<img src="https://hosted.weblate.org/widgets/free-tube/-/287x66-grey.png" alt="Translation status" />
</a>

We are actively looking for translations!  We use [Weblate](https://hosted.weblate.org/engage/free-tube/) to make it easy for translators to get involved.  Click on the badge above to learn how to get involved.

For the Linux Flatpak, the desktop entry comment string can be translated at our [Flatpak repository](https://github.com/flathub/io.freetubeapp.FreeTube/blob/master/io.freetubeapp.FreeTube.desktop).

## Contact
If you ever have any questions, feel free to ask it on our [Discussions](https://github.com/FreeTubeApp/FreeTube/discussions) page.  Alternatively, you can join our [Matrix Space](https://matrix.to/#/#freetubeapp:matrix.org).  

> [!IMPORTANT]
> Don't forget to check out the [rules](https://docs.freetubeapp.io/community/matrix/) before joining.

## Donate
If you enjoy using FreeTube, you're welcome to leave a donation using the following method.  

* Bitcoin Address: `1Lih7Ho5gnxb1CwPD4o59ss78pwo2T91eS`

While your donations are much appreciated, only donate if you really want to.  Donations are used for keeping the website up and running and eventual code signing costs. 

> [!TIP]
> If you are using the Invidious API then we recommend that you donate to the instance that you use. You can also donate to the [Invidious team](https://invidious.io/donate/) or the [Local API developer](https://github.com/sponsors/LuanRT).

## License
[![GNU AGPLv3 Image](https://www.gnu.org/graphics/agplv3-155x51.png)](https://www.gnu.org/licenses/agpl-3.0.html)  

FreeTube is Free Software: You can use, study share and improve it at your
will. Specifically you can redistribute and/or modify it under the terms of the
[GNU Affero General Public License](https://www.gnu.org/licenses/agpl-3.0.html) as
published by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.  
