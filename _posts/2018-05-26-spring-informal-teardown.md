---
layout: post
title:  "'In C' Informal Reading Tech Teardown (Spring 2018)"
author: "Griffin Moe"
date:   2018-05-25 11:00:00 -0600
image: "covers/modular-spring-2018.png"
categories: update
---

A while back I did a brief [teardown][teardown] of my setup for LUTE's first
performance. In recent performances I have still been using the Launchpad to
trigger phrases and operate a simple drum machine, but now the phrases are
being played off my modular synthesizer. The one minor modification I made to the
Launchpad controller was the addition of a phrase loop, because triggering phrases
while turning knobs and changing patches was hard to manage during rehearsals.

[teardown]: {% post_url 2016-12-26-fall-2016-instruments %}

![Griffin's Modular Synthesizer](/images/modular-spring-2018.jpg)

I changed my patches mid-play but the core signal path was a Mutable
Instruments Plaits macro-oscillator controlled by Expert Sleepers Disting to
(converting MIDI messages from my laptop to Eurorack signals) with dynamic
controls provided by a Make Noise LXD low pass gate. I'm also using a Mutable
Instruments Rings resonator with an Ears contact microphone to ping and accent
phrases. The drum machine was still being played by the laptop rather than the
modular, but in the future that might change!

![Disklavier Piano](/images/player-piano.jpg)

We realized after our first informal 'In C' reading in the Music Hall that the
piano sitting in the background was actually a Yamaha Disklavier, so we knew
that it had to be included in the next performance in that space. Dr. David
Wetzel controlled the Disklavier via MIDI using the unmodified [performance
app][app], using it to play both the ostinato pulse and the 'In C' phrases.

[app]: https://github.com/loyola-university-tech-ensemble/InC
