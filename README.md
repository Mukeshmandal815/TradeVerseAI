# TradeVerseAI
An Intelligent Web and Mobile Stock Exchange Platform with AI-Based Market Analysis and Virtual Trading
# TradeVerse AI
 
TradeVerse AI is a virtual trading platform for Nepal Stock Exchange
(NEPSE) listed companies. Users trade with simulated funds while an AI
microservice explains short-term trend signals and financial-news sentiment.
 

 
## Problem
Learners rarely get a safe, realistic way to practise stock trading. Real
brokerages carry financial risk, and spreadsheets offer no live data, charts,
or intelligence layer.
 
## Solution
TradeVerse AI combines a modular trading engine with a bounded AI layer:
- A MarketDataProvider abstraction sources live or mock NEPSE data.
- A backend-authoritative trading engine executes virtual buy/sell orders.
- XGBoost and LSTM models generate short-term trend predictions.
- FinBERT scores financial-news sentiment per company.
- Every AI output is labelled experimental / educational in the UI.
 
## Features
- Email/password authentication with JWT sessions and password reset flow.
- Dashboard, market, stock detail, trade, portfolio, watchlist, orders,
  transactions, news, AI, profile, settings, and admin screens.
- NEPSE company list, search, sector filters, OHLC, and historical charts.
- Virtual wallet, MARKET/LIMIT orders, holdings, and realized/unrealized P/L.
- Watchlists, price alerts, and real-time notifications.
- AI dashboard: bullish/bearish/neutral view, prediction score, trend signal,
  and news sentiment.
- Admin dashboard for users, audit logs, and model-performance monitoring.
 
## Architecture
```text
Next.js / Flutter UI
        |
   NestJS API
        |
PostgreSQL + Redis
        |
MarketDataProvider + XGBoost/LSTM + FinBERT (FastAPI AI service)
```
The backend owns trading logic, balance validation, and persistence. The AI
service only explains data and drafts trend signals — it never executes trades.
 
## Tech Stack
- Frontend: Next.js, TypeScript, Tailwind CSS, shadcn/ui, ECharts, TanStack
  Query, React Hook Form, Zod.
- Backend: NestJS, TypeScript, Prisma, PostgreSQL, Redis, class-validator.
- AI: Python, FastAPI, Pandas, NumPy, Scikit-learn, XGBoost, TensorFlow/Keras,
  FinBERT.
- Mobile: Flutter, Dart.
- DevOps: Docker, Docker Compose, GitHub Actions, Nginx.
 
## Installation
Requirements:
- Node.js 20 or newer
- Python 3.11 or newer
- Docker Desktop
- PostgreSQL 15 or compatible (or use the provided Docker service)
 
Set up:
```bash
pnpm install
cp .env.example .env
pnpm prisma:migrate
pnpm prisma:seed
```
Update `.env` with your local database URL, a long `JWT_SECRET`, and your
chosen MARKET_DATA_PROVIDER (`mock` or `nepse`).
 
## Running Locally
```bash
docker compose up -d      # postgres, redis
pnpm dev                  # web + api
uvicorn app.main:app --reload   # ai-service
```
- Web: `http://localhost:3000`
- API: `http://localhost:4000/api/v1`
- AI service: `http://localhost:8000`
 
## Useful Commands
```bash
pnpm dev
pnpm build
pnpm lint
pnpm test
pnpm prisma:migrate
pnpm prisma:seed
pytest services/ai-service
```
 
## Documentation
Start with: `docs/SRS.md`, `docs/ARCHITECTURE.md`, `docs/DATABASE.md`,
`docs/API.md`, `docs/AI_MODEL.md`, `docs/DEPLOYMENT.md`, `docs/TESTING.md`.
 
## Limitations
TradeVerse AI supports NEPSE-listed companies and virtual trading only.
Real brokerage execution, multi-exchange support, and options/derivatives
simulation are documented as future work.
 
## License
Educational use — course project for Khulna University, CSE Discipline.
