# K-Data Lab MCP: Korean data and e-commerce tools for AI agents

Give Claude, ChatGPT, Cursor, VS Code or any MCP client direct tools for data that is hard to get elsewhere:
**Korean music charts (Melon, Genie, Bugs, FLO, VIBE), Korean apartment prices (KB부동산)**, Amazon ratings,
Google Play reviews, Google Ads Transparency and Agoda hotel prices.

Every tool is a [K-Data Lab](https://apify.com/k-data-lab) actor on the Apify Store, served through
[Apify's hosted MCP server](https://mcp.apify.com). Nothing to install or host: add one URL to your client and the
tools appear by name, so the agent doesn't have to search for them.

- No login or cookies needed for the data (except Seller Central, which reads your own account).
- Pay per result on your own Apify account; the Apify Free plan includes $5 of credit every month.
- Results come back as clean JSON rows the agent can read, filter or export.

## Quick start

1. Get an Apify API token: [console.apify.com/settings/integrations](https://console.apify.com/settings/integrations) (free account).
2. Add the server to your client. The example below loads the Korea bundle; see [all bundles](#bundles).

**Claude Code**
```bash
claude mcp add --transport http k-data-lab "https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper,k-data-lab/kbland-scraper" \
  --header "Authorization: Bearer <YOUR_APIFY_TOKEN>"
```

**Claude Desktop, Cursor, VS Code, Windsurf** (any client that takes `mcpServers` JSON):
```json
{
  "mcpServers": {
    "k-data-lab-korea": {
      "url": "https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper,k-data-lab/kbland-scraper",
      "headers": {
        "Authorization": "Bearer <YOUR_APIFY_TOKEN>"
      }
    }
  }
}
```

Clients that support OAuth can drop the header: they will open an Apify sign-in the first time.

3. Ask in plain words:
   - "What's #1 on Melon, Genie and Bugs right now? Is it an all-kill?"
   - "지난주 멜론 주간 차트 TOP 10 보여줘"
   - "What is the KB price for 은마아파트 76㎡, and how did it change over 5 years?"
   - "Check the rating and review count of B0F497T8NG on Amazon US, UK and Japan."
   - "Get the 1★ and 2★ Google Play reviews of com.spotify.music from the last 7 days."
   - "Which ads is hubspot.com running on YouTube?"
   - "Cheapest 4★+ Agoda hotels in Shinjuku for 2 adults, Dec 20–23."

## Tools

| Data | Actor (tool) | What you get | Price (Apify Free plan) |
|---|---|---|---|
| K-pop charts, all platforms | [`k-data-lab/korean-music-chart-scraper`](https://apify.com/k-data-lab/korean-music-chart-scraper) | Melon, Genie, Bugs, FLO and VIBE charts in one table, with all-kill detection | $0.25 / 1,000 songs |
| Melon | [`k-data-lab/melon-scraper`](https://apify.com/k-data-lab/melon-scraper) | Melon TOP100/HOT100/daily/weekly charts, songs, likes, albums, artists | $0.25 / 1,000 songs |
| Genie | [`k-data-lab/genie-scraper`](https://apify.com/k-data-lab/genie-scraper) | Genie charts with total plays and unique listeners per song | $0.25 / 1,000 songs |
| Bugs | [`k-data-lab/bugs-scraper`](https://apify.com/k-data-lab/bugs-scraper) | Bugs realtime/daily/weekly charts, likes, credits | $0.25 / 1,000 songs |
| FLO | [`k-data-lab/flo-scraper`](https://apify.com/k-data-lab/flo-scraper) | FLO charts with chart score and popularity index | $0.25 / 1,000 songs |
| NAVER VIBE | [`k-data-lab/vibe-scraper`](https://apify.com/k-data-lab/vibe-scraper) | VIBE charts, past charts, ISRC | $0.25 / 1,000 songs |
| KB부동산 (KB Land) | [`k-data-lab/kbland-scraper`](https://apify.com/k-data-lab/kbland-scraper) | Korean apartment KB prices (sale, 전세, 월세) per unit type, last deals, 20-year monthly price history, region prices | $0.006 / complex |
| Amazon ratings | [`k-data-lab/amazon-asin-rating-scraper`](https://apify.com/k-data-lab/amazon-asin-rating-scraper) | Star rating, review count, 5★–1★ split, BSR, "bought in past month" for any ASIN on 19 marketplaces | $1 / 1,000 ASINs |
| Amazon Seller Central reviews | [`k-data-lab/amazon-seller-central-review-scraper`](https://apify.com/k-data-lab/amazon-seller-central-review-scraper) | Your own brand's customer reviews from Seller Central, for monitoring | $3 / 1,000 reviews |
| Google Play | [`k-data-lab/google-play-scraper`](https://apify.com/k-data-lab/google-play-scraper) | App details, exact installs, reviews with stars, version and developer reply | $0.06 / 1,000 reviews |
| Google Ads Transparency | [`k-data-lab/google-ad-library-scraper`](https://apify.com/k-data-lab/google-ad-library-scraper) | Every ad a domain or brand runs on Search, YouTube, Shopping, Maps and Play; monitor mode returns only new ads | $0.90 / 1,000 ads |
| Agoda | [`k-data-lab/agoda-scraper`](https://apify.com/k-data-lab/agoda-scraper) | Hotel prices per night and total with taxes, every room and rate plan, cancellation terms, reviews | $1.50 / 1,000 hotels |

Prices are the per-event prices on the Apify Free plan at the time of writing; other Apify plans have their own tier prices.
Each actor's Store page shows the current price for your plan. A small start fee applies per run.

## Bundles

Load only what you need. Fewer tools keep the agent's context small.

| Bundle | Config file | MCP URL |
|---|---|---|
| `korea` | [configs/korea.json](configs/korea.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper,k-data-lab/kbland-scraper` |
| `kpop-charts` | [configs/kpop-charts.json](configs/kpop-charts.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper` |
| `korean-real-estate` | [configs/korean-real-estate.json](configs/korean-real-estate.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/kbland-scraper` |
| `amazon-seller` | [configs/amazon-seller.json](configs/amazon-seller.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/amazon-asin-rating-scraper,k-data-lab/amazon-seller-central-review-scraper` |
| `app-and-ads` | [configs/app-and-ads.json](configs/app-and-ads.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/google-play-scraper,k-data-lab/google-ad-library-scraper` |
| `travel` | [configs/travel.json](configs/travel.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/agoda-scraper` |
| `all` | [configs/all.json](configs/all.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper,k-data-lab/kbland-scraper,k-data-lab/amazon-asin-rating-scraper,k-data-lab/amazon-seller-central-review-scraper,k-data-lab/google-play-scraper,k-data-lab/google-ad-library-scraper,k-data-lab/agoda-scraper` |

`actors,docs` keeps Apify's own search and docs tools available next to ours. Remove them for a minimal tool list.

## FAQ

**Is this official?** No. These are independent tools. They are not affiliated with Melon, Genie, Bugs, FLO, NAVER, KB국민은행,
Amazon, Google or Agoda.

**Who pays?** You, on your own Apify account, only for the results returned. There is no subscription.

**Can I call them without MCP?** Yes. Every actor has a REST API, and integrations for n8n, Make and Zapier. See its Store page.

**Something broke or a field is missing?** Open an issue on the actor's Store page (Issues tab) or here.

## License

The configs and docs in this repository are MIT licensed. The actors are separate products on the Apify Store.
