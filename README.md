# Avontic ChatGPT product feed

Automatically converts Avontic's existing product feed into ChatGPT JSONL. Uses standard free GitHub Actions in this public repository. No paid runners, caches, artifacts, Pages, LFS, or hosting subscription are used.

- [Hosted feed](https://github.com/avonticofficial-sys/avontic-chatgpt-feed/raw/refs/heads/feed/products.jsonl.gz?feed=chatgpt)
- [Full validation report](https://github.com/avonticofficial-sys/avontic-chatgpt-feed/blob/feed/validation.json)
- [Run history and manual refresh](https://github.com/avonticofficial-sys/avontic-chatgpt-feed/actions/workflows/feed.yml)
- [ChatGPT Business Hub](https://chatgpt.com/business-hub/bizprof_4bfbeafdb7f0819ebf92ad5872457d68/products)

The converter refreshes daily at 17:23 UTC (12:23 PM Eastern standard time / 1:23 PM Eastern daylight time). ChatGPT's hosted connection is configured for daily refreshes. Scheduled jobs can start later than their nominal time.

The source URL is held only in the encrypted SOURCE_FEED_URL repository secret. The converter uses the structured XML source and does not publish that URL or its access token. Public outputs contain public product information only.

Every source variant gets one output row with a stable ID, required ChatGPT discovery fields, current regular and sale prices where supplied, US market settings, and a product URL selecting the correct numeric Shopify variant ID. Source variants with ambiguous option combinations are retained as individual items instead of incorrectly grouped options. This does not enable checkout inside ChatGPT or paid ads.

Before publishing, the workflow checks required fields, USD prices, stock values, numeric variant URLs, duplicate IDs, exact source/output ID coverage, and grouped option uniqueness. It keeps the last published feed if conversion fails. The initial verified catalog contains 44,137 unique variants. The current guard stops publication below that baseline so an unexpected catalog drop must be reviewed; update the guard after confirming legitimate product removals.

GitHub validation proves file coverage and format checks. ChatGPT's full processing result and product eligibility must be checked separately in Business Hub; initial validation or connection alone does not establish that every product is accepted or displayed.
