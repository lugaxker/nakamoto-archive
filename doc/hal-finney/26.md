# Re: disk full

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Tue, Jan 13, 2009 at 2:42 PM<br>
Subject: Re: disk full<br>
To: hal.finney@gmail.com

If you build the dependencies, let me know how that goes. &nbsp;Everything is always harder to build on Windows than Linux. &nbsp;I've always hated projects with a lot of big dependencies, but there's no avoiding it, each one is essential.

I still haven't figured out how you managed to get a read exception rather than a write exception when your disk filled up. It's unlikely but maybe possible that the incident could have messed up your block data file. &nbsp;In that case, it might manifest as a similar exception again, or if your block count in the status bar stopped going up, that would also indicate a problem. &nbsp;As of this moment it's at 375 blocks.

If there is a problem, it could easily be solved by deleting your block files, as follows:

(exit Bitcoin and make sure it's stopped)<br>
cd /d "%appdata%\bitcoin"<br>
(backup this directory first)<br>
del blk0001.dat<br>
del blkindex.dat

It'll then re-download the block chain. &nbsp;Your transactions and generated blocks show as 0/unconfirmed until it's done downloading.

The crucial file to backup is wallet.dat. &nbsp;If bitcoin is running then you have to backup the whole %appdata%\bitcoin directory including the database subdirectory, but even if it's not running it certainly feels safer to always backup the whole directory.

The database unfortunately names its files "log.0000000001". &nbsp;To the rest of the world, "log" means delete-at-will, but to database people it means delete-and-lose-everything-in-your-other-files. &nbsp;I tried to put them out of harm's way by putting them in the database subdirectory. &nbsp;Later I'll write code to flush the logs after every wallet change so wallet.dat will be standalone safe almost all the time.

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
