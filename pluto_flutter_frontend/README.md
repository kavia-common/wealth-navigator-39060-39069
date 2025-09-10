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

## Run

1. Create a `.env` file at project root with the following (example):
```
API_BASE_URL=https://mock.pluto.local
WS_URL=wss://mock.pluto.local/ws
```
2. Get packages and run:
```
flutter pub get
flutter run
```

## Architecture

- State management: Provider
- Services: ApiClient (env-based), MockServices for dev
- Storage: SharedPreferences wrapper
- Routing: AppRouter (centralized)
- Theming: Material 3 with ColorScheme.surface
- Strict async UI safety: No context/controller usage after await (see QATab)

This app is ready to integrate with real backend services by replacing `MockServices` calls with `ApiClient` requests.
