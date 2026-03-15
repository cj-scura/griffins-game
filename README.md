# Griffin's Megalodon Chase — Game Spec

## The Pitch (by Griffin, age 5)
> A megalodon is on land. It's so fast that no one can get away from it. It puts you in jail. But Griffin is the fastest kid alive and HE can escape it.

---

## Game Overview

**Title:** Griffin's Megalodon Chase
**Genre:** Endless runner / chase game
**Platform:** Browser (React single-file artifact for claude.ai, or standalone HTML)
**Controls:** Arrow keys (← → ↑) + Spacebar. Must also work with on-screen touch buttons for tablet/mobile.
**Audience:** A 5-year-old who wants to feel like a superhero

---

## Core Loop

Griffin runs automatically from left to right across a scrolling landscape. The Megalodon (a massive shark stomping on land with tiny furious legs) chases from behind. The player's job:

1. **Jump** over obstacles (rocks, cars, buildings)
2. **Duck/slide** under low obstacles (tree branches, bridges)
3. **Collect speed boosts** (lightning bolts) to temporarily blast ahead of the Megalodon
4. **Free jailed friends** by running through jail cages scattered on the path

The Megalodon is ALWAYS gaining on you. The screen shakes subtly when it gets close. If it catches Griffin → he goes to jail. But jail has a mini-game to break out (mash spacebar / tap rapidly), because Griffin never stays caught.

---

## Characters

### Griffin (Player)
- A fast-running kid with a cape that flutters behind him
- Cape color: let the player pick at start (suggestion: blue, red, gold)
- Running animation should feel FAST — speed lines, blur effects
- When boosted: leaves a fire/lightning trail

### The Megalodon
- Comically enormous shark — but ON LAND
- Has tiny cartoon legs (stubby, fast-moving, funny)
- Mouth open, teeth visible, looks menacing but also silly
- Gets angrier (redder, faster) as the game goes on
- Takes up ~30% of the left side of screen when close

### Jailed Friends (NPCs)
- Other kids / characters trapped in cartoon jail cells along the path
- When Griffin runs through them, the cage breaks and they cheer
- Each freed friend adds +1 to a rescue counter
- Freeing friends gives a small speed boost

---

## Difficulty & "Impossible" Feel

This is supposed to feel IMPOSSIBLE — but Griffin can do it. Design levers:

- **Speed ramps up** over time (the world scrolls faster, obstacles come quicker)
- **Megalodon gets faster** every 30 seconds
- **Obstacle density increases** — early game has big gaps, late game is a gauntlet
- **Screen effects** intensify: more shake, redder edges, dramatic music swell
- **Other characters** appear running alongside Griffin early on but get caught one by one (dragged off screen by the Megalodon) — only Griffin survives
- **Near-miss feedback**: when Griffin barely clears an obstacle, show a "CLOSE!" or "TOO FAST!" popup with screen flash

### But keep it FUN, not frustrating:
- Griffin gets 3 lives (shown as little Griffin icons)
- Jail breakout mini-game means getting caught isn't game-over, it's a dramatic moment
- After breakout, Griffin gets a brief invincibility burst
- Speed boosts are generous early on
- First 15-20 seconds should feel achievable to build confidence

---

## Visual Style

- **Bright, bold, and cartoony** — think Saturday morning cartoon energy
- **Parallax scrolling** background: sky → mountains → city/landscape → ground
- Ground terrain shifts over time: grass → city streets → desert → beach (approaching water, Megalodon's home turf — final danger zone)
- **Screen shake** when Megalodon is close
- **Speed lines** when Griffin is boosted
- **Particle effects**: dust clouds from running, sparks from speed boosts
- Red vignette on screen edges when Megalodon is very close

---

## UI / HUD

- **Top-left**: Score (distance in meters)
- **Top-right**: Friends rescued counter (🗝️ x 3)
- **Top-center**: Lives remaining (Griffin face icons)
- **Bottom of screen** (mobile only): Touch control buttons — left/right arrows, jump, slide
- **No complex menus** — title screen has one big "RUN!" button

---

## Screens

### 1. Title Screen
- Big bold title: **GRIFFIN'S MEGALODON CHASE**
- The Megalodon lurks in the background, chomping
- Griffin stands in hero pose with cape blowing
- Cape color picker (3 color options)
- Giant "RUN!" button to start

### 2. Gameplay
- Side-scrolling runner as described above
- HUD overlay

### 3. Jail Breakout (mini-game overlay)
- When caught: screen goes dramatic, bars slam down
- Text: "MASH SPACEBAR TO BREAK FREE!" (or tap rapidly on mobile)
- Progress bar fills as player mashes — Griffin flexes and breaks the bars
- Dramatic burst animation on breakout

### 4. Game Over
- Only triggers when all 3 lives are spent
- Shows: distance ran, friends rescued, time survived
- Megalodon does a silly victory dance in background
- Big "TRY AGAIN" button
- Text: "The Megalodon wins this time... but Griffin NEVER gives up!"

---

## Sound Design (optional, nice-to-have)

- Upbeat fast-tempo background music
- Megalodon roar/growl when it gets close
- "Whoosh" on speed boosts
- Crowd cheer when freeing a friend
- Dramatic jail-break sound effect
- Comedic "chomp" if caught

---

## Technical Notes

- Build as a **single-file React component** (JSX) that runs in claude.ai's artifact renderer
- Use **requestAnimationFrame** for the game loop
- All art should be **SVG or CSS-drawn** (no external image assets)
- Game state managed with **useRef** for performance (not useState for frame-by-frame updates)
- Collision detection: simple **bounding box** (AABB) is fine for a 5-year-old's game
- Touch controls: absolute-positioned div buttons at screen bottom
- Target **60fps** — keep draw calls efficient
- The game should be fully playable and fun within a single React artifact

---

## Success Criteria (from Griffin's perspective)

- [ ] "The Megalodon is SO BIG and SO FAST"
- [ ] "I'm the fastest! No one else can do it!"
- [ ] "I saved my friends from jail!"
- [ ] "That was SO HARD but I did it!"
- [ ] "Can I play again??"

---

*Designed by Griffin (creative director) and Mom (executive producer).*
