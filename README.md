# Sony MC-60 Microcassette 3D Web Viewer & Integration Guide

This directory contains everything you need to showcase and post the interactive 3D **Sony MC-60 Microcassette** model on your website.

---

## 📁 File Structure

| File | Purpose |
| :--- | :--- |
| **`viewer_standalone.html`** | **Instant Local Testing** &bull; Fully self-contained with embedded 3D model. Simply **double-click** to open directly in Chrome/Edge without needing any local web server or CORS configuration! |
| **`index.html`** | **Web Deployment Ready** &bull; Lightweight standard web page that loads `sony_mc60.glb`. Upload this and the GLB file to any web hosting. |
| **`sony_mc60.glb`** | **3D Asset** &bull; Optimized glTF 2.0 binary asset (~693 KB) with physical transmission, IOR, roughness, and vector label textures. |

---

## 🚀 How to Post on Your Website

### Option 1: Standard `<model-viewer>` Component (Recommended)
This gives you a responsive, interactive 3D viewer with touch gestures, auto-rotation, and mobile AR:

1. Add Google's `<model-viewer>` script to your HTML `<head>`:
```html
<script type="module" src="https://ajax.googleapis.com/ajax/libs/model-viewer/3.5.0/model-viewer.min.js"></script>
```

2. Place the `<model-viewer>` tag anywhere in your page body:
```html
<model-viewer
  src="sony_mc60.glb"
  alt="Sony MC-60 Microcassette"
  camera-controls
  auto-rotate
  shadow-intensity="1"
  style="width: 100%; height: 500px; background-color: transparent;"
  ar
  ar-modes="webxr scene-viewer quick-look">
</model-viewer>
```

---

### Option 2: Embed via `<iframe>` (WordPress, Webflow, Wix, Squarespace)
If you already have a website builder or CMS:
1. Upload the entire `web_viewer/` folder to your web server, AWS S3, Vercel, or Netlify.
2. In your CMS page editor, add an **Embed / HTML Block** with:
```html
<iframe 
  src="https://yourdomain.com/web_viewer/index.html" 
  width="100%" 
  height="600" 
  style="border: none; border-radius: 16px; overflow: hidden;"
  allow="camera; microphone; xr-spatial-tracking;">
</iframe>
```

---

### Option 3: React / Next.js Integration
Install the library:
```bash
npm install @google/model-viewer
```

Then create a component:
```jsx
import { useEffect } from 'react';

export default function Microcassette3D() {
  useEffect(() => {
    import('@google/model-viewer');
  }, []);

  return (
    <div style={{ width: '100%', height: '550px' }}>
      <model-viewer
        src="/models/sony_mc60.glb"
        alt="Sony MC-60 Microcassette"
        camera-controls
        auto-rotate
        shadow-intensity="1"
        style={{ width: '100%', height: '100%' }}
      />
    </div>
  );
}
```

---

## 📱 Features Included
- **360° Free Orbit Rotation**: Drag on desktop or swipe on mobile/tablet.
- **Smooth Zoom & Pan**: Scroll wheel / pinch-to-zoom right down into the felt pad, leaf spring, and stamped serial number.
- **5 Camera Angle Presets**: Front Face, 3/4 Isometric, Bottom Head Gate, Top Serial Edge, and Rear (Side B).
- **Auto-Rotation**: Graceful turntable presentation that automatically pauses when interacted with.
- **Theme Switcher**: Dark Slate, Clean Studio White, or Transparent (seamlessly blends with your website).
- **Augmented Reality (AR)**: Mobile users on iOS and Android can tap "View in AR" to place the true-to-scale cassette directly in their room.
