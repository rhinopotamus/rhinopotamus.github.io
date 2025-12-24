---
layout: post
title: Using TightVNC in safe mode in Vista SP2
categories:
- Spencer ex San Diego
---

Some time ago, I installed TightVNC on my mom's computer so that I can remote-control it. (There are few things in this world more frustrating than attempting to tech support over the phone with your mom, because you can't even get mad, and if you get mad, you're in trouble.) Well, apparently my mom's computer caught a browser hijacker pretty bad, and I spent a significant amount of time today trying to pry it out of the computer.

Part of this required booting into safe mode, because this was an extra smart browser hijacker that killed any process you tried to open (including and especially cmd.exe, taskmgr.exe and regedit.exe). Unfortunately, even when booting into safe mode with networking, I couldn't figure out how to get TightVNC to work. (I now suspect that there was a solution, but it's hard to figure something out without being able to see the screen.)

So, I googled and googled until my googler was sore, and found this page:
<http://www.thinkjim.com/2008/08/how-to-use-vnc-in-safe-mode.html>
I tried to very carefully talk my mom through the reg hack outlined on this page (boy was this fun!) and once we finally got it all entered in properly, reg complained that the key didn't exist.

$(\*@#\*@^!$!!!!!!!

Well, I found another way around the browser hijacker and eventually annihilated it (I hope! - thanks MBAM!), but then I got to thinking, what if the reg key I'm looking for is just named differently, but still living in the same place? It turns out that this is indeed the case. See, TightVNC's service is not called winvnc.exe - instead, it is called tvnserver.exe.

So. If you are running TightVNC on Vista, and if you've installed it as a service (which I bet you have), and if it is already configured and port-forwarded and otherwise running properly, then all you have to do is issue the following command:
`reg copy hklm\system\CurrentControlSet\services\tvnserver hklm\system\CurrentControlSet\control\safeboot\network\tvnserver /s /f`

I'd like to make it clear that you CAN INDEED use the abbreviation hklm instead of HKEY\_LOCAL\_MACHINE, and that case DOES NOT matter. (These two clarifications would have saved me ... a significant amount of time.)

I'd also like to note that booting into safe mode can be difficult, because sometimes the F8 key just doesn't work, for one reason or another. Also, I couldn't get Bootsafe to work for me. The intelligent thing to do instead is to run msconfig, go under the Boot tab, tick the "Safe boot" box, and make sure that the radio button by "Network" is filled in. Then proceed to reboot, and come up happily in safe mode. When you're done in safe mode, just run msconfig again, untick the safe boot box, and reboot to come back up in regular mode.

I hope that Google indexes this post, and that it saves someone some time and/or beard pigmentation.
