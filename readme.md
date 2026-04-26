# Polymarket Smart Money Tracker

A data-driven system that tracks top-performing wallets on Polymarket, identifies consistent performers, and monitors their trades in near real-time to extract actionable insights.

---

## Overview

This project focuses on analyzing “smart money” behavior on Polymarket instead of blindly copying trades.

It:

* Identifies top-performing wallets across categories
* Filters for consistent performers
* Tracks their trades continuously
* Logs structured data for analysis

---

## Data Source

Top wallets are fetched using the Polymarket leaderboard API:

### Top 50 Wallets per Category

* Politics
  https://data-api.polymarket.com/v1/leaderboard?timePeriod=MONTH&limit=50&orderBy=PNL&category=POLITICS

* Economics
  https://data-api.polymarket.com/v1/leaderboard?timePeriod=MONTH&limit=50&orderBy=PNL&category=ECONOMICS

* Finance
  https://data-api.polymarket.com/v1/leaderboard?timePeriod=MONTH&limit=50&orderBy=PNL&category=FINANCE

* Culture
  https://data-api.polymarket.com/v1/leaderboard?timePeriod=MONTH&limit=50&orderBy=PNL&category=CULTURE

* Tech
  https://data-api.polymarket.com/v1/leaderboard?timePeriod=MONTH&limit=50&orderBy=PNL&category=TECH

* Sports
  https://data-api.polymarket.com/v1/leaderboard?timePeriod=MONTH&limit=50&orderBy=PNL&category=SPORTS

* Crypto
  https://data-api.polymarket.com/v1/leaderboard?timePeriod=MONTH&limit=50&orderBy=PNL&category=CRYPTO

---

## How It Works

### 1. Wallet Collection Script

* Fetches top 50 wallets per category
* Stores results in an Excel file
* Used to build a pool of high-performing traders

Output:

```
polymarket_smart_money.xlsx
```

---

### 2. Trade Tracking Script

* Uses selected consistent performers
* Polls for new trades every 60 seconds
* Detects when a wallet enters a trade

For each trade, it logs:

* Wallet address
* Market name
* Timestamp
* Entry price
* Position (YES/NO)

Output:

```
polymarket_trades_log.xlsx
```

---

## Project Structure

```
├── data/
│   ├── polymarket_smart_money.xlsx
│   ├── polymarket_trades_log.xlsx
│
├── scripts/
│   ├── wallet_collector.py
│   ├── trade_tracker.py
│
└── README.md
```

---

## Key Insight

This project does not aim to blindly copy trades.

Instead, it focuses on identifying repeatable patterns in high-performing wallets and using them as signals.

---

## Limitations

* API polling (not true real-time WebSocket yet)
* Trade execution is not automated
* No guarantee of profitability (markets are efficient)

---

## Future Improvements

* Real-time alerts (Telegram / Discord)
* WebSocket-based tracking
* Trade quality scoring system
* Strategy clustering of wallets

---

## Disclaimer

This project is for research and educational purposes only.
Not financial advice.

---

## If you like this project

Give it a star
