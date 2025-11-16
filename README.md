# 🐋 Whale Watcher - Solana Whale Tracker

A real-time Solana whale tracking system that monitors large on-chain DEX swaps and delivers instant alerts via Telegram. Built for traders and analysts who need to stay ahead of market-moving transactions.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Solana](https://img.shields.io/badge/Solana-Web3-purple)
![Telegram](https://img.shields.io/badge/Telegram-Bot_API-blue)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-green)
![FastAPI](https://img.shields.io/badge/FastAPI-API-red)
![Docker](https://img.shields.io/badge/Docker-Containerization-2496ED)

## 🌟 Features

### 🔍 Real-time Monitoring
- **Live Transaction Streaming**: Track Solana DEX swaps in real-time using WebSocket connections
- **Whale Detection**: Identify large transactions based on customizable threshold amounts
- **Multi-DEX Support**: Monitor swaps across popular Solana decentralized exchanges

### 📊 Advanced Analytics
- **Wallet Profiling**: Track whale wallet patterns and trading behaviors
- **Volume Analysis**: Monitor trading volume spikes and unusual activity
- **Price Impact Alerts**: Estimate potential price impact of large swaps

### 🔔 Smart Notifications
- **Instant Telegram Alerts**: Receive real-time notifications for significant trades
- **Customizable Thresholds**: Set minimum swap amounts for different tokens
- **Rich Media Alerts**: Get detailed messages with token info, USD value, and transaction links

## 🛠 Tech Stack

- **Python 3.8+** - Core programming language
- **solana-py** - Solana blockchain interaction
- **WebSockets** - Real-time data streaming
- **MongoDB** - Transaction logging and analytics
- **FastAPI** - REST API for data queries
- **Telegram Bot API** - Instant notifications
- **Docker** - Containerization
- **Redis** - Caching and rate limiting

## 📈 Supported Tokens

| Token | Default Threshold | Description |
|-------|------------------|-------------|
| **SOL** | 1,000 SOL | Large SOL movements |
| **USDC** | 50,000 USDC | Significant stablecoin swaps |
| **BONK** | 100M BONK | Meme coin whale activity |
| **JUP** | 25,000 JUP | DEX aggregator token |
| **Custom** | Configurable | Any SPL token on Solana |

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- MongoDB instance
- Telegram Bot Token
- Solana RPC URL

### Installation

# Clone the repository
git clone https://github.com/mrsirjon/WhaleWatcher.git
cd whale-watcher

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

### Configuration
```bash
# .env file
SOLANA_RPC_URL=https://api.mainnet-beta.solana.com
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
TELEGRAM_CHAT_ID=your_chat_id
MONGODB_URI=mongodb://localhost:27017
MIN_SWAP_AMOUNT_USD=10000  # Alert threshold
```
### Usage
```bash
# Start the whale watcher
python main.py

# Or run with Docker
docker-compose up -d
```
### 📊 Sample Alert
```bash
🐋 WHALE ALERT 🐋

Token: SOL → USDC
Amount: 1,250 SOL ($187,500)
DEX: Raydium
Wallet: 7abc...xyz1

📈 Price Impact: ~2.3%
🕒 Time: 2024-01-15 14:30:22 UTC

🔗 View on Solscan: https://solscan.io/tx/...
```
### 🗃️ Database Schema
```bash
// Swaps Collection
{
  signature: "5x8d...",
  wallet: "7abc...xyz1",
  token_in: "SOL",
  token_out: "USDC",
  amount_in: 1250,
  amount_out: 187500,
  usd_value: 187500,
  dex: "raydium",
  timestamp: ISODate("2024-01-15T14:30:22Z"),
  price_impact: 2.3
}
```
### 🔧 API Endpoints
```bash
# Get recent whale transactions
GET /api/whales/recent?limit=10

# Get wallet analysis
GET /api/wallets/{wallet_address}

# Get token statistics
GET /api/tokens/{token_mint}/stats
```
### 🐳 Deployment
```bash
# docker-compose.yml
version: '3.8'
services:
  whale-watcher:
    build: .
    environment:
      - SOLANA_RPC_URL=${SOLANA_RPC_URL}
      - TELEGRAM_BOT_TOKEN=${TELEGRAM_BOT_TOKEN}
    depends_on:
      - mongodb
      - redis
```
## Cloud Deployment
AWS: EC2 + Elasticache + DocumentDB

Heroku: Redis + MongoDB Atlas

Railway: All-in-one deployment

## 📈 Performance
< 2 second alert delivery from transaction to Telegram

10,000+ transactions processed per hour

99.5% uptime with automatic reconnection

Multi-RPC fallback for reliability
