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

## Monetization
- AppStateProvider.isPremium flag toggles premium UI (currently stored locally).
- Integrate real entitlements (StoreKit BillingClient) and set flag via backend.

## WebSocket / Real-time
- Use WS_URL from `.env` to connect to signals/alerts channel.
- Not implemented in this mock; ready for future integration.

## Security
- Do not hardcode secrets. Use `.env` and secure key management for release builds.

## Tests
- Basic placeholder test included. Add widget and integration tests per feature as backend stabilizes.
