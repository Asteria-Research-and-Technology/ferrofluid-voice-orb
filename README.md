# Ferrofluid Voice Orb

Audio-reactive voice assistant interface. A single-file WebGL prototype ahead of a native macOS build.

Live: https://ferrofluid-voice-orb.vercel.app

## Running it locally

Serve the folder with any static server and open it in a browser:

```
python3 -m http.server 8000
```

The page asks for the microphone right away. Audio is analyzed locally in the browser; nothing is recorded or sent anywhere. If the mic is blocked, double-click anywhere to look around without it.

## Presets

The app opens on Wisp.

1. **Wisp**. Not ferrofluid at all: a soft body of pale light with a blue fringe, drifting between pebble shapes over black, with a little film dust in the air.
2. **Syrup**. Slow and heavy, reluctant to let go.
3. **Crystalline**. Sharp, fast, brittle.
4. **Molten**. Turbulent, always churning.
5. **Orb**. Gathered into a floating body even at rest.
6. **Pool**. Settled low and wide, patient.
7. **Levitate**. Held aloft by the rhythm of speech; when the talking stops it sinks back into the pool.
8. **Mitosis**. The mass keeps dividing, and surface tension keeps drawing it back together.
9. **Sigil**. A shaped magnet that swaps glyphs as you speak.
10. **Baseline**. The reference ferrofluid: a backlit disc, dark fluid, spikes that answer your voice.
11. **Halo**. The wisp in daylight: paper ground, pale blue body, blue rim.

## Controls

Number keys 1 through 9 select presets, 0 selects preset 10, and the arrow keys cycle through all eleven. Space toggles listening. Light flips the room. Controls opens the sliders, and Reset reverts the active preset.

The Fullscreen button (or the F key) clears the room: every control fades away and the orb is left alone in the center. Esc or the corner Exit button brings the interface back.

## How it works

Everything renders in one fragment shader. A CPU simulation drives up to 96 metaballs; the ferrofluid presets shade that field as dark fluid over a backlit disc, and the wisp presets shade the same field as an emissive soft body, using the signed distance to the isoline for the fringe and halo. Voice arrives through a single analyser: three self-normalizing bands, a voice gate, and a spectral-flux onset detector that pushes each syllable into the body as a physical impulse.

## Update notes

**2026-08-28**

- Fullscreen mode: a Fullscreen button in the bar (and the F key) hides the preset rail and the bottom bar, asks the browser for true fullscreen, and leaves the single orb undulating in the center. Esc or the faint Exit chip in the corner restores the interface.
- The cursor stays hidden until the mouse moves, and slips away again after a few still seconds, so nothing sits in the shot.
- Wisp is now the opening preset. It swapped slots with Baseline, which now lives at 10; every preset is still one tap away.

**2026-08-27**

- Added preset 10, Wisp: an emissive soft-body blob in the spirit of a captured glow rather than a liquid. Three overlapping lobes on damped springs shape the silhouette, one with a longer reach so the outline swings between egg, teardrop, and rounded pebble. A chromatic edge (blue reaching furthest out, red pulling furthest in) makes the rim read as a lens fringe, and an inner hot spot wanders on its own.
- Motion pass: quicker tumble, a whisper of random drive in the wobble springs so the surface never sits still, wider lobe travel, and more wander in the whole body.
- Film hiss on the black wisp: sparse white dust specks, re-rolled at 24 fps like a print. Dark version only; the ferrofluid presets and Halo stay clean.
- Added preset 11, Halo: the same body drawn on white with a pale blue interior and a blue rim. On paper a halo cannot add light, so it darkens toward blue instead.
- New shader path behind a style uniform; the ferrofluid render path is untouched.

**2026-08-26**

- First public build: nine ferrofluid presets, one shared shader and simulation, Apache 2.0 license.

## License

Apache 2.0. See [LICENSE](LICENSE).
