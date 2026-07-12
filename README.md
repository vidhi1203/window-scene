# my current view

Compose a little window scene — a view, the weather, some clutter on the sill, a note — and send it to someone. They open the link to closed curtains, tap to draw them open, and the scene comes to life.

**Live:** https://vidhi1203.github.io/window-scene/

## How it works

The whole app is a single static file, `index.html` — no backend, no database, nothing to pay for.

When you hit **Create the link**, the entire design (view, weather, frame, curtains, sill items, hanging extras, ambient sound, any doodle on the glass, and your message) is serialized to JSON, base64-encoded, and packed into the URL after `#w=`. Nothing is ever sent to a server — the link *is* the greeting card. Opening it just decodes that fragment and renders the scene.

This is also why hosting is free: GitHub Pages serves one HTML file, and every visitor's window lives entirely in the link they were sent.

## Features

- **Compose**: tap-to-pick trays for view (meadow, ocean sunset, city night, snowy mountains, rainy hills, starry night, northern lights), weather, frame, curtains, up to 5 sill items, and hanging extras
- **Fog doodle**: draw on the glass with your finger; the recipient watches the strokes appear stroke-by-stroke after the curtains open
- **Touchable scene**: tap the cat (purrs), the candle (blows out/relights), the radio (plays a generated lo-fi loop), the mug (steams more)
- **Ambient sound**: rain, thunderstorm, wind, crickets, birdsong, or a meditation drone — all synthesized live with the Web Audio API, no audio files
- **Reveal**: recipient sees closed curtains first; tapping draws them open over the scene

## Development

It's one file. Open `index.html` directly in a browser, or serve it locally:

```
python3 -m http.server 8000
```

To deploy changes, just commit and push `index.html` to `main` — GitHub Pages rebuilds automatically.

## Stack

Vanilla HTML/CSS/JS. No build step, no dependencies. Scenes are hand-drawn inline SVG; animation is CSS; sound is Web Audio API oscillators and filtered noise.
