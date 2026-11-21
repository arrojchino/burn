# Burn

Slow Burn: a patient session timer where the joint burns down with the clock.

Live: https://arrojchino.github.io/burn/
Source: https://github.com/arrojchino/burn

## What it does

- **The joint is the progress bar.** Light up and the paper burns from the tip toward the crutch in step with the timer. A grey ash cone grows past the ember and breaks off every 30 to 40 seconds.
- **Smoke from the ember.** A canvas particle plume rises from the ember's position on screen and drifts in a slow wind. It thickens on each exhale, thins to a thread while the joint rests, and takes on a little of the current vibe colour.
- **Breathing guide.** While it burns, the timer cycles 4 s inhale, 1.5 s hold and 5 s exhale. The ember brightens as you draw and fades as you breathe out.
- **Put it down and pick it back up.** Pausing leaves the joint smoldering, and the remaining time is kept. The countdown is based on the wall clock, so a background tab still finishes on time.
- **Session lengths:** 3:00, 4:20, 5:00, 7:00 and 10:00.
- **Four vibes:** Chill, Creative, Sleepy and Giggly. Each one recolours the page, the ring and the smoke.
- **Sound:** a lighter flick, a soft crackle while it burns and a chime at the end. Everything is synthesized with Web Audio; there are no audio files. Sound can be switched off.
- **Toke log and stats:** sessions, total minutes, a daily streak and a countdown to the next 4:20 on your local clock. The log lives in `localStorage`.
- **Copy for Discord:** copies the last session as a short text block.
- Keys: `Space` lights up or puts it down, `R` resets.

## Privacy and security

Everything is in a single HTML file with inline CSS and JS. The CSP is `default-src 'none'` with only inline scripts and styles and `data:` images, so the page cannot load anything or send anything. Fonts are system fonts. Session history never leaves the browser.

A personal timer for adults, where it is legal.

## Verification

Checked in Chromium at 1440 x 900 and 390 x 844 against a local server:

- A full session runs unlit, lit, paused, resumed and complete, with no page errors.
- At 55% the joint has burned from x 402 to x 247 in SVG units. At the end it stops at the crutch and the ember goes out.
- Ash grows and breaks, and its flecks stay inside the ash.
- Smoke particles are emitted from the ember.
- Completion logs the session: stats read 1 session and 5 minutes, and the log entry shows 05:00.
- Switching vibes recolours the page, the ring and the smoke.
- On mobile, the page has no horizontal overflow.
