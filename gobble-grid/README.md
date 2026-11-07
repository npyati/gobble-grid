# Gobble Grid

A math and word game for kids that runs in the browser. Steer your Gobbler around a grid and gobble every square that fits the rule ("Multiples of 7", "Starts with a blend", "x = 4") while dodging monsters. Every 3 levels, a Cyclops boss shows up. At 10 health it gets angry and smashes a row and a column every 5 seconds.

New players can start with **How to play**, a 6-step tutorial level where mistakes don't cost a life.

**Play it:** https://npyati.github.io/kid-games/gobble-grid/

## What's in it

- **Modules:** 2nd, 5th, 6th and 7th grade math, a 9th grade boss battle (Algebra 1), and Word sort (nouns, verbs, rhymes, long a, and blends).
- **Make your own:** in the menu, type a rule plus words that fit and words that don't. Topics are saved in your browser, and the menu can give you a code to copy them to another device.
- **It teaches as you play:** a wrong answer costs a life and shows why it's wrong, for example "8² means 8 × 8 = 64, not 8 × 2."
- **Monsters:** Grumble (walks straight, may turn), Wobbler (wanders), Scrambler (puts new numbers on squares), Sneaker (follows you). You can set monsters to None, Slow or Normal.
- **Extras:** a hint block that flashes every right answer for a split second, and original music: four level songs picked at random, separate boss music, and music that gets scarier when a monster is near.

## Controls

- **Keyboard:** arrow keys to move, Space to gobble, P to pause.
- **Tablet:** tap a square to walk toward it, and tap your Gobbler to gobble.

## Adding a topic in code

Everything is in `index.html` in this folder, with no build step. Topics live in the `MODULES` list. A word topic is a rule plus two lists:

```js
listTopic({ key: 'ocean', text: 'Lives in the ocean',
  yes: ['whale', 'crab', 'shark', 'squid'],
  no:  ['cow', 'eagle', 'lion', 'horse'] })
```

Math topics are small generators that return a right answer (`good()`) or a wrong one with an explanation (`bad()`), so every level is different.

## Testing shortcuts

- `gobble-grid/?level=4` starts at level 4.
- `gobble-grid/?boss` goes straight to the Cyclops.
- `gobble-grid/?boss&bosshp=3` gives the Cyclops only 3 health.
