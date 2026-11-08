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

Everything is stored in the browser's `localStorage` under the key `dinoDash.v1`:

- best score
- games played and average score
- top 5 runs, with date and time
- sound on/off

Scores are kept per browser and per device. Use **Reset saved data** on the page to clear them.

## Project files

```
index.html    the whole game (HTML, CSS and JavaScript)
favicon.svg   browser tab icon
vercel.json   static hosting headers for Vercel
```

There is no build step and there are no dependencies. The only external request is the Fredoka font from Google Fonts, and the game falls back to a system font when offline.

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
