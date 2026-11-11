# KopiTraders Intermarket Analyzer — Android starter

This is a native Android (Kotlin + Jetpack Compose) starter dashboard for XAUUSD intermarket analysis.

## Current status
- Android dashboard UI scaffold is included.
- Live feeds are **not connected yet**. The dashboard intentionally displays dashes and `WAIT FOR LIVE DATA`; it does not fabricate prices or signals.
- API keys are not included in the project.

## Planned live data sources
A production build needs a licensed/reliable provider and API keys:
- Spot gold and silver: market-data provider that explicitly supports XAU/USD and XAG/USD.
- DXY: provider supporting the US Dollar Index (or a clearly identified proxy; do not silently substitute).
- US nominal and real yields: FRED series `DGS10` and `DFII10` (daily, not tick-by-tick).
- Fed expectations: a provider with a permitted Fed-funds futures / probability feed. Otherwise label it manual and timestamp it.

Do not call this feed “live” unless the provider's update frequency and entitlements support that claim. FRED yield series are daily observations, not real-time intraday prices.

## Build
1. Open this folder in Android Studio (Hedgehog or newer).
2. Let Gradle sync.
3. Build > Build Bundle(s) / APK(s) > Build APK(s).

## Next implementation steps
1. Choose a market-data vendor and obtain API keys.
2. Implement provider-specific Retrofit services and rate-limit/cache handling.
3. Add timestamps, stale-data warnings, market-session status, and retry/error states.
4. Validate correlations on aligned timeframes before calculating a bias score.
5. Add risk calculator (entry, stop-loss, lot size, risk in USD and % equity).

Never put production API keys directly in a distributed APK. Use a backend proxy to protect secrets and respect provider terms.
