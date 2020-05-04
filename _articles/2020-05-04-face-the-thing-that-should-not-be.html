---

title: Face the thing that should not be, 
date: 2020-05-04 17:21:00.000000000 +03:00
published: true
type: post
excerpt: |-
  Prompted by a recent tweet requesting to share early career mistakes, I decided to reply with a bit more detail than what can fit in a single tweet. I hope this can alleviate impostor syndrome at least in a single person!
header: 
toc: true
redirect_from: 
  - /latest/
permalink: /articles/face-the-thing-that-should-not-be/
---

# Face the thing that should not be

Twitter user <a href="https://twitter.com/ElleArmageddon/status/1255870742727585792">@ElleArmageddon had an excellent tweet</a> on a very dear topic: displaying your personal vulnerabilities.

> This is your unscheduled reminder that telling early-in-career engineers stories of times you messed something up real bad is a good way to help them combat their own impostor syndrome.
 
As a life-long professional of <a href="/articles/take-account-of-your-impostor-syndrome">impostor syndrome</a>, I am *all* for alleviating it in others if in any way possible.

Instead of going for short tweet-length responses, I wanted to take this as an opportunity to write the first post in 1,5 years.

Not all of these are *real bad* fails in the big picture, but at the time they felt real bad.

## Physical damage

I had a personal computer which stopped working and failed to boot. There were no beeps from the beeper, no indicators as to what broke. I had effectively two options: either the processor or the motherboard was the problem.

If the motherboard is the issue and I replace the CPU then I would have bought a new processor for nothing and still had to fix the motherboard, and vice versa.

My friend had the exact same CPU family so the sockets were compatible and I asked them to come over with their processor. I figured if the computer booted then I'd know it is a CPU issue and I can just buy a CPU. If the computer doesn't boot then it is a motherboard issue.

This way I'd eliminate the need to buy extra parts because of a wrong guess.

I was not *totally* wrong, just not correct either.

I inserted the CPU to the socket and it failed to boot. Great. Problem debugged => motherboard is the problem. I thanked my friend and they left. Half an hour later they called that their computer won't boot.

My motherboard had fried their CPU. Whether it was a heating issue or a short circuit or what, we don't know, but the fact is that my actions had destroyed their CPU that they had borrowed me out of trust.

Instead of saving money, I now had to replace my motherboard, my CPU and my friend's CPU. At the time I had money for 1,5 components not all three.

## Network issues

I will start by setting aside all of the times when the network cable simply has not been plugged in or has been the wrong type of cable (straight or crossover) etc. There are dozens of these cases where I am the culprit.

But I will instead focus on the cases where I have unwittingly cut network connectivity at the office / in production due to misunderstanding, or more commonly, not thinking things through.

### Case: Firewall default DENY ALL

Fool me once, shame on you; fool me twice, shame on me; fool me (n where n > 1), #feelsbadman.

***Principle of network access control***: everything is forbidden which is not explictly permitted. 

In other words: whitelists > blacklists.

One way to build your firewall rules is to add your `ACCEPT` rules then as the last rule `REJECT ANY ANY` i.e. all other traffic after this rule has been read, is now denied.

Then you add some new `ACCEPT` rules and they don't work. What the hell?! After a few moments of pondering you remember that you inserted them *after* the last final reject i.e. these rules are not being processed any more.

So two things can happen (and have happened to me):
1. you remove the REJECT line to append it to the end *but forget to do it* because the problem you are debugging is taking so long even if the firewall rule is now permitting traffic.
1. you remember that you could add a _default policy_ to reject instead of having it as an explicit rule.

So the first one already has the issue defined: I forgot to re-add the REJECT line and suddenly the firewall is not blocking all that much and for a while I exposed sensitive services to the public internet. 

Yes I could have removed the ACCEPT and then just insert it it *before* the REJECT. Yes. That would've been the smart thing to do.

The second seems like and *is* a good idea overall. It is more secure as it is a fail-secure alternative. But it doesn't mean it cannot bite you (me) in the ass.

A few years after accumulating different exceptions (ALLOWs) in your office network and you want to do some spring cleaning.

Let's start fresh, you say.

```
# iptablesh -F
  --flush   -F [chain]		Delete all rules in  chain or all chains
```

This works perfectly. I tested it on `localhost` before production and no syntax errors. So it's safe, right?! RIGHT?!

