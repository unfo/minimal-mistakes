---
title: Episode 001 - Let's get the ball rolling
date: 2019-01-16 10:44:07 +01:00
published: true
layout: single
excerpt: scp broken. Using fonts to evade defences. NotPetya an act of war? Certs expiring due to gov't shutdown. And more.
toc: true
---

<pre>2019-01-16</pre>

This is my first bundle of curated links. 

This is new for me, as I am used to sending these out to an internal mailing list of like-minded techies.

So let's see how this goes...

<hr class="hr-knot" />

## Multiple vulns affecting `scp` found and disclosed by F-Secure fellow hax0r Harry Sintonen

Harry is a great guy and an excellent vuln researcher, so I'll just [quote him directly](https://sintonen.fi/advisories/scp-client-multiple-vulnerabilities.txt) (emphasis mine):

> Many scp clients fail to verify if the objects returned by the scp server match those it asked for. This issue **dates back to 1983** and rcp, on which scp is based.

> Malicious scp server can write arbitrary files to scp target directory, change the target directory permissions and to spoof the client output.

Some of the found issues are design problems that can't or *won't* be fixed. 

Best to switch to `sftp` and `rsync` and avoid `scp`.

<hr class="hr-knot" />


## Using webfonts as a substitute cipher

Substitute ciphers are the oldest form of encryption, dating back to Caesar et co. It seems scammers have no issues turning old tricks into a new business advantage. [Proofpoint has a nice article](https://www.proofpoint.com/us/threat-insight/post/phishing-template-uses-fake-fonts-decode-content-and-evade-detection) covering how a phishing campaign dating back at least to May 2018 has been using `woff` web font files to bypass detection.


<figure><img src="/assets/font-cipher.jpg"/><br/>
<figcaption>Alphabet and "The Quick Brown Fox" reveals the substitution. Source: Proofpoint.</figcaption></figure>

Pretty neat trick. Should be handy for red teams as well to make sure defenses get updated too.

<hr class="hr-knot" />

## Insurance company out to prove NotPetya was Russian act of war to avoid $100m bill

[The Register reports on a lawsuit between a large US company and their insurance company.](https://www.theregister.co.uk/2019/01/11/notpetya_insurance_claim/)

The US company says it lost 1700 servers and 24k laptops and wants money from insurance to recoup damages. Insurance company rejected the claim and is now expected to *prove* that it was Russian activity in order to win the case due to:

>exclusion for "hostile or warlike action in time of peace or war" by a "government or sovereign power."

**End scene**. Transition to the studio where *Zurich* is playing final Jeopardy . . .

*Alex, I'll take Attribution for $100 million.*

"This nation--"

-BZZZZZZZT-

*WHAT IS RUSSIA!* 🥳🏆💰💰💰


<span style="font-size: 300%">🤷‍♂️</span>



<hr class="hr-knot" />

## Business email compromise (BEC) had a super year - doubling profits over 2017!

Even discarding the sarcasm, the numbers are quite *ahem* 

```
 ,,﹏﹏﹏)
@(￣ . ￣)@
     ʘ
m/_       _\m <( YUUUGE )
```
As this [Threatpost article on Shipping exec phishing](https://threatpost.com/shipping-execs-whaling/140643/) quotes the FBI:

> In fact, [the FBI says](https://www.ic3.gov/media/2018/180712.aspx) that BEC scams in 2018 resulted in losses of more than $12.5 billion – a more-than-double jump from the losses accrued in 2017, which harbored a $5 billion scam.

One (simplistic) idea I had to combat this:

**Let's stop doing large business over email and attached Excel documents.** And invest in something a tad more robust with potential for more security controls.

Also: Requiring valid digital signatures from within your own organization for internal, sensitive comms is not overwhelmingly difficult for a serious IT org to accomplish.

<hr class="hr-knot" />

## US Gov't shutdown: no funds? no new SSL certs

As [Threatpost](https://threatpost.com/u-s-government-shutdown-leaves-dozens-of-gov-websites-vulnerable/140782/) and [Netcraft](https://news.netcraft.com/archives/2019/01/10/gov-security-falters-during-u-s-shutdown.html) are reporting, several US .gov sites are either inaccessible or only available over unencrypted connections.

The simple reason is that a significant amount of .gov sites have originally acquired and installed certificates at the start of the new year. Mind you, I doubt this is a US Gov't exclusive *modus operandi*.

I'm not going to dwell on the actual shutdown but rather, what can we perhaps learn or change so that in the future we, the collective of all IT peeps, are maybe a bit safer.

**Do not renew your certificates near any well-known holiday or other periods which are known to disrupt working hours or payments.**

This goes for all y'all out there. Get your certs in the middle of quarters or fiscal years!

<hr class="hr-knot" />

## Intel releases fix for vuln that could enable privilege escalation

[The Register reports about Intel patching an issue with SGX](https://www.theregister.co.uk/2019/01/14/intel_patches_sgx_flaw/) (Software Guard Extensions) where the software in charge of managing the hardware security feature is broken.

As this is effectively a new way to escalate privileges, I would offer this to all EDR/MDR providers and red teams as a juicy target.

<center>EOF</center>




