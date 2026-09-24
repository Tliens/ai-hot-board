# AI Hot Board · AI 热榜

Live board of AI money-making news, large-model releases and AI deals/free credits — auto-refreshed every 5 minutes.

实时 AI 情报站：AI 创业搞钱 · 大模型动态 · 优惠福利，每 5 分钟自动刷新，新消息从顶部资讯条弹出，点击直达原文。

**URL**: https://tliens.github.io/ai-hot-board/

## How it works / 工作原理

- **Client-side live sources** (real 5-minute freshness): Hacker News (Algolia), dev.to, GitHub Search, Hugging Face — fetched directly in the browser via CORS-enabled public APIs.
- **Server pipeline**: `.github/workflows/update-data.yml` runs every 5 minutes, pulls Google News RSS (zh/en queries per category) + TechCrunch / The Verge / Ars Technica / 爱范儿 / 少数派 feeds, classifies items, and commits `data.json`. The page reads it as one more source.
- **New-item ticker**: unseen items are tracked in `localStorage`; when a poll returns something new, a banner slides down at the top and rotates through the new stories. Click to open the original article.
- **Fallbacks**: live APIs → `data.json` → localStorage cache → bundled seed items.

## Files

- `index.html` — the whole app (single file, no build step)
- `scripts/update-data.mjs` — RSS → `data.json` pipeline (zero dependencies; classification keywords must stay in sync with index.html)
- `data.json` — pipeline output, committed by the Action

## License

MIT
