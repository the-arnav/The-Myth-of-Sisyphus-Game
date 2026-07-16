# Myth of Sisyphus

> *A boulder. A slope. No summit worth keeping.*
> Tap fast and steady to climb — hesitate, and gravity takes it back.

A single-file, browser-based endless climber inspired by Camus's *The Myth of Sisyphus*. There is no finish line: every hill you crest simply rolls into the next one. The only real objective is distance — how far you can carry the boulder before your rhythm breaks and it slips away from you.

**[[▶ Play the game](https://thesisyphus.netlify.app/)](#)**

---

## The idea, in short

Sisyphus is condemned to push a boulder up a mountain forever. In the myth, the boulder always rolls back down the moment it nears the top. This game turns that into the actual mechanic:

- The terrain is an endless chain of hills of varying height and shape — no two climbs feel the same.
- Physics pulls the boulder back down every slope at all times (`BASE_G`); you only move it forward by tapping.
- There is no "you win." Cresting a hill just puts you at the top of the next one. The run only ends when the boulder outruns your rhythm and rolls back past the last ground you secured.
- Progress is measured in **distance climbed (meters)**, not levels or streaks — Camus's absurd repetition made literal.

## Features

- **Rhythm-based push, not a hold button** — each tap gives the boulder a velocity kick. Tap in quick succession and each kick lands before gravity erases the last one, so you climb; tap slowly and the gaps between kicks let gravity win, so you slide back. Holding the key down does nothing — key auto-repeat is deliberately ignored, so only real, distinct taps count. Consecutive taps under the reference interval even earn a small bonus kick.
- **Procedurally varied mountains** — every hill gets its own randomized height and one of several shapes (a classic symmetric rise, a steep-then-gentle skew, a plateau/breather near the crest, or a rough, bumpy climb), so the terrain never repeats the same rhythm twice.
- **Single-knob difficulty tuning** — one `DIFFICULTY` constant scales gravity strength, drag, fail tolerance, and tap timing windows together, so the whole game can be re-balanced from one line.
- **Escalating difficulty with distance** — gravity gradually strengthens the farther you get, so staying alive gets harder the longer a run lasts.
- **Hand-drawn pixel-art rendering** — the whole frame is drawn into a small low-resolution off-screen buffer and then blown back up with nearest-neighbor scaling, giving the game a consistent, chunky retro pixel look at any screen size.
- **A sculpted, lit Sisyphus sprite** — a custom silhouette (not a static image) with directional lighting, a walk/push animation cycle, and a smoothed lean into the slope so he reads as grounded rather than jittery on bumpy terrain.
- **A textured, cracked boulder** — layered gradients, noise-based rock grain, irregular crack fissures, pockmarks, and a contact shadow that grounds it on the slope, plus a rolling rotation tied to actual distance traveled.
- **Full day/night cycle** — sky, lighting, and exposure shift gradually as you travel, with stars and fireflies appearing at night.
- **In-world milestone banners** — an original, myth-flavored line appears roughly every 250 m of progress.
- **Expanded, Camus-inspired game-over quotes** — a rotating pool of lines themed around the absurd, persistence, and "one must imagine Sisyphus happy," shown when a run ends.
- **5-track background music with crossfade** — a looping playlist that fades smoothly from one track to the next, with mute and skip controls, handled carefully around browser autoplay restrictions.
- **Best-distance persistence** — your best run is saved locally (`localStorage`) so it survives reloads and future visits.
- **Pause menu** and a minimal always-visible HUD (current distance, best distance, title watermark).

## How to play

**The core rule is the same everywhere: tap rhythmically and quickly. Don't hold — tap.**

### On PC
- Tap the **Spacebar** repeatedly, at a fast, steady pace, to push the boulder up the slope.
- Holding Spacebar down does nothing — only distinct key presses register.
- Click anywhere to start, resume from pause, or start a new run after a game over.

### On mobile
- **Tap the screen** repeatedly, fast and steady, to push the boulder.
- Tapping and holding your finger down does nothing — lift and tap again each time.
- Use the pause button (top-left) to pause/resume, and the music icons to mute or skip tracks.

### The core logic
- Every tap = one forward kick of speed.
- Gravity is *always* pulling the boulder back down the current slope.
- Tap fast enough and your kicks outpace gravity → you climb and crest the hill.
- Tap too slowly and gravity wins the gap between taps → the boulder recedes.
- If it slides back past the last low point (valley) you secured, the run ends.
- Cresting a hill doesn't end anything — it just rolls you into the next climb. Keep going as far as you can.

## Setting up your own copy

This is a single self-contained HTML file (canvas + JavaScript, no build step, no external framework). To run it:

1. Download/clone the file and open it in any modern browser, or serve it from any static host (GitHub Pages, Netlify, Vercel, etc.).
2. **Add your own music (optional):** drop 5 audio files into an `audio/` folder in your repo, then edit the `MUSIC_TRACKS` array near the top of the `<script>` block with your file paths. Fewer or more than 5 tracks also works.
3. Push to your repo — if it's linked to a host like Netlify, it will redeploy automatically.

No dependencies, no package manager, no build tools required.

## Tech notes

- Pure HTML5 Canvas 2D — no external graphics or game engine.
- Everything (terrain, boulder, Sisyphus, lighting, particles) is drawn procedurally in JavaScript; nothing is a sprite sheet or imported image asset.
- Deterministic pseudo-random hashing seeds the hill heights/shapes and scenery placement, so the world is endless but reproducible from the same seed logic.
- Fonts: `Press Start 2P` (title/UI), `VT323` (HUD text), `Cormorant Garamond` (quote styling) via Google Fonts.

## Credits

- Concept & design: inspired by Albert Camus's *The Myth of Sisyphus*.
- Game-over quotes are original lines written in the spirit of the essay's themes (the absurd, revolt, and persistence), not direct quotations.
- Built as an experimental single-file browser game.

## Play it here

<!-- Add your deployed link below -->

🔗 **Live game:** [https://thesisyphus.netlify.app/]

