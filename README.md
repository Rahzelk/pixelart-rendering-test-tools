# Pixel-Art Rendering Test Tools

A set of **two HTML5 tools** designed to preview pixel-art rendering and animation **before engine implementation**.  
Everything runs **locally** in your browser — no uploads, no servers.

These two tools are also designed to **work together**:
- You can export a **parallax-scrolling background** using Tool #1  
- …then load that exported video into Tool #2 to **animate sprites over it**
- To animate **multiple sprites**, simply use Tool #2 **several times in sequence**, adding one sprite per iteration (overlaying the new output each time)

This workflow allows artists to quickly build **multi-sprite animated previews** on top of parallax backgrounds, without writing any code.

---

# 📌 Tools Overview

1. **[Parallax Scrolling Renderer](#-parallax-scrolling-renderer--2-layers-fgbg)**  
   Generate parallax-style animations (FG/BG) with zone-based scrolling and export to WEBM.

2. **[Sprite Over Background Video](#-sprite-over-background-video-local)**  
   Animate one sprite at a time over a video background.  
   *(Can be used repeatedly to stack multiple sprites and can use exports from Tool #1 as the background.)*

---

# 🎥 Parallax Scrolling Renderer — 2 Layers (FG/BG)

Create **parallax differential scrolling** videos from two images: **Foreground** and **Background**.  
Horizontal scrolling is controlled per **8px zone**, vertical scrolling applies to the whole layer.  
Exports directly to **WebM**, fully offline.

This tool can be used as a **base layer** for Tool #2, allowing artists to place animated sprites on top of the parallax video.

![Demo](./demo/demo-tool1.webp)
---

## ✨ Features

- Two independent layers: **Foreground** and **Background**
- Transparency-aware composition
- **Vertical scroll** per layer; **horizontal zone scroll** (8px bands)
- **Windowed output**: define crop size + window origin
- **Playback**: play/pause toggle + scrub bar
- **WebM export** with on-screen progress and cancel option

---

## 🔧 How It Works

- Vertical speed = applied to whole layer  
- Horizontal speed = defined **per 8px tile band**  
- Zone bands loop seamlessly  
- Exported area = your defined **Window & Output** rectangle  

---

## 🚀 Quick Start

1. Download `Scroll-Parallax-2-layers.html`  
2. Open in Chrome/Edge/Firefox  
3. Load **Background** and/or **Foreground** images 
4. Adjust vertical speeds, zone scrolls, and output window  
5. Preview → Export WEBM  
6. *(Optional)* Use this exported video as the **Background** in Tool #2 to animate sprites over it

---

## 🧭 UI Summary

### Background / Foreground  
- Load image, set vertical speed  
- Optional background color (for BG transparency)  
- Define **zones**: start tile, end tile, horizontal speed  

### Window & Output  
- Output size (W×H)  
- Window origin (X,Y)  
- Preview auto-fit  
- **FPS** and **Number of Frames**  

### Playback & Export  
- Play/Pause  
- Export WebM (forced-stop playback for consistent frames)

---

# 🕹 Sprite Over Background Video (Local)

Overlay a **Sprite (PNG or animated GIF)** on top of a looping **Background video (WEBM)**.  
Move, rotate, and scale the Sprite in real-time, then **record** the composition to WEBM.

![Demo](./demo/demo-tool2.webp)

This tool is fully compatible with **exports from the Parallax Scrolling Renderer**.  
You can:
- Load a parallax animation from Tool #1 as the **Background video**
- Animate a sprite on top of it  
- Export → re-import that new video into the tool  
- Add another sprite  
- Repeat as many times as needed

This creates an easy workflow for building **multi-sprite composite animations** without code.

---

## ✨ Features

- Sprite (**PNG with alpha** or **animated GIF**) over looping WEBM Background    
- Perfect for animating sprites **on top of parallax exports from Tool #1**  
- Use multiple passes to **stack several sprites**  
- Mouse + keyboard controls for precise animation  
- Framerate-independent Sprite motion  
- Accurate clamping inside visible Background area  
- WEBM recording (video + audio when supported)

---

## 🚀 Getting Started

1. Download `Sprite-On-AnimatedBG.html`  
2. Open locally (double-click)  
3. Load your **Background (WEBM)** — including one exported from Tool #1  
4. Load your **Sprite (PNG)**  
5. Animate → Record WEBM  
6. (Optional) Re-import the exported video to **add another sprite** and so on

---

## 🎮 Controls

### Keyboard  
- Move: ← → ↑ ↓  
- Rotate: PageUp / PageDown  

### Mouse  
- Drag: move  
- Wheel: zoom  

---

## 🎥 Recording Notes

- Uses `canvas.captureStream()` + `MediaRecorder`  
- VP9/VP8 WebM depending on browser  
- Adds Background audio when allowed
- Animated **GIF sprites are recorded as animation** when the browser supports **WebCodecs `ImageDecoder`**. If WebCodecs is unavailable, GIF may export as a **static first frame** 
- Output naming: `export-YYYY-MM-DDTHH-MM-SS.webm`

---

# 🌐 Browser Support (Both Tools)

- Best: **Chrome / Edge / Brave / Firefox**  
- Safari: partial or unreliable WebM support  
- Everything is processed **locally**  

---

# 🔒 Privacy

No uploads. All rendering stays in your browser.

---

# 🐛 Troubleshooting

- **Blank export** → try Chrome/Edge  
- **No audio** → Background may lack audio or browser blocked capture  
- **Misaligned Sprite** → ensure browser zoom = 100%  
- **Preview empty** → window origin outside image bounds  

---

# 📝 License

MIT — free to use, modify, distribute.

---

# 🙌 Credits

- Built with plain HTML/CSS/JS  
- Uses `<canvas>`, `<video>`, `MediaRecorder`, and `captureStream()`  
- Developed with the help of ChatGPT  

