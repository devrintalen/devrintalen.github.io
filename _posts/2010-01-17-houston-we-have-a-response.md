---
layout: post
title: Houston, We Have a Response
tags:
- ADB
- adb
- stk500
- worked
status: publish
type: post
published: true
meta:
  _edit_last: '19855582'
---

Last night I got a response from my ADB mouse (I've been using the
mouse since it's easier to probe and, unlike the keyboard, it appears
to be working). In the end, I think it was a combination of my
protocol and hardware that was preventing the response earlier.

First, the protocol: I spent some time trying to get a good trace of
the initial communication between the Apple II (host) and the mouse
(device). I eventually got it, and it was something like this:

1. Host raises data line for some time (a second or so).
2. Host sends a reset pulse (low) for 4ms. The spec indicates this only has to be 3ms, don't know why it's doing it for longer.
3. Data line is set high for 1ms.
4. Host polls device 0 with a TALK command for register 3 (which is the default device identifier register). There is no response.
5. Host waits 1ms, then polls device 1 similarly. Again, no response.
6. Host polls device 2. No response.
7. Host polls device 3. Since the mouse is (by default) located at address 3 it responds with data. I didn't have enough resolution to record what it responds with.

That's as much as I could trace and still have an idea of what was
going on (hooray for logic analyzers!). So, knowing this, I modified
my adb_init() function to keep the line high for 1s, reset for 4ms,
then wait 1ms before polling.

I think the hardware setup I was using was also preventing the device
from responding. Long story short, I was using the STK500 to supply
the data line and a separate power supply for the VCC and GND
lines. To "power up" the system I would turn on the power supply, then
the STK500. I think the timing was thrown off and the mouse wasn't
resetting properly. I ended up using the VTG and GND rails on the STK
to power the mouse so everything came up at the same time, and got the
response!
