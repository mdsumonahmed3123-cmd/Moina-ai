# MOiNA AI Official Website
React + Vite + Supabase. Public site reads live from Supabase; admin panel (email+password, then Google Authenticator) manages releases and content.

## Setup
1. Database is already set up (see supabase/migrations). .env is pre-filled with the publishable key.
2. Authentication → Users → add your admin user; turn OFF sign-ups; MFA (TOTP) must be enabled (default).
3. Run: `insert into admin_profiles(id) select id from auth.users where email='YOUR_EMAIL';`
4. `cp .env.example .env`, fill URL + anon key (never the service role key).
5. `npm install && npm run dev`. Open `/#/admin`, sign in, scan the QR in Google Authenticator.
6. Deploy: `npm run build`, upload `dist/` to Netlify/Vercel/Cloudflare Pages, set the two env vars there.

## Test checklist (do before trusting it)
Upload a small APK → Publish → Set latest → open `/#/download` in a private window → download → confirm "completed" count rises.
Supabase free plan caps single uploads at 50 MB; raise the global limit in Storage settings for bigger APKs.

## Not yet built
Language selector, feature/FAQ/social/screenshot/media editors (tables + policies exist), SEO tag injection for crawlers (SPA), upload % bar, contact form.
