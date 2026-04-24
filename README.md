# NameHim

Static site hosted on Cloudflare Pages, using Supabase as the backend.  
Users can anonymously submit reports about men who raised concerns (emotional/physical abuse, stalking, sexual assault, rape).  

## Live site

[https://namehim.app](https://namehim.app)

## Tech stack

- HTML/CSS/JS (no build step)
- Tailwind CSS (via CDN)
- Supabase (database + Row Level Security)
- Cloudflare Turnstile (CAPTCHA)
- Cloudflare Pages (hosting)

## Database schema (Supabase)

```sql
CREATE TABLE public.reports (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  city TEXT NOT NULL,
  state TEXT NULL,                 -- optional
  country TEXT NOT NULL,
  categories TEXT[] NOT NULL,      -- array of selected categories
  created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  submitter_uuid TEXT NOT NULL     -- anonymous client‑generated UUID
);

-- RLS policies
ALTER TABLE public.reports ENABLE ROW LEVEL SECURITY;
CREATE POLICY "Anyone can insert reports" ON public.reports FOR INSERT WITH CHECK (true);
CREATE POLICY "Anyone can view reports"   ON public.reports FOR SELECT USING (true);

Environment variables
The frontend hardcodes the following values (you should replace them with your own if you fork):

SUPABASE_URL

SUPABASE_ANON_KEY

TURNSTILE_SITE_KEY

In production, it is recommended to use Cloudflare Pages environment variables instead of hardcoding.

Local development
Run a static server:

bash
python3 -m http.server
Then open http://localhost:8000.

License & contributions
Open source – feel free to fork and improve.
See GitHub Issues for planned features.

text

Copy and paste the entire block above into your GitHub `README.md` file, commit, and push. Your documentation will then match the current live site.
This response is AI-generated, for reference only.
im confused with the markdown with the hashtags it doesnt look right to me
You're right – the markdown I gave uses # for headings, which will render correctly on GitHub. But if you're viewing the raw text and thinking it looks odd, that's normal – GitHub will interpret the # as headings.

If you want a plain text version without any markdown symbols, here it is – ready to copy and paste (it will still appear as plain text on GitHub, no formatting):

text
NameHim

Static site hosted on Cloudflare Pages, using Supabase as the backend.
Users can anonymously submit reports about men who raised concerns (emotional/physical abuse, stalking, sexual assault, rape).

Live site: https://namehim.app

Tech stack:
- HTML/CSS/JS (no build step)
- Tailwind CSS (via CDN)
- Supabase (database + Row Level Security)
- Cloudflare Turnstile (CAPTCHA)
- Cloudflare Pages (hosting)

Database schema (Supabase):

CREATE TABLE public.reports (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  city TEXT NOT NULL,
  state TEXT NULL,
  country TEXT NOT NULL,
  categories TEXT[] NOT NULL,
  created_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
  submitter_uuid TEXT NOT NULL
);

-- RLS policies
ALTER TABLE public.reports ENABLE ROW LEVEL SECURITY;
CREATE POLICY "Anyone can insert reports" ON public.reports FOR INSERT WITH CHECK (true);
CREATE POLICY "Anyone can view reports"   ON public.reports FOR SELECT USING (true);

Environment variables:
The frontend hardcodes the following values (replace with your own if you fork):
- SUPABASE_URL
- SUPABASE_ANON_KEY
- TURNSTILE_SITE_KEY

In production, it is recommended to use Cloudflare Pages environment variables instead of hardcoding.

Local development:
Run a static server: python3 -m http.server
Then open http://localhost:8000

Open source – feel free to fork and improve.
GitHub Issues: https://github.com/namehim/namehim/issues
