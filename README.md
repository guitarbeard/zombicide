# Zombicide Weapon Odds

A one-page calculator that compares two Zombicide 2nd edition weapons, or custom dice pools, and shows the chance of scoring at least N hits in a single attack.

Live at https://alxdna.dev/zombicide/

## How the odds work

The math follows depesz's [The hard math of killing zombies in Zombicide](https://www.depesz.com/2016/05/17/the-hard-math-of-killing-zombies-in-zombicide/). Each die hits on a roll of the weapon's accuracy or higher, so the per-die hit chance is `p = (7 - accuracy) / 6`. With `n` dice, the chance of at least `k` hits is the binomial tail:

    P(≥k) = Σ C(n,i) · p^i · (1-p)^(n-i),  for i = k..n

## Presets

The weapon list is the 2nd edition core box: starting gear, the equipment deck and the Epic weapons. Each preset records dice, accuracy, damage, range, melee or ranged, noise, and traits such as Dual, Sniper and Reload. Ma's Shotgun and Gunblade carry both a melee and a ranged profile. Edit the `PRESETS` array in `index.html` to add weapons.

Plenty of Bullets and Plenty of Shells each re-roll the whole attack once. The odds assume you re-roll only when short of the hits you need, so the chance becomes `1 - (1 - P)^(cards + 1)`.

## Development

There is no build step. Open `index.html` in a browser.
