---
title: Ye Olde Linx
layout: single
---

<p>Cisco ASA is a popular firewall platform and there is now a new vulnerability being disclosed by Exodus Intel. The vulnerability is in the IKE (Internet Key Exchange) protocol.</p>
<p>Even though the exploit takes expert knowledge and fine crafting <strong>it can be remotely exploited</strong> to open a privileged session to the ASA device.</p>
<p>via <a href="https://blog.exodusintel.com/2016/01/26/firewall-hacking/">Execute My Packet | Exodus Intelligence</a>.</p>

<hr/>
{% include video id="siV5pr44FAI" provider="youtube" %}
<p>A very nice talk by <a href="https://twitter.com/lgnome" target="_blank">@LGnome</a> on the differences in performance by five different non-cryptographic hash functions: FNV-1A, CRC32, MurMurHash3, XXHash and CityHash32.</p>
<p>Key points:</p>
<ul>
<li>Know your inputs (small data, small variance vs large corpus of random data)</li>
<li>Know your environment (implementation in C vs higher level language)</li>
<li>If you have a standard library hash function, most often just use it and don't roll your own!</li>
</ul>
<p>(via <a href="https://twitter.com/binitamshah/status/699102612608561152" target="_blank">https://twitter.com/binitamshah/status/699102612608561152</a>)</p>

<hr/>

<p>Sources:</p>
<ul>
<li><a href="https://googleonlinesecurity.blogspot.fi/2016/02/cve-2015-7547-glibc-getaddrinfo-stack.html">https://googleonlinesecurity.blogspot.fi/2016/02/cve-2015-7547-glibc-getaddrinfo-stack.html</a></li>
<li><a href="https://sourceware.org/ml/libc-alpha/2016-02/msg00416.html">https://sourceware.org/ml/libc-alpha/2016-02/msg00416.html</a></li>
</ul>
<h2>What?</h2>
<blockquote><p>During upstream review of the public open bug 18665 for glibc, it was<br />
discovered that the bug could lead to a stack-based buffer overflow.</p></blockquote>
<h2>Exploitation</h2>
<blockquote><p>Remote code execution is possible, but not straightforward. It requires bypassing the security mitigations present on the system, such as ASLR</p></blockquote>
<p><a href="https://sourceware.org/ml/libc-alpha/2016-02/msg00416.html" target="_blank">Mitigations</a></p>
<p>- Mitigating factors for UDP include:<br />
- A firewall that drops UDP DNS packets &gt; 512 bytes.<br />
- A local resolver (that drops non-compliant responses).<br />
- Avoid dual A and AAAA queries (avoids buffer management error) e.g.<br />
Do not use AF_UNSPEC.<br />
- No use of `options edns0` in /etc/resolv.conf since EDNS0 allows<br />
responses larger than 512 bytes and can lead to valid DNS responses<br />
that overflow.<br />
- No use of `RES_USE_EDNS0` or `RES_USE_DNSSEC` since they can both<br />
lead to valid large EDNS0-based DNS responses that can overflow.</p>
<p>- Mitigating factors for TCP include:<br />
- Limit all replies to 1024 bytes.</p>

<hr/>

<p><a href="https://graph.no/finger/">https://graph.no/finger/</a></p>
<p>Try it yourself:</p>
{% highlight bash %}finger newyork@graph.no{% endhighlight %}
<p>Very cool! :)</p>
<hr/>
<p>Maciej Cegłowski writes on his blog idlewords <a href="http://idlewords.com/talks/website_obesity.htm">a longish but to the point article on the causes and effects of big web pages</a>.</p>
<p>It starts off to a bit of a rocky start - in my view - with comparing the web site sizes to the literary works of Russian writers, but I don't think the physical comparison of web page sizes to big books is solid enough. But the article gets better and is definitely worth the read.</p>
<p>This topic especially tickles my fancy, since I have for a long time been a proponent of minimalism in "homepage design" and would've liked to make my own web presence on the web as lightweight as possible - preferably static html with little or no Javascript, but this failed due to my time resources =&gt; big CMS and big theme, not fully controlled by me.</p>
<p>One of the biggest things I am a fan of in his post is the fact that I believe ads should be served from the same host as the other contents. Ads should be meaningful to the target audience. Ads should be incorporated into the design in a non-intrusive manner. Ads should optimally be tailored to really help the user find things that are of interest to them.</p>
<p>Alas we do not live in such a world and ad-blockers are a must given the reality of malware ads being served even on big sites - even if usually for brief periods.</p>
<p>Another thing he bemoans is the amount of Javascript and design compromises needed to get a 'one size fits all' (responsive) design. I thoroughly believe that serving customized markup for different categories of devices is a better solution. This is fraught with its own problems of keeping up to date with classifications etc. but it makes for a better end-result as a 2008 Nokia barely-smart-enough-for-internet phone does not need to have the 512kB JS libs since it doesn't even know how to render table and so forth. There are some work-arounds, but I digress.</p>
<p>Go read <a href="http://idlewords.com/talks/website_obesity.htm">The Website Obesity Crisis</a>!</p>
<p>[Or you can <a href="http://www.webdirections.org/blog/the-website-obesity-crisis/">watch his talk (53 mins)</a>]</p>
<hr/>
<p><a href="http://www.nrl.navy.mil/itd/chacs/biblio/sniper-attack-anonymously-deanonymizing-and-disabling-tor-network">The Naval Research Labs has a conference paper to a new type of attack against the Tor Network.</a></p>
<blockquote><p>an adversary may consume a victim relay’s memory by as much as 2187 KiB/s [903 median] while using at most only 92 KiB/s [46 median] of upstream bandwidth. -- a strategic adversary could disable all of the top 20 exit relays in only 29 minutes, thereby reducing Tor’s bandwidth capacity by 35 percent.</p></blockquote>
<hr/>
<p><a href="http://www.nrl.navy.mil/itd/chacs/biblio/sniper-attack-anonymously-deanonymizing-and-disabling-tor-network">The Naval Research Labs has a conference paper to a new type of attack against the Tor Network.</a></p>
<blockquote><p>an adversary may consume a victim relay’s memory by as much as 2187 KiB/s [903 median] while using at most only 92 KiB/s [46 median] of upstream bandwidth. -- a strategic adversary could disable all of the top 20 exit relays in only 29 minutes, thereby reducing Tor’s bandwidth capacity by 35 percent.</p></blockquote>
<hr/>
<p>In <a href="https://slack.engineering/distributed-security-alerting-c89414c992d6#.7fpm7v7eq">Distributed Security Alerting</a> Ryan Huber describes some pitfalls of common security 'best practices' of monitoring systems.</p>
<p>Most of the things he has issues with, I've experienced first-hand in security and sysadmin work in general.</p>
<p>He then explains how at Slack they have a reactive system where the automation asks you whether you just ran some sensitive commands or not and then requires two factor auth to prove that you did. (Or else it escalates.)</p>
<p>This is quite a handy paradigm of monitoring, but I personally have been wanting a way to say to monitoring "so, I'm going to do stuff now and all problems it raises in the next 5 mins are my fault" -- I mean, Nagios sort of has that with scheduled downtime but Nagios is not a security tool.</p>
<p>Maybe my idea of a blanket statement is a bit too naive and might end up masking unintended consequences so reacting to things that actually did happen is a more mature approach.</p>
<hr/>