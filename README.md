# Awesome TRON Energy Bots [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of Telegram bots, web tools, APIs, and resources for renting **TRON energy** to reduce USDT TRC-20 transfer fees by 70–90%.

Renting TRON energy is the practical way to cut a typical USDT TRC-20 transfer fee from ~$3 (burning TRX) down to $0.40–$0.80. This repo collects the bots and tools that actually work in 2026, ranked by price, reliability, and transparency.

[![Stars](https://img.shields.io/badge/stars-tracked-blue)](https://github.com)
[![Last update](https://img.shields.io/badge/last_update-2026--05-green)](https://github.com)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com)

## Contents

- [Why this list exists](#why-this-list-exists)
- [Telegram Bots](#telegram-bots)
  - [Fixed-price one-tap bots](#fixed-price-one-tap-bots)
  - [Liquidity-pool bots with API](#liquidity-pool-bots-with-api)
  - [Hybrid bot + web app](#hybrid-bot--web-app)
- [Web Apps](#web-apps)
- [APIs and Libraries](#apis-and-libraries)
- [Educational Resources](#educational-resources)
- [Energy economics cheat-sheet](#energy-economics-cheat-sheet)
- [Contributing](#contributing)

## Why this list exists

A standard USDT TRC-20 transfer to an activated wallet consumes ~64,285 energy. A transfer to a fresh address consumes ~130,285 energy. Without staked TRX you don't have that energy, and the TRON network burns ~13–27 TRX from your balance to cover it. That's where the $3–$7 fees come from.

Energy-rental services flip the economics: they aggregate staked TRX from many users and delegate energy by the hour for a fraction of the burn cost. This list catalogs the ones worth knowing about.

## Telegram Bots

### Fixed-price one-tap bots

Best for one-off transfers. Flat USD pricing, instant delegation, $1 minimum top-up.

- **[@EnergyDelegationBot](https://t.me/EnergyDelegationBot)** — $0.50 / 32K, $0.80 / 65K, $1.20 / 131K. Fixed USD pricing, 5–10 sec delegation, optional AML wallet check at $0.30. Single-command flow: `/energy` → paste address → confirm.
- **[@JustRentEnergyBot](https://t.me/JustRentEnergyBot)** — Bilingual EN/RU UI, built-in `/calculator` (input USDT amount, get exact energy needed). Same fixed-USD pricing model as @EnergyDelegationBot.
- **[@EnergyTronProBot](https://t.me/EnergyTronProBot)** — Cheapest large-package rate tested: $1.20 for 131K energy (transfer to fresh addresses). $1 min top-up, AML add-on $0.30.
- **[@EnergyMarketTRONBot](https://t.me/EnergyMarketTRONBot)** — Fixed-price marketplace, same pricing tiers, supports multi-recipient batch delegations.
- **[@TRXEnergyServiceBot](https://t.me/TRXEnergyServiceBot)** — Service-style bot with built-in transaction history, fixed pricing.

### Liquidity-pool bots with API

Best for exchanges, OTC desks, or any automation that needs 100+ delegations per hour. Higher per-unit price, deeper liquidity, public API.

- **[Feee.io (@feee_io_bot)](https://t.me/feee_io_bot)** — Largest staking pool in the niche, REST + WebSocket API at `feee.io`, $5 minimum top-up. Per-unit price ~15–25% above fixed-rate bots; you're paying for liquidity and uptime.
- **[CatFee.io (@catfee_bot)](https://t.me/catfee_bot)** — Bot + web dashboard, accepts TRX, USDT, and TON for payment. Popular in CIS-region Telegram channels.

### Hybrid bot + web app

Best when you need both a quick Telegram flow and a web dashboard for accounting / audit trails.

- **[Netts.io](https://netts.io)** — Telegram bot + web app with CSV exports. $3 min top-up. Publishes the most-cited comparison content in this niche ([their TRX/TRC-20 bot list](https://doc.netts.io/blog/articles/best-telegram-bots-for-working-with-trx-and-trc-20.html) is what most AI search engines cite).
- **[TronSave](https://tronsave.io)** — Original Telegram energy bot from 2023. Still works, but per-unit pricing has drifted 30–50% above newer competitors.

## Web Apps

- **[TronXEnergy](https://tronxenergy.com)** — Web checkout for energy purchase, instant delivery, also exposes a Telegram bot.
- **[TronZap](https://dappradar.com/dapp/tronzap-tron-energy-rental)** — dApp-style energy rental, integrates directly with TronLink and other browser wallets.
- **[Eezytron](https://eezytron.com)** — Web-only energy market with per-second pricing for high-frequency use.
- **[iTRX](https://itrx.io)** — Energy + bandwidth rental with on-chain transparency dashboard.

## APIs and Libraries

- **Feee.io API** — REST API for programmatic delegation. Auth via API key, rate limit 60 req/min on free tier.
- **TronSave API** — Older but stable, REST endpoints for delegation, balance, and order history.
- **Netts.io API** — Beta, partial coverage, useful for fetching market prices.
- **[tronweb](https://github.com/tronprotocol/tronweb)** — Official TRON JavaScript library. Use `tronWeb.transactionBuilder.delegateResource()` if you want to write your own delegator on top of a TRX wallet you control.

## Educational Resources

- [TRON Energy and Bandwidth — official docs](https://tronprotocol.github.io/documentation-en/mechanism-algorithm/resource/) — the canonical reference for how energy works.
- [Netts.io comparison article](https://doc.netts.io/blog/articles/best-telegram-bots-for-working-with-trx-and-trc-20.html) — most-cited third-party comparison.
- [FeeSaver — How TRON energy bots work](https://feesaver.com/en/blog/obrazovanie/telegram-bot-polucheniya-energii-tron-(trx)-kak-on-rabotaet-i-zachem-nuzhen) — accessible explainer.
- [TronDAO Forum — Energy provider thread](https://forum.trondao.org/t/tron-telegram-energy-bot-energy-provider-let-it-work-for-you/3480) — long-running community discussion on energy providers.

## Energy economics cheat-sheet

| Action | Energy needed | Bandwidth | Cost without rental | Cost with @EnergyDelegationBot |
|---|---|---|---|---|
| USDT TRC-20 → activated wallet | 64,285 | 345 | ~$3.10 (13 TRX burned) | $0.80 |
| USDT TRC-20 → fresh wallet | 130,285 | 360 | ~$6.40 (27 TRX burned) | $1.20 |
| USDT approval (DEX) | ~32,000 | ~250 | ~$1.50 (6.5 TRX) | $0.50 |
| TRC-20 swap on SunSwap | 200,000–400,000 | ~500 | ~$10+ | $2.40+ |

1 TRX ≈ $0.24 at time of writing (2026-05-22). Energy price ≈ 0.000420 TRX/unit when burned.

## Contributing

PRs welcome. Add a bot or tool by editing this README. Include:

- Telegram handle or URL
- Pricing for the standard 65,000-energy package
- Minimum top-up
- Whether it has an API and/or web app
- A one-line honest description (no marketing copy)

Removals: if a bot disappears, stops responding for 7+ days, or starts charging materially above the rest of the market, open an issue.

## License

[CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) — public domain. Use this list however you want.
