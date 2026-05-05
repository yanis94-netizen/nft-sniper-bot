# 🎯 NFT Sniper Bot — FCFS Edition

A fully automated First-Come-First-Served NFT minting bot with a real-time web dashboard.

## Features
- ⚡ Ultra-fast FCFS minting — fires the moment a sale goes live
- 🔄 Automatic sale status detection (monitors `saleIsActive`, `paused`, etc.)
- 🌐 Supports Ethereum, Polygon, BSC, Arbitrum, Base, Optimism
- ⛽ EIP-1559 gas optimization with configurable priority fees
- 📊 Real-time dashboard with live logs, stats, and TX tracker
- 🔌 WebSocket RPC support for lower latency
- 🛑 Auto-stop after successful mint (configurable)

---

## 🚀 Quick Start

### 1. Requirements
- **Node.js v16+** — https://nodejs.org
- An **RPC endpoint** (free at Alchemy or Infura)
- A **wallet private key** with ETH for gas

### 2. Install
```bash
cd nft-sniper-bot
npm install
```

### 3. Configure (optional — you can also use the dashboard UI)
```bash
cp .env.example .env
# Edit .env with your values
```

### 4. Run
```bash
npm start
```

### 5. Open Dashboard
Visit: **http://localhost:3000**

---

## 📋 Configuration Guide

| Field | Description | Example |
|-------|-------------|---------|
| Private Key | Your wallet private key | `0xabc123...` |
| RPC URL | Alchemy/Infura HTTP endpoint | `https://eth-mainnet.g.alchemy.com/v2/KEY` |
| WebSocket RPC | Same but WSS (faster) | `wss://eth-mainnet.g.alchemy.com/v2/KEY` |
| Contract Address | NFT contract to mint from | `0xBC4CA0E...` |
| Mint Function | The function to call | `mint(uint256)` |
| Mint Amount | How many NFTs per TX | `1` |
| Max Price ETH | Max you'll pay (0 = free) | `0.08` |
| Max Priority Fee | Miner tip in Gwei | `50` |
| Max Fee | Total max gas in Gwei | `150` |
| Poll Interval | How often to check (ms) | `1000` |

---

## 🔎 How to Find Contract Info

1. Go to the NFT project's website
2. Find the contract on Etherscan
3. Go to **Contract → Read Contract** to see functions
4. Copy the contract address
5. Check which function is used for minting

### Common Mint Functions
- `mint(uint256)` — most common
- `publicMint(uint256)` — some projects
- `mint(address, uint256)` — mints to address
- `claim(uint256)` — claim-style drops

---

## ⛽ Gas Tips

For **competitive drops**, increase these values:
- Priority Fee: `100-200 Gwei`
- Max Fee: `300-500 Gwei`

For **low-competition** or free mints, defaults are fine.

---

## ⚠️ Disclaimer

This tool is for educational purposes. Always understand:
- Minting from bots may violate project terms of service
- Gas fees are non-refundable even on failed transactions
- Never share your private key with anyone
- Test with small amounts first

---

## 🆘 Troubleshooting

| Error | Fix |
|-------|-----|
| `invalid private key` | Make sure it starts with `0x` and is 66 chars |
| `could not connect` | Check your RPC URL and API key |
| `transaction reverted` | Sale may not be active, or max supply reached |
| `insufficient funds` | Add more ETH to your wallet |
| `gas too low` | Increase Max Fee and Priority Fee |
