# Re: select failed 10038 fix

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Mon, Jan 12, 2009 at 8:41 AM<br>
Subject: Re: select failed 10038 fix<br>
To: hal.finney@gmail.com

It definitely looks like 0.1.3 solved it. &nbsp;It was getting so there were so many zombie nodes, I was having a hard time getting a reply to any of my messages. &nbsp;Now, four inventory messages go out, four getdata messages come back.

Did you get any "not accepted" blocks? &nbsp;The connectivity bug could have caused a generated block not to be accepted if the node wasn't able to broadcast at the time. &nbsp;Once the status is above 5 or so it's safely accepted.

Unfortunately, I can't receive incoming connections from where I am, which has made things more difficult. &nbsp;Your node receiving incoming connections was the main thing keeping the network going the first day or two.

You can send to my Bitcoin address if you want to, but you won't get to see the full transfer sequence:<br>
1NSwywA5Dvuyw89sfs3oLPvLiDNGf48cPD

You could always findstr /c:"version message" debug.log and send a test to some random person you're connected to near the end of the list. &nbsp;The ones ending in port 8333 can receive connections.

I just thought of something. &nbsp;Eventually there'll be some interest in brute force scanning bitcoin addresses to find one with the first few characters customized to your name, kind of like getting a phone number that spells out something. &nbsp;Just by chance I have my initials.

Satoshi

>Thanks, Satoshi, this new version seems to be running much better. I've got 8 connections, and watching debug.log there seems to be quite a bit of activity. I see you sent me a payment, thanks! Let me know your address and I will try sending one to you. I managed to generate a block yesterday and the coins are about to mature, if I understand it correctly.
>
>Hal

---

Source file: finneynakamotoemails.pdf
