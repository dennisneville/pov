# Writing in the air with my phone

I'd seen small hardware gadgets that can write words in the air. They use a strip of LEDs on a wand or a
spinning arm, and as the strip moves, the lights flash in a careful pattern so your eyes see a message
floating in space. My first thought was that a phone should be able to do the same thing. It has a bright
screen and motion sensors, and almost everyone carries one.

I spent a long time looking for an app that did this and never found one, so I decided to build it myself.
The result is POV Wand, a free web app that runs in Chrome on Android.

I could see it being useful in a very large crowd, like a concert or a carnival, where a short word held up
in the air is easier to spot than a waving hand. It could also help someone get noticed in an emergency,
when they need to be seen from a distance in the dark.

## How it works

The effect is called persistence of vision. Your eyes hold onto an image for a split second after it
disappears, which is why a sparkler seems to leave a trail of light behind it.

POV Wand uses the same effect. You type a short message, go somewhere dark and wave the phone from side to
side. The phone's motion sensors work out where it is in each swing, and at every point the screen lights up
only the thin slice of the message that belongs there. Your eyes blend those slices together into a word
that appears to float in the air.

## The main limitation

A phone screen can only redraw itself a limited number of times per second. During one quick swing, even a
fast screen gets about 15 to 20 chances to draw. That's plenty for a short word but not nearly enough for a
full sentence, and if you try to fit in too much, the letters blur together.

To work around this, the app splits longer messages into short pieces and shows them one after another. A
birthday greeting might show "HAPPY" for a few swings, then "BIRTHDAY", then the person's name.

## Getting the swing right

Once the first version worked, most of my time went into learning how to use it well.

Working out how fast to swing the phone took a lot of experimenting. I would change a setting, go into a
dark room, wave the phone, see how it looked and try again.

One setting made a bigger difference than I expected: how much of each swing the text uses. At the ends of
every swing, the phone slows down, stops and reverses, and letters drawn there come out squashed. Limiting
the text to the middle part of the swing, where the phone moves at a fairly steady speed, made the words
much easier to read. About three quarters of the swing works well.

## Making it easier to use

The first working version did its job, but it wasn't easy to use. The Start button sat at the bottom of a
long page, the sliders were small and fiddly on a phone screen, and settings you only need to adjust once
were mixed in with the ones you change every time.

I spent some time reorganizing the screen. The message and a live preview are now at the top, the Start
button stays pinned to the bottom of the screen, and the one-time settings are grouped in their own section
in the order you'd adjust them. The wand itself works the same way, but it's much easier to pick up and
use, and that round of changes was well worth the time.

## Building it with AI

I built POV Wand with Claude, an AI assistant, which wrote the code. My role was to decide what the app
should do, test it, and explain what needed to change.

Each session with an AI assistant starts fresh, so I kept a short written guide in the project. It
describes what the app does, the rules it has to follow and what I've learned from testing. Claude reads it
at the start of each session, so lessons from earlier work carry forward instead of getting lost.

This arrangement worked well. Claude was quick at writing and fixing code, but it couldn't stand in a dark
room and wave a phone around, and real testing was the only way to know what actually looked good.

## Where it could be used

- Helping your group find you in a big crowd at a concert, festival or carnival
- Getting noticed in an emergency at night
- A birthday message at a party
- A hands-on science class demo of how our eyes and screens work

## Give it a try

You'll need an Android phone with Chrome. Other phones may work, but I haven't tested them.

1. Open [POV Wand](https://dennisneville.github.io/pov/) in Chrome.
2. Type a short message.
3. Turn your screen brightness all the way up.
4. Go somewhere dark and tap Start.
5. Hold the phone upright with the screen facing the people watching, and swing it smoothly from side to side.

If the words look doubled or backwards, the Calibration section has settings to fix that.

The app and its code are free on [GitHub](https://github.com/dennisneville/pov). The written guide I used
with Claude is there too, in a file called CLAUDE.md, if you'd like to see how the project came together.
