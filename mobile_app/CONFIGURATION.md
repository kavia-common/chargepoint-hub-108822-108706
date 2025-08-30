ChargeMate Mobile App Configuration (Flutter)

This app uses flutter_dotenv to load variables from an .env file bundled as an asset. Copy .env.example to .env and populate values.

Backend
- API_BASE_URL: Base URL of the FastAPI backend.
  - Android emulator: http://10.0.2.2:<port> maps to host localhost.
  - iOS simulator: http://localhost:<port>.

Supabase (Auth)
- SUPABASE_URL: Supabase project URL.
- SUPABASE_ANON_KEY: Public anon key for client-side auth.

Stripe (Client)
- STRIPE_PUBLISHABLE_KEY: Publishable key used by the mobile client to create payment methods/intents.

Notifications (FCM)
- FCM_SENDER_ID: Firebase project sender ID (for device registration and push).

Maps
- MAPS_API_KEY: Google Maps SDK key for mobile map rendering.

Environment
- APP_ENV: development|staging|production.

Setup Steps
1) cp .env.example .env and set values.
2) Ensure pubspec.yaml includes:
   assets:
     - .env
3) For Android network calls to localhost backend, use http://10.0.2.2:<port>.
4) Provide corresponding server keys (FCM, Stripe secret) only on backend, not here.
