# SparkLab Prospects

A single-page PWA (`index.html`) for tracking local-business prospects, with a call list and outreach tools.

## Setup

This is a static app: no build step and no `.env` file.

1. Serve the folder from any static host, or open `index.html` locally.
2. `index.html` ships the Supabase project URL and a **publishable (anon) key**. That key is designed to be public; data is protected by Row Level Security (RLS) and by signing in, not by hiding the key.
3. To run against your own Supabase project, replace `SB_URL` and `SB_ANON` in `index.html` with your own values (Supabase dashboard -> Project Settings -> API). Never commit a `service_role` / secret key.
