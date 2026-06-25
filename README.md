[Google Finance Scraper](https://apify.com/scraped_org/google-finance-scraper?fpr=data)

Effortlessly gather stocks, ETFs, Mutual Funds data from **Google Finance**.

Our Actor is designed for speed, reliability, and scalability, handling multiple stocks in a single run with ease.

Perfect for businesses, developers, and analysts looking to gain insights and make data-driven decisions.

Apify proxies are supported by this actor. See explanation. See those links for more information: [Link1](https://docs.apify.com/sdk/python/docs/concepts/proxy-management), [Link2](https://docs.apify.com/platform/actors/development/actor-definition/input-schema/specification/v1#object)

Key features include:

- Stocks Details
- Market Trends
- Stock Search

## Actions

| Action Name | Action Code | Description |
| --- | --- | --- |
| Stocks Details | `"stocks_details"` | Get Stocks Details |
| Market Trends | `"market_trends"` | Get Market Trends |
| Search Stocks | `"search_stocks"` | Search Stocks |

### Stocks Details

Get Stocks Details from Google Finance.

#### Inputs

| Input Name | Input Code | Description | Type | Constraints | Required | Default |
| --- | --- | --- | --- | --- | --- | --- |
| Action | `action` | Perform extraction of stocks details from Google Finance | String | Pass `"stocks_details"` to perform this action | Yes | `"stocks_details"` |
| Country | `country` | 2 letters country code (ISO 3166-2) | String | Valid country code | No | `"us"` |
| Language | `language` | 2 letters language code (ISO 639-1) | String | Valid language Code | No | `"en"` |
| Stocks | `stocks` | List of stocks. Fill stocks as in Google Finance URL (e.g. `["AAPL:NASDAQ"]`) | Array of Strings | Valid stocks. Non valid IDs will be skipped | Yes |  |
| Extract Stock News | `extract_stock_news` | Whether to extract news related to the stocks or not | Boolean |  | No | `true` |
| Extract Quarterly Financial | `extract_quarterly_financial` | Whether to extract quarterly financial of the stocks or not | Boolean |  | No | `true` |
| Extract Yearly Financial | `extract_yearly_financial` | Whether to extract yearly financial of the stocks or not | Boolean |  | No | `true` |
| Extract Current Stock Prices | `extract_stock_prices_in_day` | Whether to extract stocks prices of the current day (or last market day) or not | Boolean |  | No | `true` |
| Extract Stock Prices of Last 30 Days | `extract_stock_prices_last_30_days` | Whether to extract stocks prices of last 30 days or not | Boolean |  | No | `true` |

### Market Trends

Get Market Trends from Google Finance.

#### Inputs

| Input Name | Input Code | Description | Type | Constraints | Required | Default |
| --- | --- | --- | --- | --- | --- | --- |
| Action | `action` | Perform extraction of market trends from Google Finance | String | Pass `"market_trends"` to perform this action | Yes | `"stocks_details"` |
| Country | `country` | 2 letters country code (ISO 3166-2) | String | Valid country code | No | `"us"` |
| Language | `language` | 2 letters language code (ISO 639-1) | String | Valid language Code | No | `"en"` |
| Market Trends | `market_trends_types` | List of Market Trends | Array of Strings | Valid market trends types: See **Market Trends List** | Yes | `["most-active"]` |

#### Market Trends List

Market Trends and Their Code

> Indexes: `"indexes"`
> 
> Indexes in Americas: `"indexes_americas"`
> 
> Indexes in Europe, Middle East, Africa: `"indexes_europe-middle-east-africa"`
> 
> indexes in Asia Pacific: `"indexes_asia-pacific"`
> 
> Most Active: `"most-active"`
> 
> Gainers: `"gainers"`
> 
> Losers: `"losers"`
> 
> Climate Leaders: `"climate-leaders"`
> 
> Cryptocurrencies: `"cryptocurrencies"`
> 
> Currencies: `"currencies"`

### Search Stocks

Search Stocks in Google Finance.

#### Inputs

| Input Name | Input Code | Description | Type | Constraints | Required | Default |
| --- | --- | --- | --- | --- | --- | --- |
| Action | `action` | Perform search of stocks from Google Finance | String | Pass `"search_stocks"` to perform this action | Yes | `"stocks_details"` |
| Country | `country` | 2 letters country code (ISO 3166-2) | String | Valid country code | No | `"us"` |
| Language | `language` | 2 letters language code (ISO 639-1) | String | Valid language Code | No | `"en"` |
| Search Stocks | `search_stocks` | Search text (e.g. `"apple"`) | String |  | Yes |  |

## Proxy

`proxy` object should be defined by the required proxy technique.

The following section will help to define the `proxy` object.

### Data Center Proxies

| Field | Description | Type | Default |
| --- | --- | --- | --- |
| `useApifyProxy` | Whether to use Apify Proxies. | Boolean | `true` |
| `apifyProxyCountry` | Taking Data Center proxies of specific country. 2 letters country code (ISO 3166-2) If blank the proxies can be taken from anywhere. | String |  |

### Residential Proxies

| Field | Description | Type | Default |
| --- | --- | --- | --- |
| `useApifyProxy` | Whether to use Apify Proxies. | Boolean | `true` |
| `apifyProxyGroups` | Specify `["RESIDENTIAL"]` to use residential proxy. | Array of String |  |
| `apifyProxyCountry` | Taking residential proxies of specific country. 2 letters country code (ISO 3166-2) If blank the proxies can be taken from anywhere. | String |  |

### Special Proxies

| Field | Description | Type | Default |
| --- | --- | --- | --- |
| `useApifyProxy` | Whether to use Apify Proxies | Boolean | `true` |
| `apifyProxyGroups` | Specify `["GOOGLE_SERP"]` to use special proxy. Other groups can be specified here - Search that in Apify for more information. | Array of String |  |
| `apifyProxyCountry` | Taking residential proxies of specific country. 2 letters country code (ISO 3166-2) If blank the proxies can be taken from anywhere. | String |  |

### Own Proxies

| Field | Description | Type | Default |
| --- | --- | --- | --- |
| `useApifyProxy` | Whether to use Apify Proxies. Pass `false` to use your own proxies. | Boolean | `true` |
| `proxyUrls` | Specify your own proxies in an array of string with this format: `http://username:password@my-proxy.example.com:port` | Array of String | `[]` |

### No Proxies

| Field | Description | Type | Default |
| --- | --- | --- | --- |
| `useApifyProxy` | Whether to use Apify Proxies. Pass `false` to run without proxies. | Boolean | `true` |