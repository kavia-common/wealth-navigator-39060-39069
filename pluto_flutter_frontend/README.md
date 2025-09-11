# Pluto Flutter Frontend

Pluto is an AI-powered wealth copilot for iOS and Android. This Flutter app implements:
- 5-tab refined navigation (Dashboard, Ratings, AI Q&A, Portfolio, Learn/Community)
- Dashboard: market overview, alerts, top movers
- Traffic-light stock ratings with rationale and composite score
- AI-powered stock Q&A
- Portfolio syncing flows (Plaid and brokers) with mock endpoints
- Wealth growth simulator and passive income calculator
- Interactive financial lessons
- Community leaderboard and peer features
- Multi-tier monetization ready (premium flags via local storage)
- Environment-driven configuration with `.env`
- Yahoo Finance public-API quote integration for near real-time prices

## Run

1. Create a `.env` file at project root (or copy `.env.example`):
```
API_BASE_URL=https://mock.pluto.local
WS_URL=wss://mock.pluto.local/ws
```
Note: Yahoo Finance integration uses public endpoints and requires no extra client-side keys.
2. Get packages and run:
```
flutter pub get
flutter run
```

## Architecture

- State management: Provider
- Services: ApiClient (env-based), YahooFinanceService (quotes), MockServices for dev
- Storage: SharedPreferences
- Routing: AppRouter (centralized)
- Theming: Material 3 with ColorScheme.surface
- Strict async UI safety: No context/controller usage after await (see AI tab)
- Feature Providers:
  - MarketProvider: quotes, alerts, polling
  - RatingsProvider: traffic-light signals from momentum (demo heuristic)
  - AIProvider: mock AI responses
  - PortfolioProvider: holdings, linking flows, simulator, passive income
  - LearningProvider: lessons and leaderboard

## Replace mocks with backend
- Swap MockServices methods with ApiClient endpoints described in INTEGRATION_NOTES.md.
- Proxy Yahoo requests through backend for production.

## Testing
- Add widget/integration tests as the backend stabilizes.
