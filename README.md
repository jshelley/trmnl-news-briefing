# News Briefing for TRMNL

A [trmnlp](https://github.com/usetrmnl/trmnlp) recipe that shows one of eleven hourly, LLM-edited news briefings: the lead story with its summary, a two-column grid of ranked stories with one-line summaries, and a QR code on every story that opens the article. Full, half-horizontal, half-vertical and quadrant views.

![Full view on a TRMNL OG](media/screenshot-og.png)

## Use it

- **Hosted TRMNL:** install the public recipe at [trmnl.com/recipes/472511](https://trmnl.com/recipes/472511) and pick a briefing in its settings.
- **Self-hosted BYOS (LaraPaper):** Plugins & Recipes → Add → Import from OSS Catalog → News Briefing → Install. Tested on LaraPaper 0.42.0; it is listed in the [community recipe catalog](https://bnussbau.github.io/trmnl-recipe-catalog/).
- **Your own TRMNL account:** clone this repo, `trmnlp serve` to preview, `trmnlp push` to upload it as a private plugin.

## Briefings

AI Briefing, AI Research, Frontier Labs, Markets & Finance, US Sports, European Football, US News, World News, Crypto & Onchain (all hourly), plus two daily editions: Grants & Funding and Noticias Lentas (Spanish at CEFR B1).

## Data

The recipe polls `https://briefing-service.wholemind.workers.dev/v1/briefings/{key}/summary`, a free endpoint with no key and no rate limit worth mentioning at one poll an hour per device. Every story carries `id`, `short` (a link that opens the article) and `qr` (an SVG QR code of that link). The same service publishes rendered e-ink pages, a Morning Paper for Kindle and reMarkable, and a paid API and MCP server: [briefing-service.wholemind.workers.dev/llms.txt](https://briefing-service.wholemind.workers.dev/llms.txt).

## Layout notes

All text clamps are CSS `-webkit-line-clamp` rather than the framework's `data-clamp`, because the Overflow engine sizes its columns before the JS clamp pass would shrink the lead; CSS clamps are final at layout time. The title bar shows the rank time in the viewer's local time when TRMNL supplies `trmnl.user.utc_offset`, UTC otherwise.

## License

MIT, see [LICENSE](LICENSE).
