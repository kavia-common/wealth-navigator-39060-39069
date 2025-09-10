# Pluto Frontend Integration Notes

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
- The app now integrates public Yahoo Finance quote endpoints via `YahooFinanceService` for near real-time prices.
- Symbols used by default: AAPL, MSFT, NVDA, TSLA, AMZN, GOOGL, META, NFLX, AMD, INTC.
- MarketProvider replaces top movers with real quotes, computes a simple Buy/Hold/Sell signal from momentum (demo only).
- For production usage:
  - Consider proxying Yahoo requests through your backend to control rate limits and add caching.
  - Move any keys/secrets to backend and never store in the mobile app.
  - Replace the simple signal heuristic with backend-provided ratings.

## Monetization
- AppStateProvider.isPremium flag toggles premium UI (currently stored locally).
- Integrate real entitlements (StoreKit BillingClient) and set flag via backend.

## WebSocket / Real-time
- Use WS_URL from `.env` to connect to signals/alerts channel.
- Not implemented in this mock; ready for future integration.

## Security
- Do not hardcode secrets. Use `.env` and secure key management for release builds.
- No Yahoo secrets are stored client-side; the current integration uses public endpoints.

## Tests
- Basic placeholder test included. Add widget and integration tests per feature as backend stabilizes.
