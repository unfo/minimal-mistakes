---
title: Episode 002 - Awareness, pwning and other tomfoolery
date: 2019-01-21 13:41:07 +02:00
published: true
layout: single
excerpt: Firmware flaw in widely used wifi, Mitre-mapping, and ...
toc: true
---

<pre>2019-01-21</pre>



<hr class="hr-knot" />

## Firmware flaw finding fucks-up friends and foes

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

## Mitre releases initial study of how different EDR products fare against their ATT&amp;CK framework

<figure><img src="/assets/mitre.png"/><br/>
<figcaption>Mitre ATT&amp;CK mapping. Source: Mitre.</figcaption></figure>

Given that the Mitre ATT&CK framework is a fairly good way to map different attack paths and vectors, I really like the effort they have put into modelling different EDR products based on what they can detect.

imho this should be done by the vendors themselves as well. No false advertizing fuckery mind you.


Source: [Mitre](https://attackevals.mitre.org/evaluations.html)


<center>EOF</center>




