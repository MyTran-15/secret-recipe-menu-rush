# PLAN.md: <team name>

## Pitch (one sentence)
You are the late-shift drive-thru crew, trying to decode customers' vague secret-menu orders, before the 60-second rush ends.

## Theme and limitation
The secret recipe: off-menu Taco Bell–style items that customers never name. They only describe them ("crunchy, but folded, with something green"), and the player works out the hidden recipe and builds it from 8 ingredients.
Limitation: **60-Second Run** (a full run lasts 60 seconds or less). How it shapes the core mechanic: one global 60s clock drives everything; every order is a race against it, the last 10 seconds tick out loud, and 3 drive-offs end the run early, so a run can never pass 60 seconds.

## Core loop
What the player does every 5 seconds: read the customer's hint → tap 3–4 ingredients → hit Serve. Right: points and the next car. Wrong: the recipe is revealed, patience drops, try again.

## Controls
- Tap/click ingredients to add or remove them (max 4), then **Serve**; **Trash** clears the order.
- Keyboard: `1`–`8` toggle ingredients, `Enter`/`Space` serve, `Backspace` trash.
- Type your name on the title screen before starting.

## Win, lose and score
- +100 per correct order, plus up to +100 speed bonus from the customer's remaining patience.
- 3+ correct orders in a row = double points.
- A customer whose patience runs out drives off; 3 drive-offs end the run early.
- Run ends at 0:00. Goal: top the Top 5 board (name + score, saved on the device).

## MVP: must ship (5 items max, in build order; playable after item 3)
| # | Item | Owner | Minutes | Done when |
|---|------|-------|---------|-----------|
| 1 | Shell: title screen with disclaimer + "Click to start", 60s clock, end screen with score + Play again | | 8 | Start runs a 60s clock that ends on the score screen |
| 2 | Order loop: car + hint bubble, 8-ingredient tray, Serve/Trash, recipe check, scoring, next customer | | 12 | A correct serve scores and brings the next car; a wrong serve reveals the recipe |
| 3 | Patience bar, drive-offs, 3-strike early end, difficulty ramp | | 6 | A car leaves when its bar empties; 3 leaves end the run |
| 4 | Feel: Web Audio sounds (select, serve, wrong, drive-off, final-10s tick), correct/wrong flashes | | 7 | Every action has a sound + a visual response |
| 5 | Phone + polish: one-column layout, big tap targets, keyboard shortcuts | | 5 | Plays well at 375px wide and on desktop with keys |

## Stretch: only after MVP (cut from the bottom)
1. Player name + Top 5 scores board on the end screen (who got which score)
2. Streak multiplier + combo text
3. Varied car colours

## Risks and fallbacks (top 2)
- Risk: hints too vague to decode in time / Fallback: after 5s the bubble shows one ingredient as a clue.
- Risk: phone layout too cramped / Fallback: fixed single column, tray as a 4×2 grid.
- Risk: 3D (Three.js from CDN / WebGL) fails or is slow on a phone / Fallback: game detects it and uses the 2D emoji scene.

## Milestones
- 0:55 First playable: MVP items 1 to 3
- Final: all MVP items

## Change log (fill in while you build)
| Time | Change | Why |
|------|--------|-----|
| | Built MVP 1–5 plus stretch 2–3 in one pass | Small single-file game; everything fit the time box |
| | Clock label shows "1:00" instead of "0:60"; start/end screens scroll on short windows | Found in playtest |
| | Added stretch 1: name input + Top 5 board (local to the device) | So we know who got each score |
| | Scene rebuilt in 3D with Three.js 0.149.0 (pinned CDN): kitchen-window view, 3D cars drive up, the order stacks on a tray and flies to the car; falls back to the 2D scene if Three.js/WebGL can't load | Asked for a 3D look; fallback keeps it playable offline |
