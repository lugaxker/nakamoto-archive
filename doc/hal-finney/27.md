# Re: disk full

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Sat, Jan 24, 2009 at 4:47 PM<br>
Subject: Re: disk full<br>
To: hal.finney@gmail.com

I hate duplicating code, but the compiler forces us. Copy the body of the function above it, like this:

&nbsp;&nbsp;&nbsp;&nbsp;void insert(iterator it, const_iterator first, const_iterator last)<br>
&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if (it == vch.begin() + nReadPos && last - first <= nReadPos)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// special case for inserting at the front when there's room<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;nReadPos -= (last - first);<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;memcpy(&vch\[nReadPos\], &first\[0\], last - first);<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;else<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;vch.insert(it, first, last);<br>
&nbsp;&nbsp;&nbsp;&nbsp;}

#if !defined(_MSC_VER) || _MSC_VER >= 1300<br>
&nbsp;&nbsp;&nbsp;&nbsp;void insert(iterator it, const char* first, const char* last)<br>
&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if (it == vch.begin() + nReadPos && last - first <= nReadPos)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// special case for inserting at the front when there's room<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;nReadPos -= (last - first);<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;memcpy(&vch\[nReadPos\], &first\[0\], last - first);<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;else<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;vch.insert(it, first, last);<br>
&nbsp;&nbsp;&nbsp;&nbsp;}<br>
#endif

The modified version of serialize.h is attached.

BTW, in my tests, VC8 produced an EXE that would only run on systems that had VC8 installed on them. &nbsp;The error it gives is extremely vague. &nbsp;I think they expect you to install a package during setup, but bitcoin doesn't have a setup.

My testing has been with MSVC 6.0 SP6 and GCC 3.4.5. &nbsp;GCC is the release build. &nbsp;There's nothing wrong with the MSVC 6.0 build other than its optimization of the SHA routines for generating blocks is slow.

Satoshi

---

Source file: finneynakamotoemails.pdf
