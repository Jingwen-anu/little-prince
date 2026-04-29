# The Little Prince — A Universe of Voices

A QR-code-driven audio companion for the 3D-printed + laser-cut interactive
toy described in the design document. Each of the 11 characters has a tiny
HTML page that plays a short audio clip when scanned.

## What's in this folder

| File | What it is |
|------|------------|
| `index.html` | Hub page — eleven planet cards, tap any to open that character's page |
| `prince.html` | The Little Prince — protagonist of B-612 |
| `rose.html` | The Rose — beloved on B-612 |
| `fox.html` | The Fox — the philosopher friend |
| `pilot.html` | The Pilot — narrator in the desert |
| `snake.html` | The Snake — the silent guide |
| `sheep.html` | The Sheep — the imagined companion |
| `king.html` | The King — ruler of an empty asteroid |
| `vain.html` | The Vain Man — needs constant applause |
| `drunk.html` | The Drunkard — drinks to forget |
| `businessman.html` | The Businessman — counts the stars |
| `lamp.html` | The Lamplighter — keeps a useless ritual |
| `geographer.html` | The Geographer — never leaves his desk |
| `king.mp3` | Audio file (already provided) |

## Audio files needed

Each character page expects a matching audio file in the SAME folder:

```
prince.mp3        rose.mp3        fox.mp3         pilot.mp3
snake.mp3         sheep.mp3       king.mp3        vain.mp3
drunk.mp3         businessman.mp3 lamp.mp3        geographer.mp3
```

**Filename rules:**
- All lowercase
- No spaces, no special characters
- `.mp3` extension (m4a/AAC also works if renamed to `.mp3`)
- Each file under 1 MB ideally (so it loads fast on 4G)

**Recording tips:**
- 20–40 seconds per character
- Record with phone's voice memo app, export as m4a or mp3
- If recording in a noisy room, use the phone's "voice isolation" filter
- Voice should match the character — King = pompous, Fox = warm and slow,
  Drunkard = slurred and sad, etc.

## How to deploy (free)

### Option 1 — GitHub Pages (recommended)

1. Sign up for a free GitHub account
2. Create a new repository named e.g. `little-prince-voices`
3. Upload all the files in this folder (HTML + MP3) to the repo root
4. Settings → Pages → Source: `main` branch → Save
5. Wait 1 minute. Your site is now live at:
   `https://YOUR_USERNAME.github.io/little-prince-voices/`

### Option 2 — Netlify Drop

1. Visit https://app.netlify.com/drop
2. Drag this entire folder into the drop zone
3. Done. You get a URL instantly. No account needed for the basic plan.

## Generating the QR codes

Once your site is live, you'll have URLs like:
```
https://YOUR_USERNAME.github.io/little-prince-voices/king.html
https://YOUR_USERNAME.github.io/little-prince-voices/fox.html
...
```

To turn each URL into a QR code, use a free tool such as:
- **qr-code-generator.com** — single QR codes, no account
- **the-qrcode-generator.com** — supports batch generation from a CSV
- **goqr.me/api/** — programmatic API if you want to script it

**Sizing for printing:**
- Minimum 20mm × 20mm to be reliably scanned by a phone camera
- Leave at least 4mm of white border ("quiet zone") around the code
- For laser engraving onto wood: use grayscale (no halftones), error
  correction level H (highest), and test scan on the actual material first

## How the page behaves

When a child scans the QR code with their phone camera:

1. The phone opens the URL in the default browser
2. The page loads in roughly 1 second on 4G
3. The page tries to autoplay the audio (works on Android Chrome,
   some iOS Safari versions block autoplay — child taps the play
   button instead)
4. Big play/pause button, scrubbable progress bar, time display
5. After audio ends, the play button resets — child can replay
6. "← back to all eleven" link returns to the index hub

## Customizing

Want to change quotes, colors, or character names? Edit `generate.py`
and re-run `python3 generate.py` to regenerate all 12 HTML files at once.

The design intentionally keeps each page lightweight (~15 KB before audio)
so it loads fast and works on older phones. No external dependencies
besides Google Fonts.

---

Designed to accompany the 3D-printed + laser-cut Little Prince Universe
(see `little_prince_design.html` in the parent project).
