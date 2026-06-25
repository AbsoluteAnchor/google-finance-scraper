[Google Finance Scraper](https://apify.com/kaix/google-finance-scraper?fpr=data)

# Google Finance Scraper

Scrape comprehensive financial data from Google Finance. Returns stock quotes, company info, financial statements, price charts, news, and related stocks. Supports stocks, ETFs, indices, crypto, currencies, and futures across 20+ global exchanges.

## Why use this scraper?

- Full stock data: quote, 52-week range, market cap, P/E, dividend yield, volume, beta, sector
- Company profile: description, CEO, employees, HQ, founded date, website, Wikipedia
- Financial statements: income statement, balance sheet, cash flow (quarterly + annual, multiple years)
- Price charts: intraday minute-by-minute or daily OHLCV with configurable time range
- News with snippets, thumbnails, and related stock quotes embedded in articles
- Related stocks with full quote data
- Crypto pairs (BTC-USD, ETH-USD), currencies (EUR-USD), futures (GCW00:COMEX)
- 18 market discovery pages (gainers, losers, trending, crypto, futures, sectors, etc.)

## Use cases

- Build financial databases with fundamentals across global markets
- Track stock prices, after-hours data, and earnings dates
- Analyze income statements, balance sheets, and cash flow trends
- Feed price charts into technical analysis pipelines
- Monitor financial news with related stock context
- Discover trending stocks, top gainers/losers, and market movers

## How to use

### Look up a single stock

```
{
  "stocks": ["GOOGL:NASDAQ"]
}
```

### Look up multiple stocks

```
{
  "stocks": [
    "GOOGL:NASDAQ",
    "AAPL:NASDAQ",
    "TSLA:NASDAQ",
    "AMZN:NASDAQ"
  ]
}
```

### Crypto

```
{
  "stocks": ["BTC-USD", "ETH-USD", "SOL-USD"]
}
```

### Currency pairs

```
{
  "stocks": ["EUR-USD", "GBP-USD", "USD-JPY"]
}
```

### Futures / Commodities

```
{
  "stocks": ["GCW00:COMEX", "CLW00:NYMEX", "SIW00:COMEX"]
}
```

> **Note:** Use Google Finance ticker format, not Yahoo Finance. For example, use `GCW00:COMEX` for Gold, not `GC=F`.

### Global exchanges

```
{
  "stocks": [
    "005930:KRX",
    "7203:TYO",
    "RELIANCE:NSE",
    "VOW3:ETR",
    "0700:HKG"
  ]
}
```

### Discover stocks from market pages

```
{
  "searchMarket": "gainers",
  "maxSearchResults": 10
}
```

### Minimal output (quote only)

```
{
  "stocks": ["GOOGL:NASDAQ"],
  "includeFinancials": false,
  "includeChart": false,
  "includeNews": false,
  "includeRelated": false
}
```

### Full output with 1-year chart

```
{
  "stocks": ["GOOGL:NASDAQ"],
  "includeFinancials": true,
  "includeChart": true,
  "includeNews": true,
  "includeRelated": true,
  "includeMarketIndices": true,
  "includeMarketMovers": true,
  "chartWindow": "1Y"
}
```

## Input

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `stocks` | string[] |  | Stock identifiers or Google Finance URLs |
| `searchMarket` | enum |  | Market page to discover stocks from (see below) |
| `searchTerm` | string |  | Search keyword to discover trending stocks |
| `maxSearchResults` | number | `20` | Max stocks from search/market page |
| `includeFinancials` | boolean | `true` | Income statement, balance sheet, cash flow |
| `includeChart` | boolean | `true` | OHLCV price chart data |
| `includeNews` | boolean | `true` | News headlines, sources, snippets |
| `includeRelated` | boolean | `true` | Related and similar stocks |
| `includeMarketIndices` | boolean | `false` | Global market indices |
| `includeMarketMovers` | boolean | `false` | Top gainers/losers/trending |
| `chartWindow` | enum | `1M` | `1D`, `5D`, `1M`, `6M`, `YTD`, `1Y`, `5Y`, `MAX` |

### Market pages

`indexes`, `gainers`, `losers`, `most-active`, `trending`, `climate-leaders`, `currencies`, `crypto`, `etfs`, `futures`, `commodities`, `bonds`, `sectors`, `americas`, `europe-middle-east-africa`, `asia-pacific`, `world`

### Supported exchanges

NASDAQ, NYSE, NYSEARCA, KRX, TYO, NSE, ETR, HKG, SHA, ASX, TSE, CVE, JSE, COMEX, NYMEX, and all major index providers (INDEXDJX, INDEXSP, INDEXNASDAQ, INDEXNIKKEI, INDEXHANGSENG, INDEXBOM, INDEXNSE, etc.)

## Output

One record per stock in the default dataset.

### Stock output (GOOGL:NASDAQ — live data)

```
{
  "ticker": "GOOGL",
  "exchange": "NASDAQ",
  "exchangeName": "NASDAQ",
  "name": "Alphabet Inc Class A",
  "type": "stock",
  "currency": "USD",
  "country": "US",
  "kgMid": "/m/07zln7n",
  "price": 337.17,
  "previousClose": 336.02,
  "open": 337.65,
  "high": 338.75,
  "low": 336.24,
  "change": 1.15,
  "changePercent": 0.34,
  "fiftyTwoWeekHigh": 349,
  "fiftyTwoWeekLow": 146.1,
  "marketCap": 4062214655676,
  "peRatio": 31.18,
  "dividendYield": 0.25,
  "volume": 27972713,
  "beta": 1.125,
  "sharesOutstanding": 5822000000,
  "sector": "Interactive media",
  "timezone": "America/New_York",
  "afterHours": {
    "price": 338,
    "change": 0.94,
    "changePercent": 0.28,
    "lastUpdateTimestamp": 1776432600
  },
  "nextEarningsDate": { "year": 2026, "month": 3, "day": 9 },
  "company": {
    "description": "Alphabet Inc. is an American multinational technology conglomerate...",
    "ceo": "Sundar Pichai",
    "employees": 190820,
    "founded": { "year": 2015, "month": 10, "day": 2 },
    "hq": {
      "city": "Mountain View",
      "state": "California",
      "country": "United States",
      "countryCode": "US",
      "address": "1600 Amphitheatre Parkway"
    },
    "website": "https://abc.xyz/",
    "wikipediaUrl": "https://en.wikipedia.org/wiki/Alphabet_Inc."
  },
  "financials": {
    "periods": [
      {
        "periodType": "annual",
        "fiscalEnd": { "year": 2025, "month": 12, "day": 31 },
        "currency": "USD",
        "revenue": 113829000000,
        "netIncome": 34455000000,
        "eps": 2.81,
        "operatingMargin": 30.27,
        "operatingIncome": 35934000000,
        "totalAssets": 595281000000,
        "totalLiabilities": 206038000000,
        "totalEquity": 415265000000,
        "cashAndShortTermInvestments": 77895000000,
        "operatingCashFlow": 52402000000,
        "capex": 32128000000,
        "profitMargin": 34.35,
        "returnOnAssets": 15.88
      }
    ]
  },
  "chart": {
    "window": "1M",
    "intervalSeconds": 86400,
    "previousClose": 337.12,
    "dataPoints": [
      {
        "timestamp": 1773738000,
        "date": [2026, 3, 17, 16],
        "price": 310.92,
        "change": 0,
        "changePercent": 0,
        "volume": 21955171
      }
    ]
  },
  "news": [
    {
      "title": "Dbs Bank Increases Alphabet (NASDAQ:GOOGL) Price Target to $400.00",
      "source": "MarketBeat",
      "url": "https://www.marketbeat.com/...",
      "timestamp": 1776436200,
      "snippet": "Alphabet (NASDAQ:GOOGL) had its price target increased...",
      "articleId": "12345678901234567890",
      "thumbnailUrl": "https://encrypted-tbn0.gstatic.com/...",
      "thumbnailWidth": 300,
      "thumbnailHeight": 168,
      "relatedTickers": [{ "ticker": "", "exchange": "", "kgMid": "/m/07zln7n" }]
    }
  ],
  "relatedStocks": [
    {
      "ticker": "AMZN",
      "exchange": "NASDAQ",
      "name": "Amazon.com Inc",
      "type": "stock",
      "currency": "USD",
      "price": 254.49,
      "change": 5.99,
      "changePercent": 2.41,
      "previousClose": 248.5,
      "kgMid": "/m/07zl90k"
    }
  ]
}
```

### Crypto output (BTC-USD — live data)

```
{
  "ticker": "BTC-USD",
  "exchange": "",
  "name": "Bitcoin (BTC / USD)",
  "type": "crypto",
  "currency": "USD",
  "price": 77925.27,
  "previousClose": 75164.04,
  "change": 2761.23,
  "changePercent": 3.67,
  "baseCurrency": "BTC",
  "quoteCurrency": "USD",
  "baseName": "Bitcoin",
  "quoteName": "United States Dollar",
  "company": null,
  "financials": null,
  "chart": {
    "window": "1M",
    "dataPoints": "32 points"
  },
  "relatedStocks": [
    { "ticker": "ETH-USD", "name": "Ether (ETH / USD)", "price": 2447.67 },
    { "ticker": "LTC-USD", "name": "Litecoin (LTC / USD)", "price": 57.05 },
    { "ticker": "DOGE-USD", "name": "Dogecoin (DOGE / USD)", "price": 0.098 }
  ]
}
```

### Output fields

**Quote** (always included): `ticker`, `exchange`, `exchangeName`, `name`, `type`, `currency`, `country`, `kgMid`, `price`, `previousClose`, `open`, `high`, `low`, `change`, `changePercent`, `fiftyTwoWeekHigh`, `fiftyTwoWeekLow`, `marketCap`, `peRatio`, `dividendYield`, `volume`, `avgVolume`, `beta`, `sharesOutstanding`, `sector`, `isDelayed`, `lastUpdateTimestamp`, `timezone`, `utcOffset`, `brandColor`, `afterHours`, `marketHours`, `baseCurrency`, `quoteCurrency`, `baseName`, `quoteName`, `companyKgMid`, `nextEarningsDate`

**Company** (stocks/ETFs only): `description`, `ceo`, `employees`, `founded`, `hq` (city, state, country, address), `website`, `wikipediaUrl`

**Financials** (when `includeFinancials` is true): quarterly + annual periods with `revenue`, `netIncome`, `eps`, `epsDiluted`, `operatingIncome`, `operatingMargin`, `ebitda`, `totalAssets`, `totalLiabilities`, `totalEquity`, `cashAndShortTermInvestments`, `operatingCashFlow`, `investingCashFlow`, `financingCashFlow`, `capex`, `freeCashFlow`, `dividendsPaid`, `profitMargin`, `returnOnAssets`, `revenueGrowth`, `netIncomeGrowth`

**Chart** (when `includeChart` is true): `window`, `intervalSeconds`, `previousClose`, `dataPoints[]` with `timestamp`, `date`, `price`, `change`, `changePercent`, `volume`

**News** (when `includeNews` is true): `title`, `source`, `url`, `timestamp`, `snippet`, `articleId`, `thumbnailUrl`, `thumbnailWidth`, `thumbnailHeight`, `relatedTickers[]`, `relatedStockQuotes[]`

**Related stocks** (when `includeRelated` is true): `ticker`, `exchange`, `name`, `type`, `currency`, `price`, `change`, `changePercent`, `previousClose`, `kgMid`, `afterHours`

**Market indices** (when `includeMarketIndices` is true): grouped by region (US, Europe, Asia, Currencies, Crypto, Futures) with `ticker`, `exchange`, `name`, `displayName`, `price`, `change`, `changePercent`

**Market movers** (when `includeMarketMovers` is true): `ticker`, `exchange`, `name`, `price`, `change`, `changePercent`