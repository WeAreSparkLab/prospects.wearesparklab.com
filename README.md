# SparkLab Prospects

**A single-page installable app for finding and tracking local-business prospects, with a map, a call list and outreach tools.**

**Live app:** [prospects.wearesparklab.com](https://prospects.wearesparklab.com/) (login required)

An internal tool I built to run SparkLab's outreach. It's open source so you can see how it's put together. The data lives in a private Supabase project behind a login.

## Features

- **Find prospects** and view them as a list, table or **map** (Leaflet).
- **Website checks:** filter by whether a business has a website, a weak website, or one that's down.
- **My list:** add prospects individually or in bulk, and track call outcomes such as no answer, spoke and interested, or not interested.
- **Call sheets:** download a CSV call sheet, and import or export CSV.
- **Outreach:** mark messages as sent and open a draft in Gmail.
- **Installable (PWA)** with a service worker.
- **Login:** Supabase email and password auth, with each user's data stored per account.

## Tech stack

- Single `index.html` in plain JavaScript, with Leaflet bundled in `lib/`
- Supabase: Auth (password grant with token refresh) and a `user_data` table accessed over the REST API
- Web app manifest and service worker
- Static site, no server code

## Run it locally

```bash
git clone https://github.com/WeAreSparkLab/prospects.wearesparklab.com.git
cd prospects.wearesparklab.com
npx serve .        # or open index.html in a browser
```

To run against your own Supabase project, replace `SB_URL` and `SB_ANON` in `index.html` with your values from **Project Settings -> API**, and create a `user_data` table with RLS so each user can only access their own row.

## Security model

The anon key in `index.html` is designed to be public. Data is protected by Row Level Security and by signing in, not by hiding the key. Never commit a `service_role` key.

## What I'd improve next

- Split the single file into modules and add a build step.
- Add automated tests for the CSV import and filtering logic.
- Move from one `user_data` blob to normalised tables, so prospects can be queried and shared across a team.
