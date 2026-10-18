# Chromatic Field

A participatory sound installation by Schack Lindemann.

Visitors scan a QR code, open this page, and tap once. Their phone is assigned
a pitch from the chromatic scale (C4–C6) and fades into a seamless, slowly
breathing tone. Carrying the phone around the room, each visitor becomes one
voice in a chord that sounds different from every spot in the space — and
different for every person.

## How it works

- A single self-contained HTML page; no backend, no dependencies.
- The tone is generated on the fly: an 8-second seamless loop (two slightly
  detuned sines plus a soft octave partial) rendered to a WAV blob.
- Playback uses an HTML audio element, so the sound survives screen lock and
  the iOS mute switch; the page appears on the lock screen via the Media
  Session API.
- A 3-second intro buffer fades the sound in, click-free, before the loop
  takes over.
- Live site: https://schack-lindemann.github.io/chromatic-field/

## Deploy

A GitHub Actions workflow (in `.github/workflows/`) deploys the site to
GitHub Pages automatically on every push to `main`.

## Tuning

- **Note pool**: `POOL` in `index.html` — currently the chromatic scale from
  C4 to C6. Phone speakers can't reproduce much below ~300 Hz, so keep the
  pool in the mid range. A major pentatonic or a single-chord set
  (e.g. Cmaj9) guarantees consonance; the full chromatic embraces dissonance.
- **Fade-in length**: the `T` constant in `makeToneWav`.
- **Loop length / breathing**: the `D` constant and the LFO depth in
  `makeToneWav`.
