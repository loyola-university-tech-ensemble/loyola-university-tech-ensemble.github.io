---
layout: post
title:  "Fall 2016 Launchpad Instrument Teardown"
author: "Griffin Moe"
date:   2016-12-24 23:50:59 -0600
image: "covers/launchpad-action-f16.png"
categories: jekyll update
---

The Novation Launchpad is a MIDI controller designed to be used with Ableton
Live, but is flexible enough for most applications. For our performance of *In
C*, I wanted to build an instrument that could trigger all 53 phrases of the
piece and use the remaining buttons as a simple drum sequencer. The Launchpad's
multi-color LEDs provided enough visual feedback that I only needed to look at
my laptop screen to manually adjust the position of the Score Viewer
application.

For more information about our Fall 2016 performance of Terry Riley's *In C*,
including performance excerpts and details about the piece, check out [this
post][perf].

[perf]: {% post_url 2016-12-21-fall-2016-performance %}

## Inspiration & Design

The Launchpad has an 9x8 grid of buttons which can be addressed by MIDI note
messages, where the pitch value is the particular button and the velocity value
is the color to be set. It also has an additional row of eight buttons
addressable with a sepearate MIDI message type, similar to the grid. Having 80
buttons is more than enough to have an individual button for each *In C*
phrase, so I assigned the top portion of the grid to playing phrases and the
bottom portion for a simple drum sequencer. The tricky part was mapping button
presses to particular functions, which I originally tried doing using modulo
math in an `expr` but conceded to using a `coll` object. For some reason the
first row starts at zero and goes to eight, then each row starts on the next multiple
of sixteen (16, 32, 48, etc.).

Novation provides a really nice set of features for addressing more than one
LED at a time, for example sending a `0x92` followed by a sequence of nine
velocity values will set the colors of the whole top row (this is how I display
the current drum sequences). There is also a SysEx message for displaying ASCII
messages, which I use at the end of the performance to display "Terry Riley's
In C".

Due to time constraints and workload I did not make anything fancy in regards
to sound design. Instead my main instrument is [The Giant][giant], which is a
sampled Klavins piano hosted inside of Native Instrument's Kontakt VST sampler.
This wound up being a good choice to offset the large presence of bright
additive and FM synthesizers. For the drum sequencer I am using a simple
FM-based kick drum and a sampled rimshot I recorded at home.

[giant]: https://www.native-instruments.com/en/products/komplete/keys/the-giant/

## Controls

David Wetzel's player abstraction provides octave and 8th note shift controls,
which I have mapped to the top row of the Launchpad. One particular feature I
am proud of is that the intensity of the octave button color matches the level
of the octave shift. There is also a button toggle for the ostinato, which wound
up being less useful than the velocity control I added to the master patch window:

![Launchpad Master Patch](/images/in-c-launchpad-master.png)

The top six rows of the grid map to a different *In C* phrase, which when
pressed will light green while playing and will turn a dull amber upon
completion. The latter was added to keep track of which phrase was played last,
in case I have to turn away from my rig (credit to David for the idea). The bottom
two rows are the kick drum and rimshot 8th note patterns respectively. Each row
has a ninth button on the right that will clear out the current pattern.

![Launchpad Control Legend](/images/launchpad-legend.png)

## Future Work

There is currently one remaining bug in my logic, where the last played phrase
LED gets wiped whenever the drum sequence is changed. This due to how I render
drum patterns, which uses the rapid LED change feature. To access the bottom
row, I have to move the cursor down six rows which will wipe any LED that is
current lit. Either I need to stop using this feature or I need to include the
state of playback when shifting the cursor.

I have four remaining buttons in the top row that I would like to use for
ostinato strength, and volume for the piano, kick, and rimshot. My plan would
be to use two buttons to increment and decrement volume, and use a third button
to cycle between which setting to change. There is also one last button in the
sixth row, which I might use to toggle phrase looping.

## Download

In the future, we will be putting the instruments we used to perform with in
a GitHub repository. Until then, if you desperately need access to my code I can
send you a zip archive ([me@griffinmoe.com](mailto:me@griffinmoe.com))
