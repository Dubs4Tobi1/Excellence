# Excellence Properties

Standalone property website built with **React + JSX + Vite**. It does not depend on the existing Excellence Properties repository.

## Included

- White and warm gold Excellence Properties home page.
- Dedicated Zylus Homes and Blue Earth Properties pages.
- WhatsApp inquiry buttons to **08033354167**, prefilled with the listing name.
- Responsive property cards and partner routes.
- Authenticated `/admin` listing dashboard for details, photos and videos.
- Supabase migration for listings, property media, an administrator role table, row-level security and the `property-media` Storage bucket.
- Supplied property advertisements and video in `public/images/`.

## Run locally

```bash
npm install
cp .env.example .env
npm run dev
```

Set `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY` in `.env`. The anon key is safe for browser use when RLS is enabled. Never put a service role key in a Vite variable.

## Set up Supabase

1. Open the Supabase SQL editor and run `supabase/migrations/001_initial.sql`.
2. Create the initial admin user in Supabase Authentication.
3. Copy that user's UUID and add the role from the SQL editor:

```sql
insert into public.user_roles (user_id, role)
values ('AUTH_USER_UUID', 'admin');
```

4. Sign in at `/admin`. Admin uploads accept images and MP4/WebM/QuickTime videos up to 50 MB each. Files are saved to `properties/{id}/images/...` or `properties/{id}/videos/...`; public pages query only published listings.

The migration creates a publicly readable media bucket. Database writes and uploads require a signed-in user whose UUID has an `admin` role. No service key or admin secret is shipped to the browser.

## Build

```bash
npm run build
```
"# Excellence" 
