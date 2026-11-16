# Writing in the Air With My Phone

I'd seen small LED gadgets that write words in the air. A strip of lights on a wand or a spinning arm
flashes in a careful pattern as it moves, and your eyes see a message floating in space. My first thought
was that my phone should be able to do this. It has a bright screen and motion sensors, and almost everyone
has one in their pocket.

So I went looking for an app. I looked for a long time and never found one. Eventually I decided to build
it myself.

The result is POV Wand, a free web app that runs in Chrome on Android. It's a fun toy, but I think it could
also be genuinely useful. In a huge crowd at a concert or a carnival, a short glowing word held up in the
air is a lot easier to spot than a waving arm. And in an emergency, it could help someone get noticed from a
distance in the dark.

## So How Does It Work?

It's built on an effect called persistence of vision. Your eyes hold onto an image for a split second after
it's gone, which is why a sparkler seems to leave a trail of light behind it.

POV Wand uses the same trick. You type a short message, go somewhere dark and wave the phone from side to
side. The phone's motion sensors work out where it is in each swing, and at every point the screen lights
up only the thin slice of the message that belongs there. Your eyes blend those slices together, and the
word appears to float in the air.

## The Catch

A phone screen can only redraw itself so many times per second. During one quick swing, even a fast screen
gets about 15 to 20 chances to draw. That's plenty for a short word, but nowhere near enough for a sentence.
Try to squeeze in too much and the letters smear together.

The workaround is to split longer messages into short pieces and show them one after another. A birthday
greeting might show "HAPPY" for a few swings, then "BIRTHDAY", then the person's name.

## Learning to Swing

Having a working version was only the start. Figuring out how fast to swing the phone took a lot of
experimenting. Change a setting, go into a dark room, wave the phone, squint at the result, repeat.

The setting that helped most was how much of each swing the text uses. At the ends of every swing, the
phone slows down, stops and reverses, and anything drawn there comes out squashed. Keeping the text to the
middle of the swing, where the phone moves at a fairly steady speed, made the words much easier to read.
About three quarters of the swing seems to be the sweet spot.

## Making It Easier to Use

The first working version did its job, but it wasn't much fun to use. The Start button was at the bottom of
a long page, the sliders were tiny on a phone screen, and the settings you only touch once were mixed in
with the ones you change every time.

So I spent a round reorganizing it. The message and a live preview are now at the top, the Start button
stays pinned to the bottom of the screen, and the one-time settings have their own section, listed in the
order you'd adjust them. The wand itself works exactly the same, but it's much easier to pick up and use. To
me, that round of changes was one of the most valuable parts of the project.

## Building It With AI

Full disclosure: I didn't write the code. Claude, an AI assistant, did. My job was to decide what the app
should do, test it, and explain what needed to change.

Each session with an AI assistant starts from scratch, so I kept a short written guide in the project. It
describes what the app does, the rules it has to follow and what I've learned from testing. Claude reads it
at the start of every session, so lessons from earlier work don't get lost.

The split worked well. Claude was fast at writing and fixing code, but it couldn't stand in a dark room and
wave a phone around. Only real testing could tell me what actually looked good.

## Where Could You Use It?

- Helping your friends find you in a big crowd at a concert, festival or carnival
- Getting noticed in an emergency at night
- A birthday message at a party
- A hands-on science class demo of how our eyes and screens work

## Give It a Try

You'll need an Android phone with Chrome. Other phones might work, but I haven't tested them.

1. Open [POV Wand](https://dennisneville.github.io/pov/) in Chrome.
2. Type a short message.
3. Turn your screen brightness all the way up.
4. Go somewhere dark and tap Start.
5. Hold the phone upright with the screen facing the people watching, and swing it smoothly from side to side.

If the words look doubled or backwards, the Calibration section has settings to fix that.

The app and all of its code are free on [GitHub](https://github.com/dennisneville/pov). The guide I used
with Claude is there too (it's the file called CLAUDE.md), if you're curious how it all came together.
