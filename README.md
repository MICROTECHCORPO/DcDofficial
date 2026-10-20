# DilloCrocodillo Ecosystem

This repository is the foundation for the DilloCrocodillo ecosystem: storefront, Telegram bot, Web3 engine, product docs, and catalog data.

## Quick project map

- `docs/` — business, product, legal, architecture docs
- `src/store-frontend/` — storefront / landing page
- `src/telegram-bot/` — Telegram shop and community bot
- `src/web3-engine/` — smart contracts, memecoin logic, blockchain tools
- `data/catalog/` — product metadata in JSON

## 8-step quick start

1. Clone the project
   ```bash
   git clone https://github.com/MICROTECHCORPO/DcDofficial.git
   cd DcDofficial
   ```

2. Copy environment variables
   ```bash
   cp .env.example .env
   ```

3. Install required local tools
   - Docker + Docker Compose
   - Node.js 18+
   - Python 3.11+
   - Git

4. Start the local foundation services
   ```bash
   make up
   ```
   This starts the local database and Redis stack.

5. Check that services are healthy
   ```bash
   docker compose ps
   ```

6. Install app dependencies separately for each module
   ```bash
   cd src/store-frontend && npm install
   cd ../telegram-bot && python -m venv .venv && source .venv/bin/activate && pip install -r requirements.txt
   ```

7. Run each module locally
   ```bash
   cd src/store-frontend && npm run dev
   cd src/telegram-bot && python bot.py
   ```

8. Open the app and validate the flow
   - Store: http://localhost:3000
   - Telegram bot: run in your local bot environment using your token
   - API/health checks: http://localhost:8000/health

## Environment variables

Copy `.env.example` into `.env` and adjust values before starting local services.

## Useful commands

```bash
make up        # start containers
make down      # stop containers
make logs      # tail logs
make test      # run app validation scripts
```

## Production-ready roadmap

- Add storefront build pipeline
- Add Telegram bot handlers for marketplace, cards, and wallet
- Add Web3 contract deploy and buyback scripts
- Connect product catalog to store and bot data
- Add monitoring, CI, and deployment automation

## Recommended next actions

1. Create a frontend app in `src/store-frontend/`
2. Create an API or bot service for NFC verification
3. Connect product data from `data/catalog/*.json`
4. Add `README` docs and deployment workflow per module

## License

MIT
