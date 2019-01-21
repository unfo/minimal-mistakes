---
title: Episode 002 - Awareness, pwning and other tomfoolery
date: 2019-01-21 23:30:07 +02:00
published: true
layout: single
excerpt: Firmware flaw in widely used wifi, Mitre-mapping, and a very common flaw found in keyboard software
toc: true
---

<pre>2019-01-21</pre>

<hr class="hr-knot" />

## [Firmware flaw finding fucks-up friends and foes](https://www.zdnet.com/article/wifi-firmware-bug-affects-laptops-smartphones-routers-gaming-devices/)

> The researcher says the firmware function to scan for new WiFi networks launches automatically every five minutes, making exploitation trivial. All an attacker has to do is send malformed WiFi packets to any device with a Marvell Avastar WiFi chipset and wait until the function launches, to execute malicious code and take over the device.

So. Trivial exploit over the air.. But surely it's not a widely-used product... right?

* Sony PlayStation 4
* Xbox One
* Microsoft Surface laptops
* Samsung Chromebooks
* Samsung Galaxy J1 smartphones
* Valve SteamLink

<span style="font-size: 300%">🤷‍♂️</span>

Source: [ZDNet](https://www.zdnet.com/article/wifi-firmware-bug-affects-laptops-smartphones-routers-gaming-devices/)

<hr class="hr-knot" />

## [Mitre releases initial study of how different EDR products fare against their ATT&amp;CK framework](https://attackevals.mitre.org/evaluations.html)

<figure><img src="/assets/mitre.png"/><br/>
<figcaption>Mitre ATT&amp;CK mapping. Source: Mitre.</figcaption></figure>

Given that the Mitre ATT&CK framework is a fairly good way to map different attack paths and vectors, I really like the effort they have put into modelling different EDR products based on what they can detect.

imho this should be done by the vendors themselves as well. No false advertizing fuckery mind you.


Source: [Mitre](https://attackevals.mitre.org/evaluations.html)

<hr class="hr-knot" />

## [SpecterOps finds local priv-esc via lax service path permissions](https://posts.specterops.io/razer-synapse-3-elevation-of-privilege-6d2802bd0585)

This is one of those things that is almost a constant when doing Windows host assessments. Things related to builtin components from MS are really robust, so third party vendors are your biggest increase in local attack surface.

SpecterOps - whose Red Team training I participated last year - has a really good blog post about a local priv-esc vulnerability caused by improper directory permissions that effectively allows a low-privileged user to overwrite a registered service's executable.

One fun thing you can do on your own system at home is to run [PowerSploit/PowerUp.ps1](https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1) and see what results you get, as it automates the tedious service and path checks.

**Caveat emptor** as with all tools, you need to understand the results before you take any action. Most common false positive from it relates to a seemingly modifiable `C:\` folder which could in some cases mean you could hijack services under `c:\program files\` by having `program.exe` at the root of `C:\`. Most commonly on modern installations this attack vector doesn't work. So *check yo'self before yo' wreck yo'self*.

Source: [SpecterOps](https://posts.specterops.io/razer-synapse-3-elevation-of-privilege-6d2802bd0585)

<hr class="hr-knot" />

## [Bypassing endpoint detection products](https://medium.com/@fsx30/bypass-edrs-memory-protection-introduction-to-hooking-2efb21acffd6)

So what do you when you get those higher privileges then? Well you want to grab creds from memory and continue pivoting/lateral movement.

To get those creds you most commonly read `lsass.exe`'s memory and get either clear text or hashed creds. That obviously makes it a prime thing for EDR products to keep an eye on. User `@fsx30` on Medium has a good article on how you might go about sneaking around any limitations those EDR products might be putting on you.

*"If you're admin, why not just turn EDR off?!"*

Well... I cannot say this hasn't worked on real gigs, but in most cases shutting down the EDR product itself when the host is still alive is a fairly severe indicator of compromise for the blue team. EDR products in general cause enough events that it is easy enough to figure it out from the lack of noise or other ways of monitoring host state.

Source: [Medium/@fsx30](https://medium.com/@fsx30/bypass-edrs-memory-protection-introduction-to-hooking-2efb21acffd6)

<center>EOF</center>




