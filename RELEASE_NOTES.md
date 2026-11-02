# FreeTube v0.26.0 (OCLP & Legacy GPU Edition)

Welcome to the **FreeTube OCLP & Legacy GPU Edition** (`v0.26.0-oclp.1`).

This release is a community fork of FreeTube specifically tailored for Mac users running macOS on older, unsupported hardware using **OpenCore Legacy Patcher (OCLP)**, as well as any legacy systems that lost GPU hardware acceleration in modern Chromium versions.

---

## ⚡ Why This Fork Exists

Starting in **Chromium 152+** (and Electron 44+ in upstream FreeTube v0.26.0), the Chromium project permanently dropped the legacy OpenGL graphics backend on macOS, mandating a strict Metal-only pipeline via ANGLE. 

On older Intel Macs running modern macOS (Ventura, Sonoma, Sequoia) with OpenCore Legacy Patcher root patches:
* The legacy GPU drivers lack compliant Metal 3 support.
* Chromium 152+ fails to initialize the Metal backend, crashing the GPU process or permanently disabling hardware acceleration ("Software only").
* As a result, CPU usage spikes to 100%, causing severe video stuttering, dropped frames on YouTube (VP9/AV1), and sluggish window rendering.

**This release keeps Electron locked to 42.11.18 (Chromium 148 / $\le 151$)**, which retains full OpenGL/ANGLE GPU hardware acceleration and video decoding on legacy hardware, while bringing in **every single feature, bug fix, and extractor update** from upstream FreeTube v0.26.0.

---

## 🚀 Key Improvements in v0.26.0-oclp.1

* **Hardware Acceleration Restored:** Runs on Electron `42.11.18` (Chromium 148.0.7778.280), keeping GPU rendering smooth and CPU temperatures cool on OCLP machines.
* **macOS 12 Monterey Support Retained:** Upstream v0.26.0 raised minimum requirements to macOS 13; this build continues to run on macOS 12 and above.
* **Updated YouTube Extractor:** Includes `youtubei.js ^18.3.0` and `googlevideo ^4.1.1` to resolve recent YouTube stream throttling and playback failures.
* **Shaka Player Upgrade:** Updated to `shaka-player ^5.3.3`, fixing live stream DVR playback and font rendering issues.
* **SponsorBlock Enhancements:** Added SponsorBlock channel exclusions list and improved segment visibility.
* **Invidious Fixes:** Updated default instances list, improved instance switching, and fixed playlist size limits.
* **UI & Stability Polish:** Fixed live chat auto-scrolling, playlist copying, tooltip positioning, and added a player crash recovery button.

---

## 🖥️ Supported Legacy Mac Hardware & GPUs

This build provides hardware graphics acceleration for:

### 1. Intel Integrated Graphics
* **Intel HD Graphics 4000 (Ivy Bridge):**
  * MacBook Pro (13" & 15", Mid 2012 / Late 2012 Retina / Early 2013 Retina)
  * MacBook Air (11" & 13", Mid 2012)
  * Mac mini (Late 2012)
  * iMac (21.5" & 27", Late 2012 / Early 2013)
* **Intel HD Graphics 5000 / Iris 5100 / Iris Pro 5200 (Haswell):**
  * MacBook Pro (13" & 15", Late 2013 / Mid 2014)
  * MacBook Air (11" & 13", Mid 2013 / Early 2014)
  * Mac mini (Late 2014)
  * iMac (21.5", Mid 2014)
* **Intel HD Graphics 6000 / Iris 6100 / Iris Pro 6200 (Broadwell):**
  * MacBook Pro (13", Early 2015)
  * MacBook Air (13", Early 2015 – 2017)
  * iMac (21.5" & 27", Late 2015)
  * MacBook (12", Early 2015)
* **Intel HD Graphics 515 / 530 (Skylake):**
  * MacBook Pro (Late 2016)
  * MacBook (12", Early 2016)
  * iMac (Late 2015)
* **Pre-Metal Intel Legacy (HD 3000 / Sandy Bridge & older):**
  * MacBook Pro (2011), MacBook Air (2011), Mac mini (2011), MacBook (2010)

### 2. NVIDIA Dedicated Graphics
* **NVIDIA Kepler Architecture (GeForce GT 640M, GT 650M, GTX 660M, GTX 675MX, GTX 680MX, GT 750M):**
  * MacBook Pro (15" Retina, Mid 2012 / Early 2013 / Late 2013 / Mid 2014)
  * iMac (21.5" & 27", Late 2012 / Late 2013)
* **Pre-Metal NVIDIA (Tesla / Fermi: GeForce 9400M, 320M, 330M):**
  * MacBook Pro, Mac mini, MacBook (2008–2010)

### 3. AMD / ATI Dedicated Graphics
* **AMD GCN 1st – 3rd Gen (HD 7000 / 8000 series, R9 M290X, M370X, FirePro D300 / D500 / D700):**
  * Mac Pro ("Trash Can", Late 2013)
  * MacBook Pro (15" Retina, Mid 2015)
  * iMac (Retina 5K 27", Late 2014 / Mid 2015)
* **Pre-Metal TeraScale 1 & 2 (Radeon HD 2000–6000 series):**
  * iMac (2007–2011), MacBook Pro (2011), Mac Pro (2008–2012)

---

## 📦 Installation on macOS

1. Download the `freetube-0.26.0-mac-x64.dmg` (for Intel Macs) or `freetube-0.26.0-mac-arm64.dmg` (for Apple Silicon).
2. Open the `.dmg` file and drag **FreeTube** to your **Applications** folder.
3. **First launch:**
   * Because this is a custom community build with an ad-hoc signature, macOS Gatekeeper may prompt on first launch.
   * Right-click (or Control-click) **FreeTube.app** in `/Applications` and select **Open**, then click **Open** in the dialog.
   * Alternatively, you can run in Terminal:
     ```bash
     xattr -cr /Applications/FreeTube.app
     ```
