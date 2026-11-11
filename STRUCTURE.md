# CS Shooter 3D — Structure Map

Single-page 3D first-person shooter (Three.js). Two modes: vs Bots and
Online 1v1 over PeerJS (WebRTC, no own server). Hosted on GitHub Pages at
`bomiro.github.io/cs-shooter/`.

The game is built as one page (`cs-shooter/index.html`). Its code is
organized into 9 numbered modules, in this order, with a structure-map
comment at the top of the script. Any change belongs in exactly one module.

## Modules

1. **Config** — constants: health, ammo, reload time, win score (10 kills),
   respawn delay, bot count and difficulty.
2. **Audio** — shot, hit, reload and UI sounds (Web Audio, no audio files).
3. **Input** — keyboard + mouse with pointer lock on PC; joystick, drag-to-look,
   fire and reload buttons on touch.
4. **World** — map, textures (sand, wood, rusted metal), lighting, shadows,
   fog, sky with sun and clouds, crates, barrels, floating dust.
5. **Weapons** — rifle viewmodel, recoil, muzzle flash, tracers, shooting,
   manual reload (R) and auto-reload when the magazine empties.
6. **Bots AI** — 4 bots with different personalities (fast, sniper, heavy,
   balanced); movement, cover, aiming, shooting at the player and each other.
7. **Online / PeerJS** — room code (5 characters), host/guest join, WebRTC
   data channel, real-time sync of position, look direction, shots, hits,
   health and kills; disconnect handling and rematch.
8. **UI / Screens** — mode select, lobby, HUD (health, ammo, score, kill feed),
   reload indicator, end screens.
9. **Main loop** — frame loop, state sync tick (~20 Hz online), win check.

## Game rules

- Health 100, respawn 3 seconds after death.
- Rifle: 30 bullets, reload 1.4 seconds, auto-reload at 0 bullets.
- First to 10 kills wins. Headshot gives bonus points.
- Bots mode: player vs 4 bots. Online mode: 1v1, first to 10 kills.

## How updates work

The page is built with the Muse artifact `tswyb-hdf-3d`, exported as a
single self-contained HTML file and uploaded here as `cs-shooter/index.html`.
The site root `index.html` is the separate personal homepage and is not
part of the game. To update the game: edit the artifact, export it, and
replace `cs-shooter/index.html` (the file update needs its current SHA).
