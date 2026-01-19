# Re: Crash in bitcoin 0.1.0

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Sat, Jan 10, 2009 at 2:59 PM<br>
Subject: Re: Crash in bitcoin 0.1.0<br>
To: hal.finney@gmail.com

I was temporarily able to reproduce the bug and narrowed it down to the "mapAddresses.count" in the following code. &nbsp;It was absolutely the last piece of code to go in and mainly only got tested with the MSVC build. &nbsp;It's not essential and I'm inclined to turn off optimization and delete the section of code until I figure out what's going on.

I'm attaching a dbg exe you can try that deletes the line of code and turns off optimization. &nbsp;I'm not able to reproduce it anymore at the moment.

irc.cpp:<br>
if (pszName[0\] == 'u')<br>
{<br>
&nbsp;&nbsp;&nbsp;&nbsp;CAddress addr;<br>
&nbsp;&nbsp;&nbsp;&nbsp;if (DecodeAddress(pszName, addr))<br>
&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CAddrDB addrdb;<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if (AddAddress(addrdb, addr))<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;printf("new ");<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;else<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// make it try connecting sooner<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CRITICAL_BLOCK(cs_mapAddresses)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if (mapAddresses.count(addr.GetKey()))<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;mapAddresses[addr.GetKey()\].nLastFailed = 0;<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;addr.print();<br>
&nbsp;&nbsp;&nbsp;&nbsp;}<br>
&nbsp;&nbsp;&nbsp;&nbsp;else<br>
&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;printf("decode failed\n");<br>
&nbsp;&nbsp;&nbsp;&nbsp;}<br>
}

> Yes, actually the version with MSVC symbols would be better, that is the one I am using.
>
> I found that if I launched this one from a cygwin shell, it does not crash. But if I launch it from Windows, double-clicking on the file, it does crash similarly to the previous version. However, I am pretty sure that the previous version did crash even when I launched it from cygwin.
>
> I have to go out but I'll leave this version running for a while.
>
> Hal

---

Source file: finneynakamotoemails.pdf
