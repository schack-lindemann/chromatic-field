# Chromatic Field

A participatory sound installation by Schack Lindemann.

Visitors scan a QR code, open this page, and tap once. Their phone is assigned
a pitch from the Cmaj9 chord with F♯ and A tensions (C·E·G·B·D plus F♯·A,
across two octaves, C4–D6) and joins a
seamless, slowly breathing tone. Carrying the phone around the room, each
visitor becomes one voice in a chord that sounds different from every spot in
the space — and different for every person.

## How it works

- A single self-contained HTML page; no backend, no dependencies.
- The tone is generated on the fly: an exactly-periodic 8-second loop (two
  slightly detuned sines plus a soft octave partial) rendered to a long WAV
  blob (24 cycles) — the loop wrap is mathematically seamless.
- Playback uses an HTML audio element, so the sound survives screen lock and
  the iOS mute switch; the page appears on the lock screen via the Media
  Session API.
- The sound starts immediately at full voice — no fade-in.
- Live site: https://schack-lindemann.github.io/chromatic-field/

## Deploy

A GitHub Actions workflow (in `.github/workflows/`) deploys the site to
GitHub Pages automatically on every push to `main`.

## Tuning

- **Note pool**: `POOL` in `index.html` — currently the Cmaj9 chord tones
  plus the F♯5 and A5 tensions (C·E·G·B·D·F♯·A, C4–D6). Phone speakers can't
  reproduce much below ~300 Hz, so
  keep the pool in the mid range. A major pentatonic or the full chromatic
  are one-line alternatives.
- **Loop length / breathing**: the `D_LOOP` constant and the LFO depth in
  `makeToneWav`.
