# Re: Crash in bitcoin 0.1.0

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Sat, Jan 10, 2009 at 11:52 AM<br>
Subject: RE:Crash in bitcoin 0.1.0<br>
To: hal.finney@gmail.com

Normally I would keep the symbols in, but they increased the size of the EXE from 6.5MB to 50MB so I just couldn't justify not stripping them. &nbsp;I guess I made the wrong decision, at least for this early version. &nbsp;I'm kind of surprised there was a crash, I've tested heavily and haven't had an outright exception for a while. &nbsp;Come to think of it, there isn't even an exception print at the end of debug.log. &nbsp;I've been testing on XP SP2, maybe SP3 is something.

I've attached bitcoin.exe with symbols. &nbsp;(gcc symbols for gdb, if you're using MSVC I can send you an MSVC build with symbols)

Thanks for your help!

> Hi Satoshi - I tried running bitcoin.exe from the 0.1.0 package, and it crashed. I am running on an up to date version of XP, SP3. The debug.log output is attached. There was also a file db.log but it was empty.
>
> The crash allowed me to start up a debugger, but there were no symbols. The exception was at address 00930AF7. The displayed call stack was 942316 called by 508936.
>
> When I have a chance, I'll try building it, although it looks like it would take me a while to acquire all the dependencies.
>
> Hal

---

Source file: finneynakamotoemails.pdf
