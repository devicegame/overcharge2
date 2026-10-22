# OVERCHARGE

A single-file 3D third-person action-RPG for the browser, built with Three.js. You play **Alex**, a
Westbrook High student who gains bio-electrical powers in a physics-lab accident and uses them to take
back the school from the gangs — ending with a boss fight against **Rex** in the gymnasium.

**Play:** open `index.html` (or serve the folder and open it) and click **ENTER CAMPUS**.
Everything — engine glue, level geometry, shaders, post-processing, audio — lives in that one file.
Three.js r160 and GSAP are pulled from CDNs; no other assets are needed.

## Controls

| Input | Action |
| --- | --- |
| `W A S D` | Move |
| Mouse | Free-look third-person camera (pointer lock; automatic fallback if the browser blocks it) |
| `Shift` | Hold to sprint, tap to **electric dash** |
| `Space` | Jump — hold in the air to **high-voltage glide** |
| Left click | **Arc bolt** (chains to 5 targets while overcharged) |
| Right click (hold) | Aim-zoom + **drain ray** |
| `E` (hold) | **Siphon** a nearby vending machine / lamp / fuse box / breaker |
| `Q` or `F` | **OVERCHARGE** (requires 100% charge, 15 s of unlimited power) |
| `Esc` | Pause · `M` mute · `H` toggle control hints |

## Systems

* **Energy loop** — abilities drain the battery; siphoning environment power refills HP + energy,
  makes the fixture flicker and die, and the fixture slowly comes back online.
* **Overcharge** — 2× speed, unlimited energy, chaining bolts, 2.4× damage, shockwave on landing.
* **Enemies with FSMs** (idle / patrol / chase / windup / attack / stun / flee):
  bully grunts (melee), jock brutes (heavy tackles and slams), ranged bullies (thrown balls).
* **Boss "Rex"** — phase 1 melee/shockwave brawling; phase 2 at 50% HP raises a battery shield,
  fires charged lasers and only becomes vulnerable after you drain the gym's three power nodes.
* **Four-quest campaign** — the awakening → hallway cleanup → breaker overload → confrontation,
  with tracked objectives, a minimap, waypoint beacons, dialog scenes and a stats-driven ending.
* **Procedural everything** — textures are painted to canvases at runtime, all sound is synthesized
  with the Web Audio API (zaps, siphon pitch-shift, thunder, impacts, UI blips, ambient hum).

## Performance notes

Instanced meshes for repeated props, pooled particles/bolts/shockwaves/projectiles, distance-culled
point lights, a player-following shadow frustum, adaptive pixel ratio, and `?quality=low` for weak GPUs.
`?nolock` forces the mouse-look fallback (useful when embedding the game in a restricted iframe).
