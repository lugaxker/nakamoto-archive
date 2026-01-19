# select failed 10038 fix

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Sun, Jan 11, 2009 at 9:31 PM<br>
Subject: select failed 10038 fix<br>
To: hal.finney@gmail.com

I believe I've fixed the bug related to "select failed: 10038" (error WSAENOTSOCK). &nbsp;The select error is not a big deal, but it led the communications thread to get blocked on a socket that should have been in non-blocking mode but wasn't. &nbsp;It never came up until now because as long as select never failed, receive would never be called unless there was data.

Without this fix, your node's communication sometimes goes dead. &nbsp;Connections are still made, but no data is passed. &nbsp;Any generated blocks would probably not be accepted since you can't broadcast them and other nodes will leave your branch behind. &nbsp;That's why Generate doesn't run when you're not connected.

This could also have caused bitcoin.exe to fail to exit. &nbsp;There's no reason for shutdown to wait for the com thread, so I made it only wait for the message processing thread. &nbsp;I'll do a more thorough forced shutdown later.

Looks like your node's com thread just now got blocked on this bug again. &nbsp;It went for a few hours this time before it did.

Version 0.1.3 exe attached.

---

Source file: finneynakamotoemails.pdf
