## [Download](https://github.com/romslf/Ultimate-Proxy/releases), [Discord](https://discord.gg/zWsTZXBYYq)
## [Online Dashboard](https://up.pragma-solutions.fr/), [Telegram Bot](https://t.me/UltimateProxyBot)

- [What is a proxy ?](#what-is-a-proxy-)
- [Features](#features)
- [Supported coins](#supported-coins)
- [Usage](#usage)
- [Config file examples](#config-file-examples)
    + [Coin config example](#coin-config-example)
    + [Smart Switch config example (Ethash)](#smart-switch-config-example-ethash)
    + [Smart Switch config example (ETH vs Nicehash ethash)](#smart-switch-config-example-eth-vs-nicehash-ethash)
- [Non-exhaustive list of compatible services](#non-exhaustive-list-of-compatible-services)
    + [Mining softwares](#mining-softwares)
    + [Pools](#pools)

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

The best part is that it subscribre once for jobs and broacast them to all connected workers. 
This lead to a huge bandwitch usage reduction, and a more stable job distributions along all miners, wich can increase profitability on a long run.

**With our example of 100 workers this will divide our bandwidth usage by 100**

# Features

- Huge bandwidth usage reduction
- Remote dashboard statistics, regroup all your proxies/workers
- Control and monitor all your workers at one place
- Smart switch (Profit, Reward, Difficulty, TimeToBlock) _[Thanks to Minerstat for providing such an awesome API for free]_
- End-to-end encryption
- Pool mining
- Solo mining directly to node (Only ETH/ETC for now)
- Switch between pools and/or node without restarting miners
- Switch between wallets without restarting miners
- Keep track of your workers uptime
- Keep track of your workers reconnection
- Get total and per pool accepted/rejected shares
- Get average and per pool calculated hashrate
- Get average and per pool response time
- Unlimited number of failover pools

Some users find it useful for:

- Mining on unMineable and switch between coins
- Mining on pools most of the time and try their luck on solo the rest of the time
- Mining on different wallets for charging hosting fee
- Mining on different wallets for splitting rewards in case of sharing rig/farm
- Control workers using different OS at a single place

# Supported coins

- CLO, ETC, ETH, EXP, QKC, UBQ
- BTCZ, BTG, FLUX, HUSH, KMD, YEC, ZCL, ZEC, ZEN, ZER
- RVN
- FIRO

# Usage

1. Install .NET 6.0 runtime, which can be found here: https://dotnet.microsoft.com/en-us/download/dotnet/6.0
2. Download Ultimate Proxy
3. Edit config.json according to your needs (If there is no config.json file, just run Ultimate Proxy it will create one. See 4.)
4. Either double click on the .exe file, or in your terminal use one of the following command:

```bash
dotnet UltimateProxyV2.dll # Will load the default config (config.json if found, or switch-config.json if found, else create config.json)
dotnet UltimateProxyV2.dll config-FLUX.json # Will load specified config file name (Eitheir a coin config file or a switch-config.json file)
```

5. Now instead of pointing you workers to the pool address, change it to your proxy IP
6. (Optional) Plug it to the online dashboard, talk to https://t.me/UltimateProxyBot or visit https://up.pragma-solutions.fr, copy and paste the API token provided by the bot to your proxy config in "DashboardApiToken" field, resart your proxy if already running.
7. Enjoy 😎

To achieve **100% Uptime** I strongly recommend using PM2 process manager: 
https://pm2.keymetrics.io/docs/usage/quick-start/

1. Install nodejs/npm (Can be done very easily using https://github.com/nvm-sh/nvm)
2. Then you get access to the following commands 
```bash
npm install pm2@latest -g # Install pm2
```
```bash
pm2 start dotnet --name UltimateProxy -- UltimateProxyV2.dll # Start UltimateProxy 
pm2 start dotnet --name UltimateProxy -- UltimateProxyV2.dll configName.json # Start UltimateProxy with the specified config file
```
```bash
pm2 startup # Auto start pm2 on boot/reboot, (follow the output messages for aditional steps)
``` 
```bash
pm2 save # Save the current process list to be automatically started on boot/startup 
```
```bash
pm2 list # See all running pm2 process an their status
```
```bash
pm2 logs UltimateProxy # To see logs and errors of UltimateProxy 
```
```bash
pm2 restart UltimateProxy # To restart UltimateProxy in case of a config change for example 
```

# Config file examples

## Coin config example

```javascript
{
  "allowedAddresses": [
    "0.0.0.0"	// This allow every IP to connect to proxy, please remove it before adding only needed IPs
  ],
    "poolList": [
    {
      "address": "eth.2miners.com",
      "port": 12020,
      "ssl": true,	// SSL Pool
      "ratio": 98	// Will mine for 98% of RatioWindowTimeHours before switching
    },
    {
      "address": "eth.2miners.com",
      "port": 2020,
      "ratio": 1,	// Will mine for 1% of RatioWindowTimeHours before switching
      "wallet": "ANOTHER WALLET",	// Will use this wallet instead of global Wallet
      "password": "ANOTHER PASS"	// Will use this password instead of global Password
    },
    {
      "address": "192.168.1.30",
      "port": 8545,
      "node": true,	// Solo mining to node
      "ratio": 1	// Will mine for 1% of RatioWindowTimeHours before switching
    },
    {
      "address": "eth-de.flexpool.io",	// Will be only used as failover since no ratio is set
      "port": 4444
    }
  ],
  "Protocol": "Stratum", // The mining protocol used (Ethproxy/Stratum/Nicehash)
  "Coin": "ETH",	// The coin you want to mine
  "Wallet": "YOUR WALLET HERE",	// Your mining wallet
  "Worker": "UltimateProxy",	// Proxy worker name
  "Password": "x",	// Proxy password
  "DashboardApiToken": "", // Your dashboard api token, generate it by talking to https://t.me/UltimateProxyBot or visit https://up.pragma-solutions.fr
  "RatioWindowTimeHours": 1,  // Used for ratio switch strategie, minimum 1H maximum 24H
  "ProxyPort": 4444,	// Proxy port
  "ProxyCert": "",	// Set it if you want your workers to connect to proxy using SSL (See "Docs" folder create a .pfx file)
  "PrintStats": true,	// Display workers/pools stats
  "StatsIntervalSeconds": 60,	// Delay between PrintStats
  "NodeGetWorkIntervalMs": 500,	// Delay between node solo getWork requests
  "PrintJobs": true,	// Print new jobs or not
  "StaleSharesWindow": 10, // How much shares should be kept in memory to catch duplciate shares
  "ForceWorkersReconnect": false // Reconnect workers on switch, NEED to be turned on if you use Stratum/Nicehash protocol and that your miner doesn't support set.extranonce request
}
```

## Smart Switch config example (Ethash)

```javascript
{
  "Coins": [
    "ETH",
    "EXP",
    "QKC",
    "CLO"
  ],
  "Mode": "PROFIT",
  "MinimumTimeSeconds": 900,
  "MinimumDifferencePercent": 1,
  "ConfigList": [
    {
      "Coin": "ETH",
      "FileName": "config-ETH.json"
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

### Smart Switch config example (ETH vs Nicehash ethash)

```javascript
{
  "Coins": [
    "ETH",
    "NH Ethash"
  ],
  "Mode": "PROFIT",
  "MinimumTimeSeconds": 900,
  "MinimumDifferencePercent": 1,
  "ConfigList": [
    {
      "Coin": "ETH",
      "FileName": "config-ETH.json"
    },
    {
      "Coin": "NH Ethash",
      "FileName": "config-NH-Ethash.json"
    }
  ]
}
```

# Non-exhaustive list of compatible services

### Mining softwares

- [Teamredminer](https://github.com/todxx/teamredminer)
- [LolMiner](https://github.com/Lolliedieb/lolMiner-releases)
- [PhoenixMiner](https://bitcointalk.org/index.php?topic=2647654.0)
- [Gminer](https://github.com/develsoftware/GMinerRelease)

### Pools

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

The software contain a 0.8% DevFee
