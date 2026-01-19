# Re: Crash in bitcoin 0.1.0

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Sat, Jan 10, 2009 at 7:11 PM<br>
Subject: Re: Crash in bitcoin 0.1.0<br>
To: hal.finney@gmail.com

OK, thanks. &nbsp;The one in bitcoin-0.1.1-exe-dbg.rar is the same build as in bitcoin-0.1.1.rar. &nbsp;I forgot, when you build debug on MSVC, it uses the debug versions of the runtime DLLs, which aren't included with Windows distributions. &nbsp;Actually, MSVC 6.0's runtime (MSVC60.DLL) is the last version that shipped preinstalled on Windows, which is why the continued interest in that ancient version of the compiler. &nbsp;Later Visual C versions can't create a standalone EXE that doesn't require additional runtime packages installed.

I can't use MSVC 6.0 for the release because its optimization of the SHA-256 routines is too slow.

I've attached a copy of the debug runtime DLLs. &nbsp;(They're redistributable)

> Hi Satoshi - The version with the .pdb file did not run for me, I got an error about MSVCP60D.DLL not being found. I imagine this is due to the version incompatibility you were worried about.
>
> The next version, that deleted the questionable line of code and turned off optimization, seems to run fine for me. So the problem may be related to that bit.
>
> Hal

---

Source file: finneynakamotoemails.pdf
