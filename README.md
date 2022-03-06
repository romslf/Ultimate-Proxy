![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/romslf/ultimate-proxy?include_prereleases) 

![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/downloads-pre/romslf/ultimate-proxy/1.1.1.0/total)
![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/downloads-pre/romslf/ultimate-proxy/1.3.2.1/total)
![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/downloads-pre/romslf/ultimate-proxy/1.4.2.1/total)
![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/downloads-pre/romslf/ultimate-proxy/1.4.3.1/total)
![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/downloads-pre/romslf/ultimate-proxy/1.4.4.1/total)

# **Please find a FREE online dashboard [HERE](https://github.com/romslf/Ultimate-Proxy/wiki/quick-start#online-dashboard-interface-from-v1321)**

## [Documentation](https://github.com/romslf/Ultimate-Proxy/wiki)
## [Discord](https://discord.gg/zWsTZXBYYq)
# Ultimate-Proxy

Repository for Ultimate Proxy releases, a multi platform stratum mining proxy

# What is a proxy ?

A proxy is a computer software that plays the role of intermediary by placing itself between two hosts to facilitate or monitor their exchanges.
So basically every request sent by a client to a server can be recorded and edited, the same with server responses.

Little example (For Ultimate Proxy):
Imagine having to switch 100 rigs to another pool or just want to edit the reward address. By hand, you just can't.

With Ultimate Proxy:
Instead of connecting your rigs to a mining pool, you are going to connect all your rigs to Ultimate Proxy, and proxy to a pool.
From here, Ultimate Proxy will receive all your rigs requests. And will adjust it depending on your proxy config. 

**The best part is that it subscribre once for jobs and broacast them to all connected workers.
This lead to a huge bandwitch usage reduction, and a more stable job distributions along all miners, wich can increase profitability on a long run.**


# So, how can Ultimate Proxy help you ?

Ultimate Proxy aims to be your best friend for mining.

**For now Ultimate Proxy is useful for:**

* Huge bandwidth optimisation
* Switch between pools
* Control on which pool you are working on
* Control on which wallet you will be rewarded
* Getting stats of all your rigs in the same place (per rig and total)
* Getting some estimations (Estimate/Calculated hashrate, number of shares per minute/hour/day)
* Access the proxy logs as well as the statistics of workers remotely
* Allows fee supression of some mining software
* Record the exact number of mining time of each rig as well of the numbers of reconnections

# Non-exhaustive list of compatible services

### Mining softwares

- [Teamredminer](https://github.com/todxx/teamredminer) (You can add `--eth_hash_report on`, it will enable hashrate reporting)
- [LolMiner](https://github.com/Lolliedieb/lolMiner-releases) (Without any arguments)
- [PhoenixMiner](https://bitcointalk.org/index.php?topic=2647654.0) (Need `-proto 4` argument)
- [Gminer](https://github.com/develsoftware/GMinerRelease) (Need `--proto stratum` argument)

### Pools

Ethash
- [2miners](https://2miners.com)
- [Crazypool](https://crazypool.org/)
- [Flexpool](https://www.flexpool.io/) (Using port 4444)
- [Prohashing](https://prohashing.com/)
- [Woolypooly](https://woolypooly.com/)
- [Unmineable](https://unmineable.com/)

Ton
- [Icemining](https:/icemining.ca)
- [TonWhales](https://tonwhales.com/)

# Screenshots

*Those screenshots are outdated*
[Starting](https://preview.redd.it/yz2znqzb39z51.png?width=978&format=png&auto=webp&s=81390a36176b471072eb40e6bcf1b5468709b712)
[Running](https://preview.redd.it/ak4fuwce39z51.png?width=723&format=png&auto=webp&s=985b5198a04ceedd93d19e1c731a62d4bd666d59)


# Download

[VirusTotal](https://www.virustotal.com/gui/file/e1ffdc33af79703daf3cd8a2c5695402a31f576f1540d7df21a4fd2886fbbfc9)

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

---

# Note

The software contain a 1% DevFee
