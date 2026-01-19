# v0.1.2 gcc debug build attached

From: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Date: Sun, Jan 11, 2009 at 4:49 PM<br>
Subject: v0.1.2 gcc debug build attached<br>
To: hal.finney@gmail.com

Could you send me your debug.log?

The gcc debug version is attached.

gdb is easier to use than you'd think. gdb.exe is the only file. You run<br>
gdb bitcoin.exe<br>
then type "run"<br>
then if it crashes, type "backtrace" for a stack dump, or it may do it automatically. &nbsp;(The stack trace doesn't always go far enough back unfortunately)

---

Source file: finneynakamotoemails.pdf