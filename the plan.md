# Meme Trend Radar

A live radar for internet culture. It scans Reddit's meme communities, groups
the hottest posts into distinct **formats**, and scores each one by how fast
it's gaining traction — so you can see what's spiking *before* it peaks.

By the time you notice a meme format, it's usually already dead. There's no
Bloomberg terminal for internet culture. This is a small attempt at one.

---

## What it does

- Pulls the current hot posts from `r/memes`, `r/dankmemes`, and
  `r/wholesomememes`.
- Groups them into named meme formats (e.g. *Aura Points*, *POV Format*).
- Scores each format's **heat** from real upvote velocity.
- Plots every format as a blip on a radar scope — hotter formats sit closer to
  the center; pink is rising, blue is cooling, amber is steady.
- Shows up to **3 real thumbnails** per format, pulled live from the actual
  posts.

## How it works

The pipeline runs entirely on a small Flask server, so nothing sensitive or
CORS-blocked happens in the browser:

1. **Fetch** — the server requests each subreddit's `hot.json` feed. Doing this
   server-side sidesteps the browser's cross-origin restrictions and lets us
   read each post's real image URL. NSFW-flagged and pinned posts are filtered
   out.
2. **Cluster** — the server reads all the post titles, finds phrases that recur
   across multiple posts (favoring two-word phrases, which are more specific),
   and groups the posts that share them. Each group becomes a format, named
   after its dominant phrase. A small lookup table upgrades well-known phrases
   to nicer labels ("chill guy" → *Chill Guy*).
3. **Score** — heat is **upvote velocity**: a post's score divided by its age
   in hours, summed across a format's posts, then normalized to 0–100. A
   two-hour-old post outrunning an all-day post ranks higher. Rising vs. cooling
   is approximated from whether a format's posts are newer or older than the
   overall batch.
4. **Display** — the browser calls the server's `/api/scan` endpoint (same
   origin, no keys) and renders the radar scope, a ranked leaderboard, and the
   real thumbnails.

If the live scan ever fails, the page falls back to a bundled sample set
automatically, so the demo never shows a broken screen.

## Running it

```bash
pip install -r requirements.txt
python app.py
```

Then open **http://localhost:5000** and click **Scan now**.

> Important: the real images only appear when you view the page *through* the
> running server at `localhost:5000`. Opening `index.html` directly (a
> `file://` path) skips the server, so there's no Reddit fetch and you'll see
> placeholder cards instead.

No API key and no paid services are required.

## Tech stack

- **Backend:** Python + Flask
- **Data source:** Reddit public `hot.json` feeds
- **Frontend:** a single self-contained HTML file — vanilla JS, an inline SVG
  radar scope, no build step and no framework

## Design decisions

- **Server-side fetch.** The browser can *display* any image URL, but it can't
  reliably *fetch* Reddit's JSON cross-origin. Moving the fetch to the server
  is what makes real, current images possible.
- **Velocity over raw score.** Ranking by total upvotes just surfaces old
  popular posts. Dividing by age surfaces genuine momentum, which is the whole
  point of a "trend radar."
- **Graceful degradation.** A live demo that depends on an external feed will
  eventually hit a bad moment. The automatic fallback means a failed fetch
  never becomes a blank screen in front of an audience.

## Known tradeoffs

- Clustering is based on shared literal phrases, so it groups by wording rather
  than meaning — it catches phrase-driven trends well but won't recognize that
  two differently-worded posts are the same joke.
- Format names default to the recurring phrase, so alongside the punchy ones
  you'll occasionally get a plain label like *Cat* or *Monday*.
- Rising/cooling is a one-snapshot heuristic, not a true time series.

## Where it could go next

- **Semantic clustering** with an embedding or language model, to group posts
  by meaning instead of exact wording.
- **True velocity** by caching each scan and diffing heat between runs, turning
  the rising/cooling label into a real time series.
- **More sources** — TikTok, X, or Instagram feeds alongside Reddit.
- **Auto-refresh** so the radar updates itself on a timer.
