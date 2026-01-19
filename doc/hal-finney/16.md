# Re: v0.1.2 debug.log

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Sun, Jan 11, 2009 at 5:25 PM<br>
Subject: Re: v0.1.2 debug.log<br>
To: hal.finney@gmail.com

OK, so no crash or exception window or anything. &nbsp;debug.log is all I need then.

It looks like there's a "select failed: 10038" error (the sockets select function failed) and then network communication goes quiet after that (except for IRC which is still working). &nbsp;I've never had select fail before. &nbsp;It looks like sockets is somehow partially hosed. &nbsp;At least now I know what's wrong now.

You should restart it. It's not doing anything right now. &nbsp;I don't know if it'll just get the "select failed" error again, or be fine for a while.

If I can't think of anything else, I can always shut down and restart sockets if it gets hosed like that. &nbsp;I'm sure everyone who's written an internet app like a browser or p2p app had to slog through all the ways the Internet can trash you. &nbsp;The Internet is a brutal, rough and tumble place.

The issue of bitcoin.exe still running after you close it is a known issue. &nbsp;It does a careful shutdown of everything to be extra safe, in case some important transaction is in progress, but it's completely fine and totally safe to just kill it if it doesn't exit on its own. &nbsp;I'll have to work on figuring out what's getting hung up. &nbsp;I may just have it kill itself after a timeout.

Thanks!

> Hi Satoshi - debug.log attached. When I started 0.1.2 this afternoon, I first quit the previous version which was running. However, 0.1.2 would not start up. Looking at the debug log, it said "Existing instance found". I ran task manager, and found two processes called bitcoin.exe running. I killed them both and started up the new one, and it seemed to run OK. It says at the bottom "3 connections". I haven't tried the debug version, I'm not sure what I would look for.
>
> Hal

---

Source file: finneynakamotoemails.pdf
