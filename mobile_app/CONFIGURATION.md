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
  - Android: Add your key to AndroidManifest.xml as shown below.
  - iOS: Add your key in AppDelegate if/when iOS target added.

Android setup
- Grant location permission and Internet.
- For local dev against backend, use http://10.0.2.2:<port> as API_BASE_URL.

Example .env (copy to .env)
APP_ENV=development
API_BASE_URL=http://10.0.2.2:8000
MAPS_API_KEY=REQUIRED_GOOGLE_MAPS_API_KEY
SUPABASE_URL=
SUPABASE_ANON_KEY=
STRIPE_PUBLISHABLE_KEY=
FCM_SENDER_ID=

AndroidManifest additions (android/app/src/main/AndroidManifest.xml)
<manifest ...>
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
  <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
  <uses-permission android:name="android.permission.INTERNET"/>
  <application ...>
    <meta-data
      android:name="com.google.android.geo.API_KEY"
      android:value="${MAPS_API_KEY}"/>
  </application>
</manifest>

Environment
- APP_ENV: development|staging|production.

Setup Steps
1) cp .env.example .env and set values.
2) Ensure pubspec.yaml includes:
   assets:
     - .env
3) For Android network calls to localhost backend, use http://10.0.2.2:<port>.
4) Provide corresponding server keys (FCM, Stripe secret) only on backend, not here.
