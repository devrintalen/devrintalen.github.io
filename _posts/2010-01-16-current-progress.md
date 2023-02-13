---
layout: post
title: Current Progress on ADB
tags:
- ADB
- adb
- avr
- fried
- usb
status: publish
type: post
published: true
meta:
  _edit_last: '19855582'
---

I've been working on this project on and off (mostly off) for a few
months now. My AVR skills were a little rusty getting into this so
I'll use that as an excuse for not making more progress.

I've done a fair bit of research on the Apple Desktop Bus (ADB)
protocol and I'll share what I've found out in another post. My
friends [Chris] and [Ben] and I did a fair bit of work on an [AVR USB
implementation][avr] so that side of things doesn't seem as daunting
to me. I've looked at different AVR microcontrollers and right now the
AT90USB168 seems like a good fit for what I need.

The wall I've run into recently is that the keyboard doesn't appear to
be responding to commands like it used to. I don't know if I've fried
it while doing work—ADB is *not* hot-pluggable—or if my timing
is off, or what. I've [opened an issue][issue] in GitHub to track
it. I also printed some PCBs to probe the bus while the keyboard is
plugged into the old Mac to see if it works then. Photos soon!

[Chris]: http://blog.cdleary.com/
[Ben]: http://benhutton.com/b/
[avr]: http://courses.cit.cornell.edu/eceprojectsland/STUDENTPROJ/2007to2008/blh36_cdl28_dct23/index.html
[issue]: http://github.com/aneviltrend/adbusb/issues#issue/1
