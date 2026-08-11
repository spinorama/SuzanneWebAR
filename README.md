# 📐 Suzanne WebAR — Image Tracker

A single-file **WebAR** experience that anchors a UV-grid 3D model onto a printed
image tracker, viewable right in a **mobile browser** (no app install).

**Live link:** https://spinorama.github.io/SuzanneWebAR/

---

## 📱 How to use it

1. Open the link above on your phone in **Chrome (Android)** or **Safari (iOS 15+)**.
2. Tap **Start AR** and **Allow** camera access.
3. Point the camera at the **printed tracker image** (the KOH‑I‑NOOR Drafting Dots box).
4. The Suzanne monkey with a UV grid locks onto the tracker — move the tracker and the
   model follows it in real time. 🎯

> Camera access requires **HTTPS**. GitHub Pages serves the site over HTTPS automatically,
> so the live link works. A plain `file://` or `http://` page will **not** get camera access on mobile.

---

## 🧩 What's inside

- **`webar-tracker.html`** — the entire experience in one self-contained file:
  - Tracker image + UV-grid texture + monkey `OBJ/MTL` are embedded as data URIs.
  - The tracker image is **compiled in-browser** at startup (no separate `.mind` file).
  - AR libraries (A‑Frame + MindAR) load from CDN at runtime.
  - A placeholder **Suzanne** model with two pieces: a visible `Model` (gets the UV grid)
    and a `Tracker_Plane` that is **hidden in AR**.
- **`index.html`** — redirects the bare repo URL to the AR page.

---

## 🔧 Swapping in your own OBJ/MTL

Open `webar-tracker.html` and edit the constants near the top of the `<script>`:

```js
const OBJ_TEXT = `...`;   // paste your OBJ contents (or point obj-model to a hosted URL)
const MTL_TEXT = `...`;   // paste your MTL contents

// Any mesh/material whose name matches this is HIDDEN in AR (your tracker piece):
const HIDE_PATTERN = /tracker/i;   // <- change to match YOUR tracker material name

// Fit the model on the flat marker:
const MODEL_POSITION = "0 0 0.05";
const MODEL_ROTATION = "-90 0 0";  // stands the model up off a flat marker
const MODEL_SCALE    = "0.5 0.5 0.5";
```

---

## 🖨️ Tracker tips for reliable tracking

- Print the tracker **matte**, keep it **flat**, and light it evenly (avoid glare).
- Bigger is better — a larger printed marker tracks from farther away.
- High-contrast, detail-rich images track best.

---

## 🛠️ Enabling GitHub Pages (once)

`Settings → Pages → Build and deployment → Deploy from a branch → main / (root) → Save`.
Wait ~1–2 min; the live URL appears in the Pages panel.
