# Writing in the air with my phone

Most of us have written our name in the air with a sparkler. The light leaves a trail, and for a moment
you can read it. I wondered if a phone could do the same thing with real words. So I built a small app to
find out. It's called POV Wand, and it's free to try.

I had help. An AI assistant called Claude wrote the code. My part was deciding what to build, testing it,
and saying what needed to change. The testing is where most of the work was.

## How it works

Your eyes hold onto light for a split second after it's gone. That's why a sparkler leaves a trail. It's
also why a movie looks smooth, even though it's really a fast series of still pictures.

POV Wand uses the same trick. You type a message and wave the phone from side to side in a dark room. The
phone's motion sensors track where it is in the swing. At each point, the screen lights up only the thin
slice of the message that belongs there. Your eyes blend the slices together, and the word seems to float
in the air. "POV" stands for persistence of vision, which is the name for this effect.

## The catch

A phone screen can only redraw itself so many times a second. In one quick swing, even a fast screen only
gets to draw about 15 to 20 times. That's enough for a short word. It isn't enough for a sentence. If you
squeeze in too much, the letters smear together.

So the app breaks long messages into short pieces. It shows a few letters at a time, then moves on to the
next piece. A birthday message might show "HAPPY" for a few swings, then "BIRTHDAY", then the person's name.

## Finding the right swing

The hardest part wasn't the code. It was learning how to swing the phone.

Finding the right speed took a lot of trial and error. I would change something, go into a dark room, wave
the phone, look at the result and try again.

The biggest step forward came from one setting: how much of the swing the text uses. At the ends of each
swing, the phone slows down, stops and turns around. Letters drawn there come out squashed. When I told
the app to use only the middle of the swing, where the phone moves at a steady speed, the words got much
easier to read. About three quarters of the swing works well.

## Making it easy to use

The first working version did its job, but it wasn't easy to use. The Start button was at the bottom of a
long page. The sliders were tiny and hard to hit with a finger. Settings you only need once were mixed in
with the ones you change every time, like the message and the colour.

So we reorganized the screen. The message and a live preview are now at the top. The Start button stays
pinned to the bottom of the screen, always in reach. The set-once settings have their own section, listed
in the order you'd adjust them. The wand itself works the same as before, but it's much easier to pick up
and use.

That was a good reminder for me. Something can work and still be hard to use, and fixing that is worth
the time.

## Working with AI

Each session with an AI assistant starts fresh. To keep things on track, I kept a short written guide in
the project. It explains what the app does, the rules it has to follow and what I learned from testing.
Claude reads it before making any changes, so lessons from one session carry over to the next.

The split worked well. Claude was quick at writing and fixing code. But it couldn't stand in a dark room
and wave a phone around. Only real testing showed what looked good and what didn't.

## Ways to use it

- A glowing sign at a concert or a game
- A birthday message at a party
- A hands-on science class demo of how our eyes and screens work

## Give it a try

You'll need an Android phone with Chrome. Other phones may work, but I haven't tested them.

1. Open [POV Wand](https://dennisneville.github.io/pov/) in Chrome.
2. Type a short message.
3. Turn your screen brightness all the way up.
4. Go somewhere dark and tap Start.
5. Hold the phone upright with the screen facing your friends, and swing it smoothly from side to side.

If the words look doubled or backwards, the Calibration section has settings to fix that.

The app and all of its code are free on [GitHub](https://github.com/dennisneville/pov). The written guide I
used with Claude is there too, in a file called CLAUDE.md, if you're curious how the project came together.
