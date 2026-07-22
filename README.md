# mod-learn-spells (Aldrynth)

Fork of [azerothcore/mod-learn-spells](https://github.com/azerothcore/mod-learn-spells) for the Aldrynth realm.

## Behaviour

- Auto-learns normal **trainer** class spells on level-up through **`LearnSpells.MaxLevel` (55)**.
- Levels **56–80**: train from class trainers as usual (talent resets unchanged).
- **Quest mounts** and **rare trainer-book ranks** are **not** auto-taught — complete quests / farm books as blizzlike.

## Conf defaults

| Key | Value |
|-----|-------|
| `LearnSpells.Enable` | `1` |
| `LearnSpells.Announce` | `0` |
| `LearnSpells.OnFirstLogin` | `0` |
| `LearnSpells.MaxLevel` | `55` |

## Scrub list (Aldrynth)

Removed from `m_additionalSpells` (and added to `m_ignoreSpells` where relevant):

| Spell IDs | Reason |
|-----------|--------|
| 5784 Felsteed, 23161 Dreadsteed | Warlock mount quests |
| 13819 / 34769 Warhorse, 23214 / 34767 Charger | Paladin mount quests |
| 25306 Fireball R12 | Rare trainer book |
| 40120 Swift Flight Form | Druid quest (also level > 55) |
| All `m_additionalSpells` buckets level **> 55** | Defense in depth with MaxLevel |

Kept trainer-style extras ≤55 (parry, dual wield, pet basics, mail/plate, capital teleports/portals, Redemption / Life Tap trainer ranks, etc.).

## Install

```bash
cd modules
git submodule add https://github.com/VenomekPL/mod-learn-spells.git mod-learn-spells
# reconfigure CMake, rebuild, copy conf.dist → conf, restart worldserver
```

Upstream credit: AzerothCore catalogue module authors.
