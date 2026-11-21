# Burn

Slow Burn: a dub session timer. A 3D joint burns down with the clock over a spinning record while a one drop riddim plays.

Live: https://arrojchino.github.io/burn/
Source: https://github.com/arrojchino/burn

## What it does

- **The joint is the timer.** Spark it and a flame catches the twist. The cherry then eats down the cone in step with the clock: char band, a broken glowing edge and grey ash that grows and drops off. When the session ends the joint is burned to the crutch and the ember dies out.
- **Real smoke.** Smoke rises from the cherry through a GPU stable-fluids solver (advection, vorticity confinement, pressure projection and buoyancy), so it curls and drifts instead of looping a sprite. It picks up the gold and green rim lights.
- **Take a hit.** Hold anywhere on the scene, or hold `H`, to draw on it: the cherry flares, sparks pop, and on release an exhale rolls across the record. Moving the pointer stirs the smoke. Tap the joint to flick the ash; the chunk falls, rides the spinning record and crumbles.
- **One drop riddim.** Synthesized live with Web Audio: kick and rimshot on beat 3, guitar skank on 2 and 4, organ bubble on the offbeats, a melodic bassline, dub delay and spring-style reverb. The breathing guide (inhale, hold, exhale) runs on the riddim's bars. Pass it and the band drops out into the echo; finishing a session fires a dub siren.
- **Strains** set the riddim and the light: Sativa is faster and brighter, Indica is slow, dark and heavy on the delay.
- **Papers:** unbleached hemp, white, rasta stripes and 24K gold foil, all generated in the browser: fibres, herb showing through, glue seam and crinkles.
- **Session lengths** of 3:00, 4:20, 7:10 and 10:00. A sticker tracks where it is 4:20 right now, or which city hits it next.
- **Toke log:** sessions, minutes, day streak and the next 4:20 on your clock, kept in `localStorage`. Copy the last session as text for Discord.
- Keys: `Space` spark or pass, `H` hold a hit, `F` flick the ash, `R` re-roll, `M` mute.

## Design references

- **Macro photos of lit joints** for the burning end: a jagged black char band with a red line along it, grey-white granular ash a little wider than the paper, and thin smoke that curls.
- **The Dub Soundsystem 1976 style** (Black Ark era; Curio style guide) for the layout:
  - a vinyl-black ground;
  - the Rastafari tricolour used like instruments in a mix, with green leading, gold as the body and red only as punctuation;
  - stamped labels, echo-offset type, groove arcs and grain.
- **Pavel Dobryakov's WebGL Fluid Simulation** (MIT) for the smoke solver structure.
- **One drop drum and skank patterns** for the riddim.

## Under the hood

- One HTML file. The only download is three.js r170, pinned on jsDelivr.
- The CSP allows scripts from jsDelivr and nothing else (`connect-src 'none'`).
- Two fonts are subset and embedded: Anton (OFL) and Permanent Marker (Apache 2.0).
- The joint is built in code:
  - The body is a lathe cone with hand-rolled lumps and a twisted tip.
  - The crutch has a spiral end face.
  - The ash is a mesh rebuilt as the burn front moves.
  - Burning is a shader on the paper. Fragments past an irregular, animated burn edge are discarded, and the edge is charred and lit.
- Behind the joint, the record has anisotropic groove highlights and its own label. Echo arcs on the floor pulse on every one drop kick.
- A sanitize pass clamps NaN and Inf before bloom. Resolution drops automatically if the frame rate falls.
- The countdown runs on the clock, so a background tab still finishes on time. A screen wake lock is held during a session where the browser supports it.

A personal timer for adults, where it is legal.

## Verification

Checked in Chromium at 1600 x 900 and 390 x 844 against a local server. No errors or warnings appeared in the browser console in either run.

**Rendering**
- The scene reports `ready` at 56 fps in the test browser, drawing about 114,000 to 119,000 triangles in 54 to 58 draw calls.
- All four papers and all three strains were captured and reviewed.

**Session flow**
- Tapping the unlit joint sparks it.
- Holding the pointer on the scene starts a hit (cherry glow 1.39), and releasing it exhales.
- Flicking dropped the ash from 0.40 to 0.02 units and released one falling chunk.
- A finished session shows IRIE and logs 04:20. The stats then read 1 session and 4 minutes.

**Audio**
- After a real click the Web Audio context is running.
- The riddim output measures RMS 0.09 to 0.27 with a peak of 0.45, so it does not clip.
- After a pass, the dub tail decays to RMS 0.002.

**Mobile**
- At 390 px the page has no horizontal overflow.
