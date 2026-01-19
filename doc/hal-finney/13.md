# Re: How's v0.1.2 going?

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Sun, Jan 11, 2009 at 4:36 PM<br>
Subject: How's v0.1.2 going?<br>
To: hal.finney@gmail.com

Well this doesn't look good. After you upgraded to 0.1.2, your node responded to one or two messages and then stopped replying to messages. &nbsp;It's still accepting connections and seems to be alive on IRC. &nbsp;That could happen if ThreadSocketHandler or ThreadMessageHandler is hung or crashed or blocked. &nbsp;Usually when there's an exception or other problem, it only stops the affected thread and everything else keeps running.

I'm attaching the msvc debug version in case you need it.

Satoshi

---

Source file: finneynakamotoemails.pdf
