# POV Wand

Persistence-of-vision text app for Dennis's Android phone. Wave the phone side to side in a dark
room and the screen flashes thin vertical slices of text that your eye stitches into a message.
Hosted on GitHub Pages at https://dennisneville.github.io/pov/ and installed as a PWA.

## Files
- `index.html`: the whole app (HTML, CSS, JS in one file, no build step, no dependencies).
- `sw.js`: offline service worker. Network-first for the page, cache-first for icons and manifest.
  Bump `VERSION` in sw.js and `APP_VERSION` in index.html together on every release.
  A new index.html shows up without a bump (network-first), but changed icons or manifest will NOT
  reach installed copies until `VERSION` changes, because they are served from cache.
- `manifest.webmanifest`, `icon-192.png`, `icon-512.png`: install metadata.

## Release process
- GitHub Pages serves the `main` branch, so anything merged to `main` is live within a minute or two.
- Claude works on a feature branch and opens a pull request only when asked. Dennis merges.
- Before merging: bump both version numbers, then check the status line on the phone shows the new version.

## Hard constraints
- Motion sensors (`devicemotion`) only work in a secure context (https or localhost), top-level page.
  They do NOT work from file:// / content:// or inside sandboxed iframes (Google Sites embeds, claude.ai artifacts).
- No native app. Web app only, Chrome on Android. Brightness can't be set from the web; user sets it manually.
- Horizontal sharpness is capped by physics: each frame stays lit while the phone moves, so it smears.
  Roughly refresh rate x time across the text = frames per pass (about 15 to 20 at 120 Hz for a quick wave).
  Vertical rows are cheap; columns are not. The preview's info line estimates columns per frame and warns above ~3.5.

## How it works
- Text rendering: real fonts drawn to an offscreen canvas at 4x oversample, downsampled to an R-row dot grid
  (8 to 48 rows), threshold 0.42, blank columns trimmed. Icons are vector drawings via `:name:` tokens
  (heart, star, smile, note, bolt, sun, arrow, check).
- Swing tracking (`SwingTracker`, between `// BEGIN TRACKER` and `// END TRACKER`):
  - Preferred: gyroscope `rotationRate` (gamma = axis y, alpha = axis z; picks the axis with higher RMS).
    Zero crossings of angular velocity = swing reversals. Sign learned by correlating with accel-derived velocity.
  - Fallback: leaky-integrated lateral acceleration (tau 0.8 s, trapezoidal integration, phase-lead compensation).
  - Each half-swing modelled as a cosine sweep: u = (1 - cos(pi*phi))/2, using the previous half-swing's duration.
  - Swing length estimated from peak velocity: L = 2 * vpeak * T_half / pi.
  - Accuracy from earlier simulation (script not in the repo, so treat as unverified): gyro mode under 1%
    of swing width; accel-only about 3 to 4%. Re-measure before relying on these.
- Drawing: each frame draws every text column the phone passed over since the last frame, each at its true
  offset from screen centre (column pitch = span * L / columns, converted at 160 CSS px per inch).
  Text order is world-left-to-right in both swing directions, so no explicit reversal of slices is needed.
- Long messages: Auto split packs whole words into parts up to "letters per part"; over-long words break by letter;
  "/" forces a break. Parts share one letter height and one column pitch (narrow parts are centred).
  Each part shows for "time per part" seconds, switching only at a swing boundary; idle > 0.8 s restarts at part 1.
- Fixed rhythm mode: no sensors, synthetic cosine swing at a set half-swing time and length.

## Tuning notes (from real-phone testing)
- Sensor check panel on the setup screen is the first diagnostic: source, gyro axis, detection mode,
  accepted/rejected half-swings and why.
- Doubled text = Timing trim. Mirrored text = Flip direction. Text span default 75%; 65 to 85% is the useful range.
- Default 20 rows, condensed bold font, 3 to 6 letters per part reads best.

## Testing
- Serve the folder over localhost first (`python3 -m http.server 8000`, then open http://localhost:8000/).
  Opening index.html as file:// blocks motion sensors and the service worker.
- Headless Chrome via Playwright works (`/usr/bin/google-chrome`). Synthetic motion: dispatch
  `new DeviceMotionEvent('devicemotion', {acceleration:{x}, rotationRate:{gamma}})` at ~60 Hz.
- Tracker can be unit-tested in Node by extracting the code between the TRACKER markers.
- Real verification has to happen on the phone in a dark room.

## Ideas not built yet
In rough priority order (Claude's suggestion, not yet confirmed by Dennis):
- Calibration pattern (single bar + edge markers) to tune Timing trim. Small, and speeds up all other tuning.
- One-direction mode (draw only on left-to-right swings).
- Light-painting photo mode for long-exposure cameras (one slow timed sweep, much higher resolution).
- Image to dot matrix upload.
- Share links with message and settings in the URL.

## Dennis's preferences for this project
- Canadian spelling in UI text. Keep it a single-file app. No paid services.
