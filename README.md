# K-Data Lab MCP: Korean data and e-commerce tools for AI agents

Give Claude, ChatGPT, Cursor, VS Code or any MCP client direct tools for data that is hard to get elsewhere:
**Korean music charts (Melon, Genie, Bugs, FLO, VIBE), Korean apartment prices (KB부동산, 부동산114)**, Amazon ratings,
Google Play and App Store reviews, Google Ads Transparency and Trends, Agoda and Airbnb prices, live Alaska Airlines award seats, Amazon reviews, search ranks and Best Sellers, TikTok, YouTube, X and Pinterest, Google Maps leads, food delivery menus, job listings and public Telegram channels.

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
claude mcp add --transport http k-data-lab "https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper,k-data-lab/kbland-scraper,k-data-lab/r114-scraper" \
  --header "Authorization: Bearer <YOUR_APIFY_TOKEN>"
```

**Claude Desktop, Cursor, VS Code, Windsurf** (any client that takes `mcpServers` JSON):
```json
{
  "mcpServers": {
    "k-data-lab-korea": {
      "url": "https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper,k-data-lab/kbland-scraper,k-data-lab/r114-scraper",
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
   - "Find business class award seats from LAX to Tokyo in December on Alaska miles."
   - "What did public Telegram channels say about this topic this week?"
   - "Which Amazon US bestsellers in Phone Cases moved up this week?"
   - "Pull the top comments on this YouTube video and summarize the complaints."
   - "Find dentists in Austin with phone numbers and emails."

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
| 부동산114 (R114) | [`k-data-lab/r114-scraper`](https://apify.com/k-data-lab/r114-scraper) | Korean apartment R114 sale and jeonse prices per unit type, up to 10 years of weekly prices, actual deals, district price lists | $4.00 / 1,000 complexes |
| Agoda | [`k-data-lab/agoda-scraper`](https://apify.com/k-data-lab/agoda-scraper) | Hotel prices per night and total with taxes, every room and rate plan, cancellation terms, reviews | $1.50 / 1,000 hotels |
| Airline award seats | [`k-data-lab/airline-award-seat-scraper`](https://apify.com/k-data-lab/airline-award-seat-scraper) | Live Alaska Airlines award search, with partner awards: points, taxes, seats left, cabin and flights for any route and date | $1.00 / 1,000 award options |
| Telegram | [`k-data-lab/telegram-channel-scraper`](https://apify.com/k-data-lab/telegram-channel-scraper) | Keyword search across public channels and channel message history, with views and reactions, no account needed | $1.40 / 1,000 keyword matches, $0.30 / 1,000 messages |
| Amazon reviews | [`k-data-lab/amazon-reviews-scraper`](https://apify.com/k-data-lab/amazon-reviews-scraper) | Reviews by ASIN or URL on 20 Amazon sites: rating, text, date, variant, verified badge, photos, star split and Amazon's AI "Customers say" summary | 100 free reviews / month |
| Amazon search | [`k-data-lab/amazon-search-scraper`](https://apify.com/k-data-lab/amazon-search-scraper) | Keyword search results on 22 marketplaces: organic and sponsored rank, ASIN, price, rating, reviews; track keyword rank changes between runs | $0.40 / 1,000 results |
| Amazon Best Sellers | [`k-data-lab/amazon-bestsellers-scraper`](https://apify.com/k-data-lab/amazon-bestsellers-scraper) | Top 100 of any Best Sellers or New Releases list on 22 marketplaces, with rank changes since your last run | $0.40 / 1,000 items |
| App Store | [`k-data-lab/app-store-scraper`](https://apify.com/k-data-lab/app-store-scraper) | iOS app details, reviews past the 500 RSS cap, rating histogram, version history, search ranks and top charts in 72 countries | $0.06 / 1,000 reviews |
| Google Trends | [`k-data-lab/google-trends-scraper`](https://apify.com/k-data-lab/google-trends-scraper) | Interest over time, regions, related and rising queries, compare up to 5 keywords, Trending now by country | $0.002 / keyword report |
| Airbnb | [`k-data-lab/airbnb-scraper`](https://apify.com/k-data-lab/airbnb-scraper) | Listings by city or link with the real price for your dates, availability calendar and occupancy, details and guest reviews | $1 / 1,000 listings |
| TikTok | [`k-data-lab/tiktok-scraper`](https://apify.com/k-data-lab/tiktok-scraper) | Video stats, engagement rate, transcripts and exact follower counts from links or usernames | $0.25 / 1,000 videos |
| YouTube | [`k-data-lab/youtube-scraper`](https://apify.com/k-data-lab/youtube-scraper) | Video and channel stats and metadata by link, search, channel or playlist: exact views, likes, comment count, subscribers | from $1 / 1,000 full videos |
| YouTube comments | [`k-data-lab/youtube-comments-scraper`](https://apify.com/k-data-lab/youtube-comments-scraper) | Comments and replies from any video or Short: text, likes, reply count, date, author, pinned, creator heart | $0.25 / 1,000 comments |
| X (Twitter) | [`k-data-lab/x-tweet-scraper`](https://apify.com/k-data-lab/x-tweet-scraper) | Tweet data and MP4 video links from tweet URLs or IDs: text, likes, replies, media, threads, polls, Community Notes | $0.09 / 1,000 tweets |
| Pinterest | [`k-data-lab/pinterest-scraper`](https://apify.com/k-data-lab/pinterest-scraper) | Pins, video pins, boards and profiles from search terms or links: saves, outbound links, images, product prices | from $0.90 / 1,000 pins |
| Google Maps | [`k-data-lab/google-maps-scraper`](https://apify.com/k-data-lab/google-maps-scraper) | Business leads by search, area, link or place ID: phone, website, emails and socials, address, hours, rating | from $0.40 / 1,000 places |
| Uber Eats and Deliveroo | [`k-data-lab/uber-eats-deliveroo-scraper`](https://apify.com/k-data-lab/uber-eats-deliveroo-scraper) | Restaurants, full menus, dish prices, delivery fees, ratings and hours by address or link | per restaurant, see Store page |
| ATS jobs | [`k-data-lab/ats-jobs-scraper`](https://apify.com/k-data-lab/ats-jobs-scraper) | Open jobs from company career sites on Greenhouse, Lever, Ashby, Workday, Workable, Rippling and more | $0.80 / 1,000 jobs |
| NaukriGulf jobs | [`k-data-lab/naukrigulf-jobs-scraper`](https://apify.com/k-data-lab/naukrigulf-jobs-scraper) | Jobs in the UAE, Saudi Arabia, Qatar, Kuwait, Oman and Bahrain: title, company, salary, skills, full description | $0.30 / 1,000 jobs |

Prices are the per-event prices on the Apify Free plan at the time of writing; other Apify plans have their own tier prices.
Each actor's Store page shows the current price for your plan. A small start fee applies per run.

## Bundles

Load only what you need. Fewer tools keep the agent's context small.

| Bundle | Config file | MCP URL |
|---|---|---|
| `korea` | [configs/korea.json](configs/korea.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper,k-data-lab/kbland-scraper,k-data-lab/r114-scraper` |
| `kpop-charts` | [configs/kpop-charts.json](configs/kpop-charts.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper` |
| `korean-real-estate` | [configs/korean-real-estate.json](configs/korean-real-estate.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/kbland-scraper,k-data-lab/r114-scraper` |
| `amazon-seller` | [configs/amazon-seller.json](configs/amazon-seller.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/amazon-asin-rating-scraper,k-data-lab/amazon-seller-central-review-scraper,k-data-lab/amazon-reviews-scraper,k-data-lab/amazon-search-scraper,k-data-lab/amazon-bestsellers-scraper` |
| `app-and-ads` | [configs/app-and-ads.json](configs/app-and-ads.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/google-play-scraper,k-data-lab/app-store-scraper,k-data-lab/google-ad-library-scraper,k-data-lab/google-trends-scraper` |
| `travel` | [configs/travel.json](configs/travel.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/agoda-scraper,k-data-lab/airbnb-scraper,k-data-lab/airline-award-seat-scraper` |
| `telegram` | [configs/telegram.json](configs/telegram.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/telegram-channel-scraper` |
| `social-media` | [configs/social-media.json](configs/social-media.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/tiktok-scraper,k-data-lab/youtube-scraper,k-data-lab/youtube-comments-scraper,k-data-lab/x-tweet-scraper,k-data-lab/pinterest-scraper,k-data-lab/telegram-channel-scraper` |
| `jobs` | [configs/jobs.json](configs/jobs.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/ats-jobs-scraper,k-data-lab/naukrigulf-jobs-scraper` |
| `local-business` | [configs/local-business.json](configs/local-business.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/google-maps-scraper,k-data-lab/uber-eats-deliveroo-scraper` |
| `all` | [configs/all.json](configs/all.json) | `https://mcp.apify.com?tools=actors,docs,k-data-lab/korean-music-chart-scraper,k-data-lab/melon-scraper,k-data-lab/genie-scraper,k-data-lab/bugs-scraper,k-data-lab/flo-scraper,k-data-lab/vibe-scraper,k-data-lab/kbland-scraper,k-data-lab/r114-scraper,k-data-lab/amazon-asin-rating-scraper,k-data-lab/amazon-seller-central-review-scraper,k-data-lab/amazon-reviews-scraper,k-data-lab/amazon-search-scraper,k-data-lab/amazon-bestsellers-scraper,k-data-lab/google-play-scraper,k-data-lab/app-store-scraper,k-data-lab/google-ad-library-scraper,k-data-lab/google-trends-scraper,k-data-lab/agoda-scraper,k-data-lab/airbnb-scraper,k-data-lab/airline-award-seat-scraper,k-data-lab/telegram-channel-scraper,k-data-lab/tiktok-scraper,k-data-lab/youtube-scraper,k-data-lab/youtube-comments-scraper,k-data-lab/x-tweet-scraper,k-data-lab/pinterest-scraper,k-data-lab/ats-jobs-scraper,k-data-lab/naukrigulf-jobs-scraper,k-data-lab/google-maps-scraper,k-data-lab/uber-eats-deliveroo-scraper` |

`actors,docs` keeps Apify's own search and docs tools available next to ours. Remove them for a minimal tool list.

## FAQ

**Is this official?** No. These are independent tools. They are not affiliated with Melon, Genie, Bugs, FLO, NAVER, KB국민은행,
Amazon, Google, Apple, Agoda, Airbnb, 부동산114, Alaska Airlines, Telegram, TikTok, YouTube, X, Pinterest, Uber Eats, Deliveroo or NaukriGulf.

**Who pays?** You, on your own Apify account, only for the results returned. There is no subscription.

**Can I call them without MCP?** Yes. Every actor has a REST API, and integrations for n8n, Make and Zapier. See its Store page.

**Something broke or a field is missing?** Open an issue on the actor's Store page (Issues tab) or here.

## License

The configs and docs in this repository are MIT licensed. The actors are separate products on the Apify Store.
