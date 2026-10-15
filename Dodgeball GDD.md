# Rebound Stars — Game Design Document

Status: final design v1.0. Every number below is a starting tuning target for playtests, not a law.

## 1. Pitch

Rebound Stars is a fast, readable, stylized 3D dodgeball game for the browser, built around rebounds. Players leap around a walled arena and off its walls, and wild curveballs and knuckleballs ricochet off every wall, floor and ceiling. Every throw, catch and jump feels punchy. Matches are short, the rules are simple, and the skill ceiling is extremely high, built on catching, baiting, feints and movement tech rather than button mashing.

## 2. Decisions

- **Name**: Rebound Stars.
- **Platform**: runs in the web browser, desktop first.
- **Dimension**: full 3D.
- **Stack**: three.js for rendering, Rapier for physics, custom ball bounce logic.
- **Core mechanic**: rebounds.
- **Cast**: 18 selectable Splatoon-inspired characters, each with traits and a special move.
- **World**: 8 colorful maps.
- **Launch mode**: 1v1 against AI.

## 3. Pillars

- **Rebound**: rebounds are the main fun of the game. Walls, floor and ceiling are your weapons, and you jump, wall-jump and fight in the air.
- **Deep**: easy to learn, extremely hard to master. The skill ceiling is a core goal, not a bonus.
- **Readable**: you always know where the ball is and who threw it.
- **Loud**: every throw, hit and catch has big, punchy sound and animation.
- **Distinct**: 18 stylized characters with their own traits, personalities and special moves.
- **Short**: a match takes 2 to 3 minutes, so "one more game" is easy.

## 4. Core loop

Grab a ball → aim → throw → opponent dodges, parries or catches → rebound hit or catch fills the special bar → score or get hit → repeat until the round ends.

Moment to moment: jump, wall-jump, pick up balls, throw, dodge, catch, use your special.

## 5. Rules

- **Format**: 1v1 with 3 lives at launch. 3v3 comes later, where a hit means you are out.
- **Arena**: a walled arena split in half by a center line. You stay on your half and can use its walls for jumping.
- **Hit**: being hit by a live ball costs a life.
- **Catch**: catching a live ball costs the thrower a life.
- **Live balls**: a ball stays live while it keeps rebounding off walls, floor or ceiling. It goes dead and can be picked up once it settles on the floor.
- **Win**: a round ends when one side has no lives left. First to 2 rounds wins.

## 6. Controls and camera

- **Camera**: a wide, dynamic view of the whole walled arena that tracks the ball and both players. Wall-jumping means the camera must always show the walls, so there is no fixed top-down view.
- **PC**: WASD move, mouse aim, left-click throw (hold to charge), Space jump (press again at a wall to wall-jump), Shift air-dash, right-click catch, E special.
- **Gamepad**: left stick move, right stick aim, RT throw, A jump (press again at a wall to wall-jump), B air-dash, LT catch, Y special.
- **Mobile**: out of scope.

## 7. Core mechanic: Rebounds

Rebounds are what make this game different. Every ball ricochets, and the best players think in angles.

- **Live balls**: walls, floor and ceiling all reflect the ball. It stays dangerous until it settles.
- **Rebound chain**: an on-screen counter tracks bounces. Each bounce adds speed and power, up to a cap.
- **Star Hit**: a hit after 3 or more rebounds. It gets the biggest impact animation and the biggest special bar boost.
- **Hard to catch**: balls with 3 or more rebounds cannot be caught normally. They must be dodged, parried or perfect-caught.
- **Aim preview**: while charging, a faint line shows only the first bounce. Everything after that is up to the player.
- **Wall-jumps feed rebounds**: use the walls to get into position and throw from angles, and use the ceiling for steep downward shots.
- **Feedback**: every bounce leaves an ink splat on the surface and plays a sound that rises in pitch along the chain.
- **Content tuned for rebounds**: map layouts and twists, and characters like Bouncer and Echo, are designed around bounces.

## 8. Mechanics