But when you are doing this on your server/network device *over ssh* it quite quickly teaches you what *fail secure* means as it will effectively disconnect all your connections (because default deny) and will require physical access to the computer. When the device is not located at your own office, this becomes quite quite painful.

The longest physical distance, I've done this is ca. 1000 km away and we had to order a local IT vendor at the target city to come to our aid.

Also a variant version of this is when your boot sequence reads your iptables rules from config but the config file has been corrupted and now you are back with a default deny and no valid rules. Fun times!

## General sysadmin snafus

### That time when I learned two things at once

It was early stages of my IT career. It was the week of Microsoft patches. I was planning on installing the patches the following Monday after I had - with due diligence - tested the updates in a _test_ environment over the weekend.

It was Friday. I was inexperienced, unscarred. I started the installation process. I quickly realized I had accidentally started operating system updates on a Friday afternoon in production by mistake. We had paying clients and I just created an unannounced, unplanned outage because I had made a typo in the server name when connecting.

Lesson #1: read-only Fridays, i.e. no changes were allowed that could come bite you in the arse over the weekend.

Lesson #2: make it _super_ obvious if you are currently administrating an active, production server. Like a red background, red borders on the window, super obnoxiously loud and obvious that you are in production.

### That time when I didn't actually learn that one thing.

It was another week, another year, another job with operating system updates. Again in an environment where the distinction between production, staging, development server naming is very very minute.

In normal sysadmin fashion, am in fire-fighting/debugging mode trying to figure out the current problem. Client has severe issues with DB performance so we need to grab a copy of the prod db and bring it up in test to run performance-heavy and potentially destructive maintenance on it to see where the hiccup is.

Given that I need to access both production and the test environment to perform the transfer of large amounts of data, I had _several_ ssh sessions and `screen`s open.

And I managed to *shutdown* the production database. No not just the single client's single db. The entire cluster of databases containing DBs for multiple clients. Why? Because I did not notice I was typing in the wrong shell because it was just your regular black-n-white `user@host:/work/temp` type PS1 prompt.

In fact, I had _not_ learned the lesson #2 from above. Thankfully I had not destroyed any data, but I can tell you that I did create quiiiite a big impact on our SLA percentage since we're talking about a hefty DB setup, it took quite a while to first shutdown completely and safely and then start up again. 

All the while I am panicking there trying quicken the process by screaming internally at the screen as my colleagues are waiting for my signal that they can let their clients know that things are back up again.

After that, I made sure every single place I have ever had remote admins to again had very clear markings of BEWARE THIS IS PRODUCTION.

### That time when I accidentally hosted 0.5TB of German warez by accident

Again, fairly early on in my IT career I was admin of a shared hosting platform. Some clients needed the ability to transfer large amounts of data to their website / extranet type of site and uploading via HTTP forms was suboptimal.

Obvious case was to enable FTP access to only a select few accounts. So I created the ftp account for the client and setup a new ftp server instance for their specific user account and their specific upload folder. All is well, I tested the account and checked that I could login and upload files.

The next day I am contacted by our own infrastructure/server provider. You are critically low on storage. Do you want us to add more?

Hmmm sure... wait... what?!

This was a fairly new server that only housed a handful of clients. There shouldn't be any reason for there to be disk space issues.

So I went and did some investigating - babby's first incident response, even if I didn't understand it at the time.

Indeed most of the 600 GB disk was hogged down somewhere. It was the usual top level folder under which the FTP sites resided. But using file explorer I could not find anything that was responsible for it.

I opened cmd prompt and did a quick `dir /s/b` to get a file listing and then the screen filled with quite the collection of German language movies - both adult and not - as well as, apparently, cracked versions of Microsoft products etc.

I had been pwned. HALP!

After a quick check I found I had, by mistake, enabled *anonymous ftp use* and some warez group had found our public facing, no auth server and had decided to take advantage of it. They had created folders with special unicode chars that prevented me from seeing it in the directory listing - or at least accessing it, I can't recall which.

Immediate step: stop the FTP site, disable FTP anonymous access.

Try to calm down. Talk to my boss, then finally document what had happened with screenshots and logfiles to contact the local law enforcement, because I had unwittingly made our public IP address a hoster for illegal files. Welp!

## How about you?

Et tu, Brute?

Contribute to the tweets on the Twitters or your blog or your tiktok or whatever media you want to use.