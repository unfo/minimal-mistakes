---

title: Performance comparison of a fork-heavy bash script on WSL vs native Linux
date: 2019-07-05 12:35:00.000000000 +03:00
published: true
type: post
excerpt: |-
  I was doing a simple conversion between dataformats in the simplest and fastest way I could: some `sed`, `tr`, `awk` and good ol' `bash` scripts.
  While doing my conversion I was baffled as the nigh one-liner was taking forever on my local machine running in Windows Subsystem for Linux bash prompt.
header:
toc: true
redirect_from: 
  - /latest/
permalink: /articles/performance-comparison-wsl-vs-native-linux/
---

# Performance comparison of a fork-heavy bash script on WSL vs native Linux

I was doing a simple conversion between dataformats in the simplest and fastest way I could: some `sed`, `tr`, `awk` and good ol' `bash` scripts.

While doing my conversion I was baffled as the nigh one-liner was taking forever on my local machine running in Windows Subsystem for Linux bash prompt.

I mean the data itself is not that fat...

## Data I am working with

`$ wc -l rawdata`

```
	2634 rawdata
```

`$ head -n2 rawdata finaldata.csv`

```
	==> rawdata <==
	2017,01,custAAA,white:272,green:36,
	2017,01,custABC,white:61,green:5,yellow:2,

	==> finaldata.csv <==
	2017,01,custAAA,272,36,0,0
	2017,01,custABC,61,5,2,0
```

## Data conversion script: `convert.sh`
```bash
#!/bin/bash

while read line; do
	new_line=$(echo -n $line | cut -f1-3 -d',')
	echo -n $new_line
	for prio in white green yellow red; do
		prio=$(echo $line | grep -Po "$prio:\K(\d+)" || echo 0)
		echo -n ",$prio"
	done
	echo
done

```

And I knew in my gut that although this might not be the optimal, best or even a good way to do the conversion, I knew it should be sufficient to get the job done given the small size of the data.

So something was amiss. From past experience I knew that doing `fork()` code in excess - i.e. the `$(stuff)` here spawning a new subprocess - can hinder the performance of the code significantly, especially if done inside multiple loops.

This is also something I had an inkling of doubt regarding how well WSL bash had been implemented. Previous things like `cygwin` were not forking emulations, but had to spawn threads and thus were less performant than native forks on a native Linux kernel.

So like any proper geek, instead of focusing on the task at hand - the thing why I was doing the conversion of data - I got derailed and followed this rabbit hole which obviously required me to do some benchmarking of WSL vs native Linux.

## Native Linux:

I uploaded my script and data to a nearby Linux server. The server is not an insane number-cruncher with massive amounts of cores or memory, just a regular utility drone with roughly equivalent hardware specs as my laptop.


`$ time cat rawdata | bash convert.sh > finaldata.csv`

```
	real    0m19.365s
	user    0m1.300s
	sys     0m16.850s
```

This is exactly in the ballpark I was picturing given the size of the data and the (lack of) complexity of the conversion. So why did it freeze up on WSL.

## WSL:

As it turns out, it didn't freeze. I was just too trigger-happy with my `Ctrl-C` interrupt...

`$ time cat rawdata | bash convert.sh > finaldata.csv`

```
	real    6m17.960s
	user    0m18.172s
	sys     7m6.125s
```

Holy Terra be blessed, that is long o_____o
