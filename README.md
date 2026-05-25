# OSCILLON by M.B. Parks

**Light & Tone Console, Model 7**

A single-file, browser-based light and sound synthesizer with a mid-twentieth-century laboratory-console aesthetic. Two oscillators, a sub and noise source, an ADSR envelope, a multimode filter, an LFO, and a tape-style echo tank drive both the audio and a full-screen CRT light show. Turning the knobs, throwing the switches, and pressing the keys reshapes the sound and the visuals together, in real time.

Everything lives in one HTML file. There is no build step, no dependencies, and no server. Open it and it runs.

## Features

### Sound engine
- Two oscillators with independent tuning and selectable waveforms (sine, triangle, square, sawtooth).
- A square sub-oscillator one octave down and a white-noise source for added body.
- ADSR amplitude envelope on the keyer, so notes bloom and decay instead of switching abruptly.
- Multimode resonant filter (lowpass, highpass, bandpass) shared across the synth voices and the uploaded audio file.
- LFO routable to pitch (vibrato) or filter (wobble), plus an amplitude tremolo switch.
- Tape-style echo tank with adjustable time, feedback, and mix, and a darkening lowpass in the feedback path.
- Monophonic keyer (on-screen or computer keyboard) with last-note priority.
- Three-channel mix with a shared fader curve, so the synth, microphone, and audio file balance against each other predictably, plus a master Output that scales the whole blend (sound, light show, and recording together).

### Light show
- Full-screen CRT scope with phosphor persistence, scanlines, vignette, and a subtle analog beam jitter.
- Six display modes: waveform, X-Y Lissajous, spectrum bars, radial starburst, circular rose, and a scrolling waterfall spectrogram.
- Beam brightness, glow, and trail length scale with the live signal level. Louder passages bloom and smear longer.
- Trace color tracks both pitch and timbre, so playing up the keyboard sweeps the color.
- Seven color palettes (Phosphor, Amber, Ice Blue, Spectra, Sunset, Violet, Mono).

### Inputs
- **Microphone.** Live voice or instrument input that feeds the filter, echo, light show, and recorder. A separate Monitor switch (off by default) guards against feedback.
- **Audio file.** Upload any audio file the browser can decode. It plays through the full processing chain (filter, LFO, tremolo, and echo), so you can filter-sweep, add vibrato or wobble, and drench an existing track in tape echo while it drives the visuals. A granular playback engine provides independent Speed and Pitch controls: Speed sets tempo from 0.25x to 4x, and Pitch shifts up or down a full octave without changing the tempo. The file also appears in the X-Y Lissajous display alongside the synth. Supports looping and level control.

### Output
- **Performance recorder.** Capture your whole session (oscillators, keyer, microphone, and the loaded file, with all processing baked in) to a downloadable 16-bit stereo WAV file. WAV opens in any editor, DAW, or player with no transcoding. The recording matches what the light show reacts to.

### State and sharing
- Four in-session patch slots for fast A/B comparison.
- Shareable patch links: the full patch encodes into the URL hash, so a sound travels as a link.
- Downloadable patch files (JSON) for a durable local library you own.
- Randomize button for happy accidents.

### Interface
- Full-screen light show with a bottom control dock that slides away after a few idle seconds, leaving a clean screen and a small tab to call it back. The show rescales to sit above the dock when it is open, so controls never overlap the visuals.
- One-tap clean-screen macro plus independent toggles for the grid, on-screen text, and indicator LEDs.
- Knobs respond to vertical drag, mouse wheel, double-click to reset, right-click to reset, and Shift for fine adjustment. Rotary selectors step forward on click and backward on right-click.
- Web MIDI support, so a connected MIDI keyboard plays the instrument.

## Getting started

1. Download `oscillon-synth.html`.
2. Open it in a modern browser (Chrome, Edge, Firefox, or Safari).
3. Throw the **Power** switch to energize the audio engine. Browsers require this first interaction before any sound can play.
4. Leave **Drone** on for a continuous tone, then turn the knobs and watch the screen respond. Or play the keyer.

For the cleanest experience, pick a palette, tap **Clean**, and let the dock auto-hide for an edge-to-edge show.

### A note on running locally

Several features need a secure context to work. Microphone input, audio file reading, and the recorder rely on browser APIs that are restricted in sandboxed previews and on some `file://` setups. If any of these do not respond, serve the file over `http://localhost` instead. A quick option:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000/oscillon-synth.html`.

## Controls reference

| Cluster | Control | Function |
| --- | --- | --- |
| Supply | Power | Energizes the audio engine |
| Supply | Drone | Continuous tone without holding a key |
| Oscillators | Tune A / B | Pitch of each oscillator |
| Oscillators | Wave A / B | Waveform per oscillator |
| Body | Sub | Level of the octave-down sub-oscillator |
| Body | Noise | Level of the noise source |
| Envelope | Attack / Decay / Sustain / Release | Amplitude envelope shape |
| Modulation | LFO / Depth | LFO rate and modulation amount |
| Modulation | Route | LFO destination (off, pitch, filter) |
| Modulation | Trem | Amplitude tremolo |
| Tone & Out | Filter | Filter mode (LP, HP, BP) |
| Tone & Out | Timbre / Reso | Filter cutoff and resonance |
| Tone & Out | Synth / Output | Synth channel level and master output (scales sound, light, and recording) |
| Echo Tank | Time / Feedbk / Mix | Tape-echo delay parameters |
| Voice In | Mic / Monitor / Level | Microphone input, speaker monitor, and level |
| Audio File | Source / Transport / Loop / Speed / Pitch / Level | Load, play/stop, loop, tempo (0.25x-4x), independent pitch (+/- 1 octave), and level |
| Recorder | Capture | Start/stop recording and download the result |
| Screen | Mode | Display mode |
| Screen | Palette | Color scheme |
| Screen | Clean / Grid / Text / LEDs | Screen-element visibility |
| Patch | RND / 1-4 / LINK / SAVE / LOAD | Randomize, slots, share link, save file, load file |

### Keyboard

| Key | Note |
| --- | --- |
| A S D F G H J K | C D E G A C D E (pentatonic plus octave) |

Patch slots: click to recall, Shift-click to store.

## Browser support

Built on the Web Audio API, Canvas, and (optionally) Web MIDI. Works in current versions of Chrome, Edge, Firefox, and Safari. MIDI input requires a browser with Web MIDI (Chrome and Edge). The recorder encodes WAV in plain JavaScript, so it works in any browser with the Web Audio API.

## Privacy

OSCILLON runs entirely in your browser. Audio never leaves your machine. Microphone access is requested only when you switch the microphone on, and recordings are saved straight to your device. There is no server, no analytics, and no network activity.

## Versioning

This project uses simple incremental versioning. The current version is shown in the on-screen marque, the page title, and a changelog comment near the top of the HTML file. See that comment block for the full history.

## License

GPL-3.0
