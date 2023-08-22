# Ultimate Proxy

[![Downloads](https://img.shields.io/github/downloads/romslf/ultimate-proxy/total?style=for-the-badge)](https://github.com/romslf/Ultimate-Proxy/releases)
[![Discord](https://img.shields.io/discord/754356608158531604?logo=discord&style=for-the-badge&logoColor=white)](https://discord.gg/zWsTZXBYYq)
[![General badge](https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/UltimateProxyChat)

- [Features](#features)
- [Supported coins](#supported-coins-and-algorithms)
- [Usage](#usage)
- [Config file examples](#config-file-examples)
    + [Coin config example](#coin-config-example)
    + [Smart Switch config example (Ethash)](#smart-switch-config-example-ethash)
    + [Smart Switch config example (ETHW vs Nicehash ethash)](#smart-switch-config-example-ethw-vs-nicehash-ethash)
- [Non-exhaustive list of compatible services](#non-exhaustive-list-of-compatible-services)
    + [Mining softwares](#mining-softwares)
    + [Pools](#pools)

# Features

- Huge bandwidth usage reduction
- Stable job distributions
- Remote dashboard statistics, regroup all your proxies/workers (paused for now)
- Ratio switch (Switch between pool on defined intervals, can be combined with SmartSwitch)
- Smart switch (Profit, Reward, Difficulty, TimeToBlock) _[Thanks to Minerstat for providing such an awesome API for free]_
- Control and monitor all your workers at one place
- End-to-end encryption
- Solo mining directly to node (Only ETHW/ETC for now)
- Switch between pools and/or node without restarting miners
- Switch between wallets without restarting miners
- Track workers uptime and reconnection, total and per-pool accepted/rejected shares, calculated hashrate, and response time
- Unlimited number of failover pools

Some users find it useful for:

- Mining on unMineable and switch between coins
- Mining on pools most of the time and try their luck on solo the rest of the time (or the opposite)
- Mining on different wallets for charging hosting fee
- Mining on different wallets for splitting rewards in case of sharing rig/farm
- Control workers using different OS at a single place
- Mining farm with a poor internet connection

# Supported coins and algorithms
_If your favorite coin is not listed use one of the algo name (will not work for SmartSwitch and coin name should always be used if available), or come ask about it on discord_

- **Autolykos**: ERG
- **Equihash125**: FLUX
- **Equihash144**: BTCZ, BTG
- **Equihash192**: YEC, ZCL, ZER
- **Equihash**: ARR, HUSH, KMD, ZEC, ZEN
- **Etchash**: ETC
- **Ethash**: BTN, CAU, CLO, ETHW, EXP, OCTA, QKC, UBQ
- **Firopow**: FIRO
- **Kawpow**: CLORE, RVN, MEWC, NEOX
- **kHeavyHash**: KAS
- **Nexapow**: NEXA
- **Octopus**: CFX
- **Scrypt**: LTC, DOGE, DGB
- **Sha512256d**: RXD
- **Sha256**: BTC, BCH, BSV, DGB, XEC
- **VerusHash**: VRSC

# Usage

1. Download Ultimate Proxy
2. Edit config.json according to your needs (Please use a high difficulty port)
3. Either double click on the .exe file, or in your terminal use one of the following command:

Load the default config (config.json if found, or switch-config.json if found, else create config.json)
```bash
chmod +x            # Linux, you may need to do that once to give it permision to run
./UltimateProxyV2   # Linux
UltimateProxyV2.exe # Windows
```

Load specified config file name (Eitheir a coin config file or a switch-config.json file)
```bash
./UltimateProxyV2 ConfigName.json   # Linux
UltimateProxyV2.exe ConfigName.json # Windows
```

4. Now instead of pointing you workers to the pool address, change it to your proxy IP
5. Enjoy 😎

To achieve **100% Uptime** I strongly recommend one of the following:
- PM2 process manager: [Quick start](https://pm2.keymetrics.io/docs/usage/quick-start/)
- Docker: You can find a prebuilt example maintained by a community member [here](https://github.com/Bitofsin/ultimateproxy-docker)

# Config file examples

## Coin config example

<details>
<summary>Click to show example</summary>

```javascript
{
  "allowedAddresses": [
    "0.0.0.0"	// This allow every IP to connect to proxy, please remove it before adding only needed IPs
  ],
    "poolList": [
    {
      "address": "de.ethw.herominers.com",
      "port": 1147,
      "ssl": true,	// SSL Pool
      "ratio": 98	// Will mine for 98% of RatioWindowTimeHours before switching
    },
    {
      "address": "de.ethw.herominers.com",
      "port": 1147,
      "ratio": 1,	// Will mine for 1% of RatioWindowTimeHours before switching
      "wallet": "solo:ANOTHER WALLET",	// Will use this wallet instead of global Wallet (Note: "solo:" is used to solo mine on herominers)
      "password": "ANOTHER PASS"	// Will use this password instead of global Password
    },
    {
      "address": "192.168.1.30",
      "port": 8545,
      "node": true,	// Solo mining to node
      "ratio": 1	// Will mine for 1% of RatioWindowTimeHours before switching
    },
    {
      "address": "ethw.2miners.com",	// Will be only used as failover since no ratio is set
      "port": 2020
    }
  ],
  "Protocol": "Stratum", // The mining protocol used (Ethproxy/Stratum/Nicehash)
  "Coin": "ETHW",	// The coin you want to mine
  "Wallet": "YOUR WALLET HERE",	// Your mining wallet
  "Worker": "UltimateProxy",	// Proxy worker name
  "Password": "x",	// Proxy password
  "RatioWindowTimeHours": 1,  // Used for ratio switch strategie, minimum 1H maximum 24H
  "ProxyPort": 4444,	// Proxy port
  "ProxyCert": "",	// Set it if you want your workers to connect to proxy using SSL (See "Docs" folder create a .pfx file)
  "PrintStats": true,	// Display workers/pools stats
  "StatsIntervalSeconds": 60,	// Delay between PrintStats
  "NodeGetWorkIntervalMs": 500,	// Delay between node solo getWork requests
  "PrintJobs": true,	// Print new jobs or not
  "AllowDuplicateWorkerNames": false, // If you use duplicate worker names (workers will be deleted from stats table on disconnection)
  "SendStaleShares": true, // If we should send stale shares to pool
  "ForceWorkersReconnect": false // Reconnect workers on switch, NEED to be turned on if you use Stratum/Nicehash protocol and that your miner doesn't support set.extranonce request
}
```

</details>

## Smart Switch config example (Ethash)

<details>
<summary>Click to show example</summary>

```javascript
{
  "Coins": [
    "ETHW",
    "EXP",
    "QKC",
    "CLO"
  ],
  "Mode": "PROFIT",
  "MinimumTimeSeconds": 900,
  "MinimumDifferencePercent": 1,
  "ConfigList": [
    {
      "Coin": "ETHW",
      "FileName": "config-ETHW.json"
    },
    {
      "Coin": "EXP",
      "FileName": "config-EXP.json"
    },
    {
      "Coin": "QKC",
      "FileName": "config-QKC.json"
    },
    {
      "Coin": "CLO",
      "FileName": "config-CLO.json"
    }
  ]
}
```

</details>

### Smart Switch config example (ETHW vs Nicehash ethash)

<details>
<summary>Click to show example</summary>

```javascript
{
  "Coins": [
    "ETHW",
    "NH Ethash"
  ],
  "Mode": "PROFIT",
  "MinimumTimeSeconds": 900,
  "MinimumDifferencePercent": 1,
  "ConfigList": [
    {
      "Coin": "ETHW",
      "FileName": "config-ETHW.json"
    },
    {
      "Coin": "NH Ethash",
      "FileName": "config-NH-Ethash.json"
    }
  ]
}
```

</details>


# Non-exhaustive list of compatible services

### Mining softwares

- [Teamredminer](https://github.com/todxx/teamredminer)
- [LolMiner](https://github.com/Lolliedieb/lolMiner-releases)
- [PhoenixMiner](https://bitcointalk.org/index.php?topic=2647654.0)
- [Gminer](https://github.com/develsoftware/GMinerRelease)

### Pools

- [Herominers](https://herominers.com)
- [2miners](https://2miners.com)
- [Crazypool](https://crazypool.org/)
- [Flexpool](https://www.flexpool.io/)
- [Prohashing](https://prohashing.com/)
- [Woolypooly](https://woolypooly.com/)
- [Unmineable](https://unmineable.com/)

---

Don't hesitate to:
* Ask questions
* Report bugs
* Give ideas
* Criticize anything

Thank you for reading all this, and happy mining !

---

# Note

The software contain a 0.8% DevFee (30s every hour)
