# Piano Lock

A responsive, minimalist lock screen for web projects that uses a playable piano as the passcode interface. Built entirely with pure HTML, CSS, and Vanilla JavaScript—no external dependencies, images, or audio files required.

## The Concept

The **Minimal Piano Lock** reimagines authentication by turning a security gate into a tactile, musical experience. Instead of entering alphanumeric characters, the user provides a "melodic key"—a sequence of notes that must be played in the correct order to trigger the unlock state.

By using the browser's native **Web Audio API**, the project treats the keyboard as a synthesizer, transforming the passive act of entering a password into an active, creative interaction. This design is rooted in the concept of **Gamified Security**, where the interface provides immediate sensory feedback (sound and visual state changes) for every interaction, making the process of unlocking content more engaging and memorable.

---

## Features

- **Zero Dependencies** — No libraries, no frameworks, no audio files. Sound is synthesized dynamically using the browser's native Web Audio API.
- **Responsive Design** — Automatically calculates key widths using Flexbox and percentages. Scales perfectly across desktop and mobile screens without horizontal scrolling.
- **Touch Optimized** — Uses modern `pointerdown` events so keys respond instantly to mouse clicks, finger taps, and styluses without input delay.
- **Setup Mode** — Users can set the length of their passcode (1–10 digits) and record their custom secret melody before locking the site.
- **Minimalist UI** — Pure black-and-white flat design with high-contrast inverted click effects.
- **Real-Time Audio Feedback** — Every key press instantly generates sound through the browser audio engine.
- **Pure Frontend Architecture** — Works fully offline after loading in the browser.

---

## Demo Flow

1. User chooses passcode length.
2. User records a melody using the piano keys.
3. User locks the interface.
4. To unlock, the exact melody must be replayed in the correct sequence.

---

## Quick Start

1. Download or copy the `index.html` file.
2. Open it in any modern browser:
   - Chrome
   - Firefox
   - Edge
   - Safari
3. Record your melody.
4. Click **Lock Site**.
5. Replay the melody to unlock.

---

## How to Implement in Your Project

You can adapt this piano lock to protect:
- Hidden pages
- Secret sections
- Easter eggs
- Internal tools
- Puzzle-based experiences
- Portfolio reveal screens

> **Security Note:**  
> This is a frontend-only lock system. It is suitable for UI gating, interactive experiences, and creative projects, but not for protecting sensitive or private data.

---

## Step 1 — Add the HTML Structure

Wrap your protected content inside a hidden container.

```html
<body>

    <!-- Piano Lock UI -->
    <div id="lock-screen-wrapper">
        <!-- Piano lock interface -->
    </div>

    <!-- Hidden Content -->
    <div id="unlocked-content" style="display:none;">
        <h1>Secret Content</h1>
        <p>This content unlocks after the correct melody.</p>
    </div>

</body>
```

---

## Step 2 — Use a Fixed Passcode (Optional)

If you want all users to use the same melody:

### Remove Setup UI

Delete:

```html
<div id="setup-ui">
    ...
</div>
```

### Set Hardcoded Melody

```javascript
let appState = 'LOCKED';

const secretPasscode = ['C4', 'E4', 'G4', 'C5'];
const passcodeLength = secretPasscode.length;
```

---

## Step 3 — Unlock Logic

Inside `handleInput(note)`:

```javascript
if (currentInput.join(',') === secretPasscode.join(',')) {

    setTimeout(() => {

        document.getElementById('header-container').style.display = 'none';

        document.getElementById('piano-wrapper').style.display = 'none';

        document.getElementById('unlocked-content').style.display = 'block';

        // Custom success logic here

    }, 200);
}
```

---

## Audio System

The project uses the browser's built-in **Web Audio API** to synthesize notes dynamically.

Example oscillator:

```javascript
const osc = audioCtx.createOscillator();

osc.type = 'sine';

osc.frequency.value = frequency;
```

### Available Waveforms

```javascript
'sine'
'triangle'
'square'
'sawtooth'
```

---

## Keyboard Range Customization

Modify these variables:

```javascript
const START_MIDI = 60;
const END_MIDI = 72;
```

### Examples

| Range | Notes |
|---|---|
| `60 → 72` | C4 → C5 (1 Octave) |
| `48 → 72` | C3 → C5 (2 Octaves) |
| `36 → 84` | Large multi-octave keyboard |

---

## Customization Ideas

### Visual Themes

Change:

```css
.white { }
.black { }
```

Ideas:
- Neon synthwave
- Retro terminal green
- Glassmorphism
- Cyberpunk
- Minimal grayscale

---

### Sound Themes

Change oscillator type:

```javascript
osc.type = 'triangle';
```

Possible styles:
- Soft piano
- Retro arcade
- Synthwave
- Chiptune
- Ambient tones

---

### Unlock Effects

Add:
- Confetti
- Fade transitions
- Blur effects
- Sound success chimes
- Hidden animations

---

## Browser Compatibility

| Browser | Supported |
|---|---|
| Chrome | ✅ |
| Edge | ✅ |
| Firefox | ✅ |
| Safari | ✅ |
| Mobile Browsers | ✅ |

---

## Performance

- Lightweight single-file architecture
- No external network requests
- No images or audio assets
- Extremely low memory footprint
- Fast initial load

---

## Possible Use Cases

- Interactive portfolios
- Creative landing pages
- Puzzle games
- ARG projects
- Secret developer panels
- Event invitations
- Music-themed websites
- Easter eggs in apps

---

## Future Improvements

Potential additions:
- MIDI keyboard support
- Recording/exporting melodies
- Multiple user profiles
- Animated visualizer
- Haptic feedback
- LocalStorage persistence
- Multiplayer melody challenge mode

---

## Tech Stack

- HTML5
- CSS3
- Vanilla JavaScript
- Web Audio API

---

## License

MIT License

Free to use, modify, and distribute for personal and commercial projects.
