# Trajectory — a group habit tracker that shows you your future self

**Hackathon project brief** · built entirely within the time limit · single self-contained HTML file, no accounts or setup

---

## The pitch

A habit tracker for a small group of friends who are leveling up together. Streaks and points, like you'd expect — but with two twists that reinforce each other:

1. **It's built for a squad.** You track alongside 3–4 collaborators, with a shared leaderboard and a *squad streak* that only survives if everyone shows up.
2. **It projects your future self.** Based on how you've actually been doing, it shows you who you're becoming — and forks that into two paths: *stay on it* vs *slip*.

The key idea that ties them together: **you can see your friends' future selves too.** A "Now / In 30 days" toggle on the leaderboard re-ranks everyone by their *trajectory*, not their current points. Watching a friend's projected self overtake yours because they didn't skip their runs is the whole hook.

---

## Core features

- **Habits with streaks and points** — the familiar loop, so it feels instantly usable.
- **Squad streak** — consecutive days where *every* member completes at least one habit. Collective stakes; one person flaking breaks it for everyone.
- **Future-self fork (the signature)** — your current trajectory splits into two futures:
  - projected attributes (e.g. Vitality, Wisdom, Calm, Energy) for each path
  - a diverging points chart showing the two futures pulling apart
  - a short *"letter from future you"* for each path — the emotional gut-punch
- **Time controls** — *Log today* banks your real choices; *Simulate a week* fast-forwards so the trajectory story is legible in a live demo with zero elapsed days.

---

## Scope (kept deliberately tight for the time limit)

**In:**
- 4 seeded members ("You" + 3 friends), each pre-loaded with ~2 weeks of history so the app looks alive from the first second
- Friends auto-simulate based on a consistency profile
- Everything self-contained — one HTML file, no backend, no auth, no API keys

**Cut on purpose (scope traps):**
- Real accounts, login, notifications, chat
- Real multiplayer infrastructure (the "group" is seeded and simulated)
- Anything that needs real days to pass — that's what the fast-forward button is for

---

## Demo flow (≈60 seconds on stage)

1. Open it — populated leaderboard, live streaks, a squad on a 9-day run.
2. Check off today's habits as "You"; points and streaks update.
3. Show the future-self fork: *stay on it* vs *slip*, side by side, with the two letters.
4. Hit **Simulate a week** — watch streaks climb, points diverge, and the leaderboard reshuffle.
5. Flip the leaderboard to **In 30 days** — reveal whose future self is winning.

---

## Why it works

- **Demo-friendly:** the stakes are visible on screen, and the fast-forward makes a time-based concept land in seconds.
- **On-theme:** the two twists aren't bolted on — the future-self projection is what makes the social layer competitive and the social layer is what makes the projection sting.
- **Achievable:** no infrastructure, no dependencies. It's one file you can open anywhere.

---

## Stretch ideas (only if there's time to spare)

- Nudge / cheer buttons between friends
- A "letter from future you" powered by an actual LLM call for freeform, personalized notes
- A shared group goal that unlocks something when the whole squad hits a threshold

---

*Working title: **Trajectory**. Tagline: "See who you're becoming — together."*
