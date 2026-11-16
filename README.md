# POV Wand

Wave your phone in a dark room and write glowing text in the air.

POV Wand is a persistence-of-vision web app. As you swing the phone side to side, the screen flashes thin
vertical slices of a message, timed to where the phone is in the swing. Your eye blends the slices into
readable text that seems to hang in the air.

**Open it:** https://dennisneville.github.io/pov/

## Getting started

1. Open the link above in Chrome on an Android phone.
2. Tap **Install app on this phone** if you want it on your home screen. It works offline once installed.
3. Type your message, pick a colour, and tap **Start**.
4. Turn the screen brightness all the way up (the app can't do this for you).
5. In a dark room, hold the phone upright with the screen facing your audience and wave it side to side
   in smooth, wide, steady arcs.
6. Double-tap the screen (or press Back) to stop.

## Tips

- Short messages read best. 3 to 6 letters at a time works well. Longer messages are split into parts
  automatically and shown one after another. Type `/` to force a break.
- Add icons with `:heart:`, `:star:`, `:smile:`, `:note:`, `:bolt:`, `:sun:`, `:arrow:` or `:check:`.
- First time on a new phone? Open **Calibration** and work through it in order: sensor check, then
  **Flip direction** if the text is mirrored, then **Timing trim** if it looks doubled, then
  **Column width scale**. The − and + buttons make small adjustments easier than dragging.
- Letters too squashed or stretched? Adjust **Text span** (65 to 85% is the useful range) or **Column width scale**.
- No motion sensors, or they aren't working? Switch **Motion** to **Fixed rhythm** and wave in time with it.
- Save settings you like with **Save current as preset**.

## Requirements

- An Android phone with Chrome. An OLED screen works far better than LCD (true black, no glowing
  rectangle), and a high refresh rate screen (90 or 120 Hz) gives sharper text.
- The page must be opened over https (the GitHub Pages link above). Motion sensors don't work if you
  open the file directly or embed the page in another site.

Other phones and browsers may work but haven't been tested.

## How it works

The app reads the gyroscope (or the accelerometer if there's no gyroscope) to detect each change of
direction in your swing, then predicts where the phone will be for every screen refresh. Each refresh
draws the columns of text that belong at that point in the air. Because the screen stays lit while the
phone moves, there's a physical limit on horizontal sharpness, which is why fewer, taller letters look
best.

It's a single HTML file with no build step and no dependencies. See [CLAUDE.md](CLAUDE.md) for
technical notes.
