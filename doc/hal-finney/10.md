# Re: Crash in bitcoin 0.1.0

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Sat, Jan 10, 2009 at 6:55 PM<br>
Subject: Re: Crash in bitcoin 0.1.0<br>
To: hal.finney@gmail.com

I isolated the problem. &nbsp;If I spawn a thread and do mapAddresses.count, even as the very first thing in the program, it segfaults. &nbsp;The workaround is to needlessly call mapAddresses.count in the main thread once and it's fine from then on. &nbsp;I hate to blame the compiler, and I've never had a GCC compiler bug before, but this feels like one. &nbsp;Maybe some bit of init code it tries to optimize out if it's not called at least once in the same thread, or some STL optimization that's not thread friendly. &nbsp;I'm really dismayed to have this botch up the release after all that stress testing.

The attached file: bitcoin-0.1.1.rar (filesize 2,132,686) is the version where I deleted the mapAddresses.count line, and that should be the safest version. &nbsp;(that was the only use of mapAddresses.count) &nbsp;If you could try this version and confirm that the crash is fixed, I'd appreciate it.

Thanks,<br>
Satoshi

---

Source file: finneynakamotoemails.pdf
