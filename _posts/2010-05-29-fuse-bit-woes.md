---
layout: post
title: Fuse bit woes
tags: []
status: draft
type: post
published: false
meta:
  _edit_last: '19855582'
---

Short version of this: remember to check your fuse bits. Now for the
long version:

Ever since I got this particular Mega32 it's been giving me
issues. The first program I loaded on it just toggled a pin on and
off, so I could make sure the clock was configured correctly. I was
lazy, though, and didn't write it in assembly. So when the toggle
period was longer than I expected, I didn't think much of it. Chalked
it up to poor compiler optization.

Fast forward to the beginning of this project. My first code that
tried to send a packet had really wonky timing. I spent a few nights
getting the AVR libc delay macros to work correctly by changing the
clock speed definition. Eventually I settled on something like 0.98
MHz (which should have been my first clue). Once I did that things
seemed to work right for the most part. I had to spend a fair bit
optimizing the receive code because the chip seemed to be running
slow, but again I thought that was the compiler. Eventually I got
things working.

At this point I needed more debug information than the logic analyzer
could show, so I started to enable the UART. I programmed everything
with (what I thought were) the right values and hit go. Nothing
happened. The Mega32 was spitting out junk. I figured the baud rate
was messed up, and spent a good hour poring over the spec and trying
different baud rates and UART settings, all to no avail. I must have
kept doing this for a good week.

Now, I was pretty ready to tear my hair out. I've worked on more than
my share of AVR-based projects (and STK boards), and there was no
reason that something this basic should have been so difficult. I took
a deep breath, abandoned all my assumptions, and started counting off
what I knew to be true:
