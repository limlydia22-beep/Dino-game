# Dino Dash 🦖🌵

An orange-themed endless runner in a single HTML file, inspired by the Chrome offline game. Jump the green cacti, duck the birds, and beat your best score.

## How to play

| Action | Keyboard | Phone |
| --- | --- | --- |
| Start / jump | `Space` or `↑` (hold for a higher jump) | Tap the game or **Jump** |
| Duck / drop fast | `↓` | Hold **Duck** |
| Sound on/off | `M` | 🔊 button |

The game speeds up as you go. Birds appear after 250 points, and day turns to night every 700 points.

## Saved data

**On each device** (`localStorage`, key `dinoDash.v1`): best score, games played, average score, top 5 runs with dates, sound on/off, the player's name, and the best score already posted to the world board. **Reset saved data** clears the scores on that device only.

**World Top 10** (Supabase): once a player saves a name, each new personal best is posted automatically. If posting fails, a **Post my best** button appears so the player can retry. The board shows each name's best score and refreshes every minute when no game is running. Rows marked *demo* are sample data.

### Supabase setup

Project `zzqkkecgnrlgxyevwfbx`. The game calls the REST API directly with `fetch`, so no library is loaded. The URL and publishable key are at the top of the leaderboard code in `index.html`. The publishable key is meant to be public.

| Object | Purpose |
| --- | --- |
| `dino_scores` table | `id`, `name` (1–16 chars: letters, numbers, space, `.` `_` `-`), `score` (1–99,999), `is_example`, `created_at` |
| `dino_leaderboard` view | Best score per name (case-insensitive), `security_invoker` |

Access through the public key: anyone can **read** the board and **insert** a `name` and `score`. Nobody can edit or delete rows, set `is_example`, or choose `created_at`.

**Limits:** there is no sign-in, so anyone can post any name and any score up to 99,999 (for example by calling the API directly). This is fine for a casual game. Remove obviously fake rows in the Supabase dashboard if needed.

To remove the demo scores:

```sql
delete from public.dino_scores where is_example;
```

## Project files

```
index.html    the whole game (HTML, CSS and JavaScript)
favicon.svg   browser tab icon
vercel.json   static hosting headers for Vercel
```

There is no build step and there are no dependencies. The page loads the Fredoka font from Google Fonts and calls Supabase for the world board. Offline, the game still works with a system font and device-only scores.

## Deploy on Vercel

1. In Vercel, choose **Add New → Project** and import this GitHub repository.
2. Leave **Framework Preset** as **Other**. Leave the build command empty and the output directory as the default (the repository root).
3. Click **Deploy**.

Each push to `main` redeploys the site automatically.

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
npx serve .
```
