# Immutable (IMX) Live Demo

**Live demo: https://immutable-imx-demo.vercel.app/**

An interactive, single-page demo that accompanies our FLCS #3 case study on **Immutable (IMX)** for *Principles of Blockchain Technology*. It turns the claims in the slides into something you can click.

## What it shows

| Tab | Demonstrates |
|---|---|
| **1. Make a trade** | The 5-step flow of an NFT trade: Passport sign-in, mint, orderbook match, sequencer, Ethereum settlement, with the fee split on the price you enter |
| **2. Blocks & sequencer** | A live block feed every 2 s, plus a counter of how many blocks came from the same producer (the single-sequencer trade-off) |
| **3. Fees & gas** | Who receives the money from an NFT sale, and a gas race between Immutable (about 2 s) and Ethereum L1 (about 12 s) |
| **4. Market & liquidity** | Price, market cap, volume, DEX pools and a sell-size price-impact estimate |

## Run it

No install or build step.

1. Download or clone the repository.
2. Open `index.html` in any modern browser.

Or serve it locally: `python3 -m http.server 8000` and visit http://localhost:8000.

## Live vs offline mode

- **Live (default):** fetches current data from CoinGecko, Immutable's RPC and explorer, Ethereum's public RPC and DexScreener. Refreshes every 60 s; blocks every 2 s. Status dot is green.
- **Offline:** press **O** (or click the button) to use a built-in snapshot from 15 Nov 2026 and simulated blocks. If a source fails in live mode, the demo falls back to the snapshot automatically. Status dot is amber.

Keyboard: **1-4** switch tabs, **O** toggles offline mode.

## Notes and limits

- The trade walkthrough is an animation, not a real purchase. Its step timings are simulated; fee percentages and the 2 s block time are real.
- The price-impact curve uses a constant-product (x·y = k) approximation; Uniswap V3 pools behave differently.
- Free public APIs can rate-limit; the snapshot fallback covers this.
- Educational project, not financial advice.

## Project structure

```
immutable-imx-demo/
├── index.html          # the whole demo (HTML, CSS, JS)
├── assets/
│   ├── favicon.svg
│   ├── favicon.png
│   └── apple-touch-icon.png
├── README.md
└── .gitignore
```

## Deployment

Deployed on Vercel: https://immutable-imx-demo.vercel.app/

It is a static site with no build step, so any static host works.

## Data sources

CoinGecko · rpc.immutable.com · explorer.immutable.com · DexScreener · publicnode.com (Ethereum RPC)
