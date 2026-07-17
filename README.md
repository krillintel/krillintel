# KRILL

**AI-Powered Trading Intelligence on Robinhood Chain**

KRILL is a launch-intelligence terminal for the Virtuals Protocol ecosystem on Robinhood Chain (EVM, chainId 4663). It pairs a live web terminal UI with a Cloudflare Worker API that surfaces agent status, clarity signals, and launch tracking.

🌐 Live: [krill.live](https://krill.live)

---

## Stack

- **Frontend** — static landing page + terminal UI (vanilla JS, no framework)
- **API** — Cloudflare Worker (`worker/`), reads on-chain data via EVM `eth_*` RPC
- **Tests** — Vitest (31 unit tests covering all routes)

## Structure

```
index.html          # landing + terminal UI
css/                # landing.css, style.css
js/                 # api.js (client), app.js (terminal logic)
worker/             # Cloudflare Worker API
  src/index.js      #   all routes (status, wallet, scan, hunt, ...)
  src/index.test.js #   Vitest suite
  wrangler.toml     #   Worker config
```

## Develop

Frontend is static — open `index.html` or serve it. The terminal auto-detects `localhost` and points to the local Worker.

```bash
cd worker
npm install
npm run dev      # → http://localhost:8787
npm test         # run the test suite
```

## Deploy

```bash
cd worker
npx wrangler secret put RPC_URL   # Robinhood Chain RPC endpoint
npm run deploy
```

Route `/api/*` on your Pages domain to the `krill-api` Worker. See [worker/README.md](worker/README.md) for the full endpoint reference.

## Chain

- **Network:** Robinhood Chain (EVM)
- **Chain ID:** 4663
- **Token:** $KRILL (Virtuals Protocol)
