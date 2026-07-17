# krill-api

Cloudflare Worker API for the KRILL Robinhood-ready Virtuals launch intelligence terminal.

The Worker serves stable demo/intelligence payloads for the public terminal. It is designed to keep the UI useful before final Robinhood/Virtuals launch addresses are live.

## Endpoints

| Method | Path             | Description                |
|--------|------------------|----------------------------|
| GET    | `/api/status`    | agent status + uptime      |
| GET    | `/api/wallet`    | wallet info                |
| GET    | `/api/deploy`    | deployment status          |
| GET    | `/api/scan`      | scan statistics            |
| GET    | `/api/targets`   | active targets             |
| GET    | `/api/hunt`      | latest intelligence log    |
| GET    | `/api/profit`    | clarity trend breakdown    |
| GET    | `/api/history`   | recent signal history      |
| GET    | `/api/portfolio` | tracked launch briefs      |
| GET    | `/api/pools`     | launch signal lanes        |
| GET    | `/api/log`       | event log                  |
| GET    | `/api/twitter`   | recent mentions            |
| GET    | `/api/gas`       | launch-track fee estimate  |
| GET    | `/api/config`    | agent configuration        |
| GET    | `/api/about`     | about krill                |
| GET    | `/api/watch?token=$KRILL` | live clarity tick |
| POST   | `/api/mode`      | set mode `{mode: "PAUSE"\|"SIGNAL"}` |
| POST   | `/api/bid`       | publish manual note `{token, amount}` |
| POST   | `/api/sell`      | archive launch `{token}`   |

## Develop

```bash
npm install
npm run dev    # → http://localhost:8787
```

The front-end auto-detects `localhost` and points to `http://localhost:8787/api`.

## Deploy

```bash
npm run deploy
```

After deploying, set up a route so the Worker handles `/api/*` on your Pages domain, e.g. `https://krill.example.com/api/*` → `krill-api`.
