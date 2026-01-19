# Crash in bitcoin 0.1.0

From: Hal Finney <hal.finney@gmail.com\> - 2009-01-10 19:13:18<br>
To: Satoshi Nakamoto <satoshi@vistomail.com\><br>
Attachments: debug.log

Hi Satoshi - I tried running bitcoin.exe from the 0.1.0 package, and it crashed. I am running on an up to date version of XP, SP3. The debug.log output is attached. There was also a file db.log but it was empty.

The crash allowed me to start up a debugger, but there were no symbols. The exception was at address 00930AF7. The displayed call stack was 942316 called by 508936.

When I have a chance, I'll try building it, although it looks like it would take me a while to acquire all the dependencies.

Hal

---

Source files: finneynakamotoemails.pdf, bitcoin-list-archive.txt
