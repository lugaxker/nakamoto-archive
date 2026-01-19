# Re: select failed 10038 fix

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Mon, Jan 12, 2009 at 11:59 PM<br>
Subject: Re: select failed 10038 fix<br>
To: hal.finney@gmail.com

Definitely the disk full. &nbsp;I completely put off disk full handling until a later version. &nbsp;Probably about time I did it now.

Well, that's a relief.

Satoshi

> Hi Satoshi - Sorry I have not been able to do more today, this looks like a busy week for me. I started 0.1.3 again under the MSVC debugger this time so if it crashes tonight I may be able to get some more information.
>
> I remember now that last night, my disk filled up. I had downloaded a bunch of the dependencies (boost, etc) with an eye towards trying to build it myself, and my disk was already pretty full. I'm pretty sure this is what caused 0.1.3 to crash. I've attached the debug.log, which also includes some other runs. The error is about 1/3 of the way down and says,
>
> EXCEPTION: NSt8ios_base7failureE<br>
> CAutoFile::read : end of file
>
> Normally this should be a rare occurrence with the large disk sizes people have today.
>
> Hal

---

Source file: finneynakamotoemails.pdf
