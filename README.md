![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/romslf/ultimate-proxy?include_prereleases) 

![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/downloads-pre/romslf/ultimate-proxy/1.1.1.0/total) ![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/downloads-pre/romslf/ultimate-proxy/1.3.2.1/total)

# **Please find a FREE online dashboard [HERE](https://github.com/romslf/Ultimate-Proxy/wiki/Quick-start#online-dashboard-interface)**

# Ultimate-Proxy
Repository for Ultimate Proxy releases, a stratum mining proxy

Developed using Dotnet, it should work on Windows and Linux.


# Preamble

First, I made a poll on r/ethereummining and r/gpumining to know who were using a mining proxy, the results are:

* 3 - Yes
* 20 - No
* 1 - Why not
* 28 - What is it ?

So i'll try to explain briefly what is it and why it was developed.


# What is a proxy ?

A proxy is a computer software that plays the role of intermediary by placing itself between two hosts to facilitate or monitor their exchanges.
So basically every request sent by a client to a server can be recorded and edited, the same with server responses.

Little example (For Ultimate Proxy):
Imagine having to switch 100 rigs to another pool or just want to edit the reward address. By hand, you just can't.

With Ultimate Proxy:
Instead of connecting your rigs to a mining pool, you are going to connect all your rigs to Ultimate Proxy, and proxy to a pool.
From here, Ultimate Proxy will receive all your rigs requests. And will adjust it depending on your proxy config. 

On rigs Authorize request for example, if you enabled it in config, it will replace rigs wallets by the one given in your proxy config, so you can edit all your rigs address/pool in one place.
It can record each accepted/reject shares too.


# So, how can Ultimate Proxy help you ?

Ultimate Proxy aims to be your best friend for mining.

**For now Ultimate Proxy is useful for:**

* Control on which pool you are working on
* Control on which wallet you will be rewarded
* Getting stats of all your rigs in the same place (per rig and total)
* Getting some estimations (For now, the number of shares per minute/hour/day)
* Access the proxy logs as well as the statistics of workers remotely
* Allows a 50% fee reduction of some mining software
* Activate the “ZIL” mode which allow mining ETH/ETC + ZIL
* Record the exact number of mining time of each rig as well of the numbers of reconnections

**To come up ?**

* Optimization of bandwidth
* One worker mode, by letting think that all rigs are a single miner to the pool
* Notifications about defined events
* Current estimated earnings and forecast
* Highly configurable profit switch for coins of same algo
* Different switching strategies between pools (Ex: quota, ping, failover, other?)
* Calculates the accepted hash rate by pools- Your idea ?


# Screenshots

*Those screenshots could be outdated*
[Starting](https://preview.redd.it/yz2znqzb39z51.png?width=978&format=png&auto=webp&s=81390a36176b471072eb40e6bcf1b5468709b712)
[Running](https://preview.redd.it/ak4fuwce39z51.png?width=723&format=png&auto=webp&s=985b5198a04ceedd93d19e1c731a62d4bd666d59)


# Download

[VirusTotal](https://www.virustotal.com/gui/file/83036d1a43b9fb88041bf6a6f96586836e406fdee81065b51a9dec044bc68fc1/detection)

[Download](https://github.com/romslf/Ultimate-Proxy/releases)


# Conclusion

The name is “Ultimate” Proxy, but it's not meant to be the “best” software out there, I just found that name cool, and I'll try to make it work for everyone, that's why its called “Ultimate Proxy”.

I'm not claiming that this program is the best or whatever, I'll let you be the judge.
I hope that you like it and that it will help some of you !

I'll be glad to read your feedbacks !

Keep in mind that this software is in early stage of development.

Don't hesitate to:
* Ask questions
* Report bugs
* Give ideas
* Criticize anything

Thank you for reading all this, and happy mining !
