---
name: web3-daily-dashboard
description: Generate a daily Web3 or crypto dashboard using market data, RSS aggregation, and lightweight analysis.
category: research
---

# Web3 Daily Dashboard

## Trigger Conditions
- Generate a recurring daily Web3 or crypto briefing
- Aggregate market data, sentiment, and major news into a compact dashboard

## Data Sources

### 1. Market Data

```bash
curl -s 'https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&ids=bitcoin,ethereum,solana,binancecoin,ripple,avalanche-2,chainlink,uniswap,polkadot,cardano&order=market_cap_desc&sparkline=false&price_change_percentage=7d,30d'

curl -s 'https://api.coingecko.com/api/v3/global'

curl -s 'https://api.coingecko.com/api/v3/simple/price?ids=bitcoin,ethereum,solana&vs_currencies=usd&include_24hr_change=true'
```

### 2. News Sources

| Source | URL | Reliability |
| --- | --- | --- |
| Cointelegraph | `https://cointelegraph.com/rss` | often malformed |
| The Block | `https://www.theblock.co/rss.xml` | stable |
| Decrypt | `https://decrypt.co/feed` | inconsistent |
| CoinDesk | `https://www.coindesk.com/arc/outboundfeeds/rss/` | redirect-prone |
| CryptoSlate | `https://cryptoslate.com/feed/` | inconsistent |

Use multiple sources with fallback logic rather than depending on one parser or one feed.

### 3. Sentiment

```bash
curl -s 'https://api.alternative.me/fng/'
```

### 4. On-Chain or Macro Signals

```bash
curl -s 'https://api.blockchain.info/stats'
```

## RSS Parsing Fallback Strategy

### Method A: Full XML Parsing

```python
import xml.etree.ElementTree as ET

try:
    root = ET.fromstring(xml_text)
except ET.ParseError:
    root = None
```

### Method B: Regex Title Extraction

```python
import re

titles = re.findall(r"<title>([^<]+)</title>", xml_text)
```

## Practical Recommendations

- Truncate oversized RSS payloads before parsing
- Run multiple feeds in parallel
- Treat one failed source as non-fatal
- Prefer stable feeds as primary sources and malformed feeds as optional fallback

## Suggested Output Structure

```text
Web3 Daily Dashboard | YYYY-MM-DD

- Market overview
- Major events
- Sector heat map
- Risk warnings
- Trading or positioning implications
```

## Interpretation Notes

- Fear and Greed can be used as a contrarian indicator
- Exchange inflow spikes often signal increased sell pressure
- Stablecoin reserve changes can be useful liquidity signals
- Geopolitical shocks can temporarily dominate narrative-driven assets like BTC
