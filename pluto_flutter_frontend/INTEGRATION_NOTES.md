# Pluto Frontend Integration Notes

## Providers and Features
- MarketProvider: quotes from YahooFinanceService; replace with backend market endpoints to unify data and signals.
- RatingsProvider: compute demo traffic-light from momentum; replace with GET /ratings/{symbol}.
- AIProvider: mock Q&A; replace with POST /ai/qa { symbol, question }.
- PortfolioProvider: mock linking; integrate with POST /portfolio/link/plaid and /portfolio/link/broker, plus GET /portfolio/summary.
- LearningProvider: mock lessons and leaderboard; replace with GET /learn/lessons and GET /community/leaderboard.
- AppStateProvider: local premium flag; replace with real entitlements and backend verification.

## Backend Endpoints
- Configure API_BASE_URL in `.env` to point to your backend.
- Replace MockServices with real ApiClient calls:
  - Market data: GET /market/top-movers, /market/alerts
  - Ratings: GET /ratings/{symbol}
  - Q&A: POST /ai/qa { symbol, question }
  - Portfolio: GET /portfolio/summary; POST /portfolio/link/plaid; POST /portfolio/link/broker
  - Lessons: GET /learn/lessons
  - Community: GET /community/leaderboard
  - Simulator & Passive income can be computed client-side or provided by backend.

## Yahoo Finance Integration (Frontend)
- Uses public Yahoo quote endpoint via `YahooFinanceService` for near real-time prices (no secrets required).
- Default symbols: AAPL, MSFT, NVDA, TSLA, AMZN, GOOGL, META, NFLX, AMD, INTC.
- For production:
  - Proxy Yahoo via backend for rate limits and caching.
  - Replace momentum heuristic with backend-provided composite ratings.

## Monetization
- AppStateProvider.isPremium flag toggles premium UI (stored via SharedPreferences).
- Integrate StoreKit/BillingClient + backend entitlements for real monetization and multi-tier features.

## WebSocket / Real-time
- Use WS_URL from `.env` to connect to signals/alerts channel.
- Not implemented in this mock; providers are structured to add a WebSocket layer later.

## Security
- Do not hardcode secrets. Use `.env` and secure key management for release builds.

## Tests
- A placeholder test exists. Add feature-level widget and integration tests as APIs stabilize.
