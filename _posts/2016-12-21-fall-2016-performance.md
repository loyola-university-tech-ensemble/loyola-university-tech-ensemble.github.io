---
layout: post
title:  "COMP122 Fall 2016 Performance"
date:   2016-12-21 23:50:59 -0600
image: "covers/performance-f16.png"
categories: update
---

During finals week for the Fall 2016 semester, LUTE put on its first public
performance of Terry Riley's [*In C*][inC]. This semester's performers
consisted of our *Introduction to Digital Music* students, who started this
class with varying degrees of technical and musical skill. These students
performed using their own musical instruments that they created in class, which
they controlled using a device they chose. These controllers included gaming
controllers (PS4, Xbox, etc.), smartphones, and MIDI controllers. A few
students opted to play live instruments and processed their output using their
custom software.

![Performance Fall 2016](/images/performance-f16.png)

## Why *In C*?

This was first semester that LUC has offered the *Introduction to Digital
Music* course ([COMP122][comp122]/MUSC122), so there was some necessary
deviation from the original syllabus. Originally students were to decide upon
and execute a final project idea approved by faculty, such as a music
instrument or composition. We felt that a public performance would be a better
demonstration of how the course material applies to the real world, and would
give our work more exposure on campus and beyond.

Once we had struck upon the idea of performing, we needed to either create a
new piece to perform or pick and existing one. We wanted to avoid performing
something weird and esoteric, which is something commonly seen in other laptop
orchestras. *In C* is a perfect choice for laptop orchestras because of its
timeless energy and freedom, and we think that our performance touches upon
what makes this piece special.

![In C Phrases](/images/in-c-phrases.png)

*In C* consists of 53 consecutive musical phrases of varying sizes, performed
by an indefinite number of performers (Terry Riley recommends 35). The piece
begins by one or more performers playing a constant C ostinato in 8th notes,
while the other performers gradually begin to play and repeat the first phrase.

> Patterns are to be played consecutively with each performer having the freedom
> to determine how many times he or she will repeat each pattern before moving on
> to the next. There is no fixed rule as to the number of repetitions a pattern
> may have, however, since performances normally average between 45 minutes and
> an hour and a half, it can be assumed that one would repeat each pattern from
> somewhere between 45 seconds and a minute and a half or longer.
>
> [ ... ]
>
> Each pattern can be played in unison or canonically in any alignment with
> itself or with its neighboring patterns. One of the joys of IN C is the
> interaction of the players in polyrhythmic combinations that spontaneously
> arise between patterns. Some quite fantastic shapes will arise and disintegrate
> as the group moves through the piece when it is properly played.
>
> -- Terry Riley, *In C*

The nature of the piece gives us some flexibility for how the piece should be
performed, for example the constant ostinato can be relegated to software so
our performers can focus on playing the phrases. Not all of our performers
could reliably play the phrases on a conventional instrument like a piano, so
we wrote some supporting software to enable all of our students to play
together.

## Performance Architecture

Each of the students were responsible for creating a software instrument in
[Max][max] that could respond to MIDI note messages. This instrument is
connected to a Max abstraction developed by David Wetzel which triggers the *In
C* phrases (he also had the difficult task of making MIDI sequences for each
phrase, thanks David!). The students were also provided a master patch that enables
communication between performer patches, handling things such as synchronization and
playback status messages.

![In C Player Abstraction](/images/in-c-player-abstraction.png)

The playback status messages are routed to a single machine hosting our custom
[Score Progress][score-progress] app, which was projected onto the wall in
front of the performers. The app shows which performers are playing each
phrase, which is helpful for performance and also demonstrates to the audience
how the piece works. Each number is unique to a particular performer that is
decided prior to performing the piece.

![In C Score Progress](https://github.com/loyola-university-tech-ensemble/in-c-score-progress/raw/master/img/screenshot.png)

## Performance Excerpts

We are currently working on editing together the raw footage from two video sources,
but in the mean time you can view the raw live stream from the link below:

[Live Stream](https://twitter.com/griffin_moe/status/809783128302690304)

[inC]: https://en.wikipedia.org/wiki/In_C
[comp122]: http://courses.cs.luc.edu/html/comp122.html
[max]: https://cycling74.com/products/max/
[score-progress]: https://github.com/loyola-university-tech-ensemble/in-c-score-progress