- **Throw**: hold to charge. A longer charge gives a faster ball but a slower throw, so it is easier to read.
- **Catch**: a window of about 0.25 seconds. A perfect catch is a tighter window inside it and returns the ball faster. A failed catch means you get hit.
- **Parry**: deflects a ball without catching it, so you do not own it. Pivot's parry lets you choose the direction.
- **Jump and wall-jump**: tap to jump, and press again at a wall to kick off it, up to 3 wall-jumps in a row. Wall-jumps keep your speed and can be aimed.
- **Air-dash**: a short dash with about a 2 second cooldown that changes direction mid-air. Being airborne is the main way to dodge.
- **Air play**: you can throw and catch in the air. Throws from above angle downward, and throws from a wall arrive from angles your opponent isn't facing.
- **Walls**: only the walls on your own half are usable, and you cannot cross the center line.
- **Landing**: a hard landing from a high fall has a short recovery, so careless jumping is risky.
- **Ball types** (after the base game works): Normal, Heavy (slow, can't be caught, knockback), Decoy. Curves and knuckleballs work on every throw, so they are not ball types.

### Curves and knuckleballs

- **Curve**: flick the aim stick at release to bend the ball, from a gentle arc to a huge loop around the opponent.
- **Knuckleball**: release at a precise point in the charge for a slow, wobbling ball that shifts speed and direction in a fixed pattern. The pattern depends on release timing, so it is learnable and readable, not random.
- **Combos**: a knuckleball thrown off a wall-jump, or a curve that bounces off a wall mid-flight.
- **Counterplay**: every curve and knuckleball shows a visible trail, so defenders can read it and time the catch.
- **3D readability**: depth is harder to judge in 3D, so every ball casts a ground shadow and shows a landing marker. Aiming locks on to your opponent, with a free-aim offset on top.

## 9. Skill ceiling

Depth comes from systems that interact with each other, not from adding buttons. Nothing is random, so every outcome can be read, baited or outplayed.

- **Rally speed-up**: every catch and return throw makes the ball faster, so rallies escalate until someone slips.
- **Catch tiers**: a normal catch, a perfect catch and a parry.
- **Charge and feint**: a throw can be canceled mid-charge to bait a dodge or catch, at the cost of a short recovery.
- **Curve and rebound control**: bend shots, mix in knuckleballs, or rebound them off walls to hit from angles.
- **Movement tech**: chained wall-jumps, air-dash cancels and aerial throws from any wall, so position in the air matters as much as aim.
- **Matchups**: the 18 characters counter each other, so character choice and counter-picks are part of the game.

## 10. Special moves

Every character has one unique special move.

- **Filling the bar**: it fills through ball contact. Star Hits give the most, then a catch, a normal hit and a parry. Being hit gives a small catch-up. These weights are tuning targets.
- **Ready state**: when the bar fills, there is a freeze-frame pulse, the character glows, a loud sting plays, and the bar flashes READY. The special stays ready until used.
- **Using it**: press the special button (E on PC, Y on gamepad). The bar resets to empty.
- **Presentation**: each special has its own animation and sound.

## 11. Characters (18)

Every character has one strength and one matching weakness. Balance by tuning tradeoffs, not by tiers. All 18 are drawn in a splat-inspired look with ink-like shapes and bold colors. Each has a distinct personality shown through idle animations, taunts, victory poses and voice lines. They share one skeleton and animation set to keep art cost down.

| # | Character | Personality | Strength | Weakness |
| --- | --- | --- | --- | --- |
| 1 | Rocket | Cocky show-off | Fastest throws | Slowest movement |
| 2 | Slick | Cool and laid-back | Fastest movement | Weakest throws |
| 3 | Wall | Calm and stoic | Widest catch window | Biggest hitbox |
| 4 | Ghost | Shy and mysterious | Longest air-dash distance | Longest air-dash cooldown |
| 5 | Bender | Theatrical artist | Strongest curve on throws | Slowest charge |
| 6 | Bouncer | Hyper, can't sit still | Throws gain speed off walls | Slow direct shots |
| 7 | Sniper | Focused and deadpan | Tightest aim at long range | Slow wind-up |
| 8 | Juggler | Cheerful clown | Carries two balls | Each throw is weaker |
| 9 | Tank | Gentle giant | Absorbs one extra hit per round | Slow and large |
| 10 | Trickster | Mischievous prankster | Feint with no recovery time | Lowest throw power |
| 11 | Magnet | Collector who hoards everything | Pulls nearby loose balls | Short catch window |
| 12 | Vault | Reckless daredevil | Highest jump | Exposed on landing |
| 13 | Blitz | Impatient speedster | Sprint burst | Long sprint cooldown |
| 14 | Counter | Smug and sarcastic | Perfect catch returns a double-speed ball | Normal catches are shorter |
| 15 | Echo | Dreamy, repeats himself | Throw splits into a delayed twin ball | Each ball is weak |
| 16 | Heavy | Grumpy bruiser | Uncatchable ball with knockback | Very slow to throw |
| 17 | Pivot | Sharp and calculating | Parry redirects a ball in any direction you choose | Cannot catch |
| 18 | Stinger | Feisty and small | Instant throw with no charge | Capped at low speed |

### Special moves

| # | Character | Special move |
| --- | --- | --- |
| 1 | Rocket | Sonic Shot: one ball at triple speed, only a perfect catch stops it |
| 2 | Slick | Slipstream: 4 seconds of double speed and free air-dashes |
| 3 | Wall | Barrier: a shield wall that blocks balls for 3 seconds |
| 4 | Ghost | Phase: 2 seconds of intangibility, balls pass through you |
| 5 | Bender | Spiral Throw: a ball that loops around the whole arena |
| 6 | Bouncer | Pinball: a ball that bounces off every wall 5 times, gaining speed |
| 7 | Sniper | Laser Shot: a freeze, then a perfectly straight instant shot |
| 8 | Juggler | Triple Toss: three balls thrown in a fan |
| 9 | Tank | Quake: a ground slam that shockwaves balls and opponents back |
| 10 | Trickster | Mirror Match: 3 fake clones, only one throws a real ball |
| 11 | Magnet | Gravity Pull: pulls all loose balls to you, then fires them |
| 12 | Vault | Dive Bomb: launch to the ceiling and slam a ball straight down |
| 13 | Blitz | Overdrive: 5 seconds of rapid-fire throws |
| 14 | Counter | Reflect Field: balls that touch you bounce back at double speed for 3 seconds |
| 15 | Echo | Chain Echo: a ball that splits into twins on every wall bounce |
| 16 | Heavy | Wrecking Ball: a huge uncatchable ball you must jump over |
| 17 | Pivot | Time Slip: slows a ball in flight for 2 seconds so you can steer it |
| 18 | Stinger | Barrage: 8 quick throws in 2 seconds |

## 12. Maps (8)

Every map has the same rules but its own look, wall layout and one mild twist. Keep twists small so balance holds.

| # | Map | Look | Twist |
| --- | --- | --- | --- |
| 1 | Ink Docks | Harbor with stacked shipping containers, teal and orange | Container walls at mixed heights |
| 2 | Candy Court | Dessert land, pink and mint | Sticky walls: wall-jumps hold longer |
| 3 | Neon Rooftop | City skyline at night, purple and cyan | Slanted side walls |
| 4 | Jungle Ruins | Overgrown temple, green and gold | Stone pillars in the middle |
| 5 | Space Station | Orbital arena, deep blue and lime | Low gravity, floaty jumps |
| 6 | Frozen Lake | Icy pond, pale blue and white | Slippery floor |
| 7 | Volcano Gym | Lava gym, red and orange | Vents that launch players upward |
| 8 | Cloud Carnival | Sky fairground, rainbow pastels | Trampoline pads on the walls |

## 13. Modes

- **Quick Match**: 1v1 against AI.
- **Team Match**: 3v3 against AI (later).
- **Survival**: waves of AI throwers (later).
- **AI opponents**: Easy, Medium and Hard, tuned mostly by reaction time and aim error.

## 14. Menus and music

- **Menu music**: bright, bouncy, melodic music in a Super Mario-style spirit. Each menu screen (title, character select, map select, settings, results) plays its own variation of the same theme, with a different tempo, instruments or key. Screens cross-fade into each other.
- **Map select**: browse the 8 maps. Hovering a map highlights it (glow, scale-up, ink-splat border), plays that map's own stylized theme, and shows a small looping preview video of the map. Moving to another map swaps the music and video.
- **Preview video**: a 5 to 8 second loop per map showing gameplay in that map's look. It is rendered live in-engine, which costs less than shipping 8 video files. Pre-recorded clips are the fallback.
- **Originality**: the music is a style target, not a copy. Write original melodies and do not reuse any Nintendo themes.

## 15. Progression

- No stat upgrades. It stays fair and simple.
- Unlock cosmetics only: alternate outfits, ball skins, throw trails and map themes. All 18 characters are playable from the start.
- Daily challenges and win streaks give reasons to return.

## 16. Art and audio style

- **Look**: Splatoon-inspired. Bold flat colors, ink-splat shapes and bursts on impacts, thick outlines and a strong palette. Inspired by, not copied from, Splatoon.
- **Team colors**: must be instantly distinguishable (for example orange vs cyan).
- **Animation**: exaggerated, with squash and stretch, speed lines on fast throws, freeze-frame hit-stop, screen shake, camera punch-in, and impact flash and particles on every throw, hit and catch.
- **Audio**: loud, bass-heavy impact sounds, a rising whoosh on charge, a distinct sound for perfect catches, crowd-style reactions and upbeat looping music.

## 17. Scope

**v1 (must ship):**

- One map and 4 starter characters (Rocket, Tank, Trickster, Counter), each with a special, in 1v1 against AI
- Rebound physics and chain counter
- Throw (with curve and knuckleball), catch, parry, jump and wall-jump, special bar, lives, and round and match logic
- Basic juice (screen shake, hit-stop, sound)
- Menu with music, restart and pause

**v2 (if v1 is fun):**

- The other 14 characters
- The other 7 maps and the map select screen with previews
- 3v3 teams, ball types, cosmetics and Survival mode

**Cut for now:**

- Online multiplayer, level editor, story mode, stats and skill trees, mobile

## 18. Tech

- **Platform**: web browser, desktop first. No install, easy to share.
- **Rendering**: three.js, full 3D.
- **Physics**: Rapier (WASM) for colliders, the kinematic character controller and continuous collision detection, so fast balls never tunnel through walls.
- **Ball logic**: custom. Set the ball's velocity on every bounce instead of relying on restitution, and handle speed gain per bounce, the bounce cap, curves and knuckleball patterns in code.
- **Audio**: Web Audio, with compressed files and map themes streamed on demand.
- **Performance target**: 60 FPS on a mid-range laptop, with a small initial download.

## 19. Build order

1. A bare box with a ball, Rapier and rebound tuning. Do not move on until bouncing the ball around is fun on its own.
2. Player movement, jump and wall-jump.
3. Throw, catch, parry, curve and knuckleball.
4. An AI opponent, then a playable 1v1 match.
5. Juice: sound, hit-stop, shake and ink splats.
6. Special bar and the 4 starter specials.
7. Menus and music.
8. v2 content.

## 20. Risks and tuning

- **Rebound tuning**: speed per bounce, max chain and the Star Hit threshold decide whether the game is fun or random. Tune this first.
- **3D readability**: curved and bouncing balls are hard to track in 3D. Ground shadows, landing markers and trails are required, not optional.
- **Balance**: 18 traits and specials need a test plan, such as AI-vs-AI matches, before v2.
- **Content workload**: 18 characters, 8 maps, 8 map themes and 5 menu variations is large. Shared skeletons and shipping in phases keep it manageable.
- **Multiplayer**: AI only at launch. Local 2-player is a stretch goal and online is cut.
- **Tone**: playful look and sound, competitive depth underneath.
