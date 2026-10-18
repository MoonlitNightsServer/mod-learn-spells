# mod-learn-spells (Aldrynth)

Fork of [azerothcore/mod-learn-spells](https://github.com/azerothcore/mod-learn-spells) for the Aldrynth realm.

## Behaviour (Moonlit Nights generation 2)

One rule for all ten classes: a character automatically learns every spell its class trainers sell, at the trainer's required level, once the
prerequisites are known (previous rank, required ability and skill; talent-chain ranks only when the talent's Rank 1 is spent in the active spec).
Death Knights follow the same rule, because their whole level curve lives in the Death Knight module's trainer table (trainer 130).

- Source: `trainer_spell` rows of the class trainers (type class, trainers with at least 50 spells), read at startup; the lowest required level wins.
- Cap: `LearnSpells.MaxLevel` = 60. A level change past the cap (a GM jump from 50 to 70) still teaches everything up to the cap.
- `LearnSpells.OnLogin` = 1 catches up characters that missed a level.
- Kept from upstream: the ignore list (quest mounts, rare books, Dalaran items) and the extra non-trainer spells by level (parry, dual wield, pet basics, armour proficiencies, capital portals).
- Added: druids learn Flight Form (33943) at level 60, the tier where everyone else gets flying mounts.

## Install

```bash
cd modules
git submodule add https://github.com/VenomekPL/mod-learn-spells.git mod-learn-spells
# reconfigure CMake, rebuild, copy conf.dist → conf, restart worldserver
```

Upstream credit: AzerothCore catalogue module authors.
