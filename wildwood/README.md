# Wildwood

A 3D exploring game. You walk through a forest that goes on forever: pines, birches, leafy trees, ferns, tall grass, flowers, mushrooms and rocks. Every few minutes of walking you reach a river or a lake, and you can wade in and swim. There are also muddy marshes, rocky caves, and very rarely, a dragon's lair.

**Play it:** https://npyati.github.io/kid-games/wildwood/

## Controls

- **Xbox controller:** left stick to walk, right stick to look, RT (or RB) to swing, A to jump, LT (or click the left stick) to run, Start to open the menu. Hold RT to keep swinging. In the menu, use the stick or d-pad and press A to choose, or B to go back.
- **Keyboard and mouse:** WASD to walk, mouse to look (click the game to grab the mouse), click or F to swing, Space to jump, Shift to run, Esc for the menu. Arrow keys work too.

## Animals and fighting

**Friendly animals:** foxes, deer (some with antlers) and rabbits. They run away if you get close, and your swings pass right through them.

| Enemy | Health | Bite | Where | Drops |
|---|---|---|---|---|
| Wolf | 50 | 9 | packs of 2 or 3, mostly in forests | 2 gems |
| Bear | 140 | 16 | lives by a cave and comes back 2 minutes after it's beaten | 5 gems, always the next weapon |
| Giant snake (boss) | 400 | 18 | marshes; it can swim | 15 gems, 2 apples |
| Dragon (boss) | 1000 | 25, plus fire | sleeps in a rare lair on a mountaintop; comes back 10 minutes after it's beaten | 40 gems, 3 apples, the Dragon sword |

- Enemies wander until they spot you (they see farther in front of them). Then a health bar pops up over their head, they chase you, and they bite when they're close. Bosses get a big health bar across the top of the screen instead.
- You run faster than all of them. Wolves and bears can't swim, so jumping in water is a good escape. Snakes can swim.
- The dragon wakes up when you come within about 40 m. It bites up close and breathes fire from farther away. Step sideways out of the flames.
- Beaten animals fall over, sink into the ground and drop gems. 35% of the time they also drop an apple (+30 health). Wolves (30%) sometimes drop the next weapon.
- **Weapons:** Fists (10 damage), Stick (16), Stone club (25), Crystal sword (38), Dragon sword (60, only from a dragon).
- Your health refills slowly when you haven't been hit for a few seconds. If it runs out you're knocked out for a few seconds, then wake up with full health. Nearby enemies leave, and if you were at a dragon's lair you wake up 100 m away from it. You keep your gems and weapon.
- **Enemies: off** in the menu leaves only the friendly animals, for calm exploring.

## How the world is made

- Everything is in `index.html`, drawn with plain WebGL 2 (no libraries).
- The world is built from a seed in 64 m squares ("chunks") as you walk, and dropped again once they're far behind. Grass, ferns and flowers are only built for the squares close to you.
- Rivers follow the zero lines of a slow, wiggly noise, and lakes are where a second noise is high. Marshes are where a third noise is high, but only on low ground (so they never leave cliffs next to hills). Caves (at most one per 384 m square) and dragon lairs (at most one per 1.5 km square, on the highest ground there) are placed from the seed too.
- The terrain code sits between `TERRAIN-BEGIN` and `TERRAIN-END` so a checker script can run it in Node. On four seeds: water about once per km (around 1 minute of walking), a marsh about every 1.4 km (around 5 minutes), a cave about every 550 m, and the nearest dragon lair is usually 1 to 1.3 km away.
- **New world** in the menu picks a new seed.

## Saved data

One `localStorage` key, `wildwood.v1`: music, sound, look direction and enemy settings, the world seed, where you were standing, your gem count and your best weapon.
