# NameHim

Static Cloudflare Pages-ready site with Supabase-backed browsing/submission flows.

## Environment configuration

Set the config object in a small script before `index.html` app logic in production:

```html
<script>
  window.NAMEHIM_CONFIG = {
    SUPABASE_URL: 'https://YOUR_PROJECT.supabase.co',
    SUPABASE_ANON_KEY: 'YOUR_ANON_KEY',
    TURNSTILE_SITE_KEY: 'YOUR_TURNSTILE_SITE_KEY'
  };
</script>
```

## Supabase setup

1. Run the SQL in `supabase.sql`.
2. Enable Realtime for `public.reports` table.
3. Enable Anonymous sign-ins in Supabase Auth settings.
4. (Recommended for production) Verify Turnstile tokens server-side via a Cloudflare Worker / Supabase Edge Function before insert.

## Run locally

Open `index.html` in a static server (for example `python3 -m http.server`).
