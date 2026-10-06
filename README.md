# AdvancedFireflies

ASI plugin for **GTA San Andreas (PC, 1.0 US)** – fireflies as living groups and fairy swarms:
they hover over meadows and water, wander across the sky, glow and flare up, light up their
surroundings, leave glowing fairy trails, draw shapes in the sky, are reflected in water,
bounce off vehicles and people, get blown away by rotors – and can be killed.
Everything is configured in `AdvancedFireflies.ini`.

**Current version:** v1.0.0 (build 64) – see [Releases](https://github.com/Mickub2001/AdvancedFireflies/releases)

> Media for every feature will be added soon.

---

## Features

### Spawning
- Configurable spawn areas: map levels (countryside, LS, SF, LV) and/or zones from `info.zon` –
  zone names: [GTA SA territories map](https://static.wikia.nocookie.net/gtawiki/images/4/40/TerritoriesNamesGTASA-map.png/revision/latest?cb=20160714130032)
- Spawn radius, number of groups, group size and other spawn rules per group type
- Night hours and weathers without fireflies, per group
- Over land and/or water
- `FixedMembers` – a group keeps exactly its members until it despawns

### Look
- Auto-generated texture (no .txd needed) – glow, or glow with a tiny insect
- Size, colour, halo size, blink rate, brightness and other base values – with variants per group
- Up to 10 custom groups next to the 4 built-in group types

### Light
- Glow and flaring of every firefly
- Atmospheric light (game point lights) from the nearest fireflies – a steady, dimmer light
  (`SteadyLights`, `IdleLight`) that brightens when they flare up
- Optional coronas

### Behaviour
- Configurable firefly motion inside a group
- Wandering swarms – groups that fly across the map at configurable heights and speeds
- Flight patterns – swarms draw shapes with their fairy trails, from small LOGO-like programs
  in `patterns\*.txt` (heart, star, HELLO!, anime girl, chibi – or write your own)
  - several patterns in a row, plane (`Viewer` / `Flight` / `Ground`), speed, scale
  - `PatternContinuous` – the trail does not break between patterns

### Interaction
- Collisions with peds, the player and vehicles
- Death: a fast hit kills, so do several slower hits (`HitsToKill`) and spinning rotors
- Configurable death animation – the firefly bursts into fairy-trail particles of its own colour
- Vehicle wind reaction – helicopters, the Hydra (VTOL) and the Vortex blow fireflies away;
  by default smoke too (tear gas, flares, exhaust…), the list of affected effects is configurable

### Fairy trails
- Glowing trails behind fireflies (on for wandering swarms by default – gives them motion)
- Rate, life, spread, drift, size, brightness – configurable per group
- Trails are scattered by passing aircraft and react to speed (`TrailWake`)

### Water reflections
- Fireflies and their trails are reflected in water, with ripple, distance and strength settings
- Works with the original water and with Proper Shaders
- `REFLOG` cheat – diagnostic log for reflection problems

### Other
- `FFLIES` cheat – reload the .ini in game
- Own effect files with unique names (`advanced_firefly`, `advanced_fairytrail`) – no clashes with
  other mods' effects
- `FxResetFix.asi` – fixes an original game crash while loading a save
  (`gta_sa.exe+0xAA3A1`, `FxSystem_c::Stop`)
- A few ready-made presets in `Setting Presets`

---

## Requirements
- GTA San Andreas **1.0 US** executable. Other versions (1.01, Steam, Definitive Edition) are not
  supported – like most ASI mods, the plugin calls game functions at fixed addresses of the
  1.0 US executable.
- An ASI loader (Silent's ASI Loader) or Modloader.
- **FxsFuncs** (Junior_Djjr) with a raised `LimitAdjusterMult` – at least 8, more for configs with
  many long trails (otherwise trails are only partly generated).

## Installation
**With Modloader (recommended):** copy the `AdvancedFireflies` folder into `modloader\`.

**Without Modloader:** copy the contents of `AdvancedFireflies` next to `gta_sa.exe` (or into the
`scripts` folder of your ASI loader). Keep all files together – the .ini, the .fxs files and the
`patterns` folder are looked for next to `AdvancedFireflies.asi`.

**FxResetFix.asi – optional, but strongly recommended:** copy it next to `gta_sa.exe`. The crash it
fixes is a bug of the original game, but this mod creates many effects, which makes that crash
much more likely.

**Presets:** copy an `AdvancedFireflies.ini` from `Setting Presets\<preset>\` over the main one.

### Files
| File | |
|---|---|
| `AdvancedFireflies.asi` | the plugin |
| `AdvancedFireflies.ini` | all settings (descriptions inside) |
| `advanced_firefly.fxs` | the firefly effect |
| `advanced_fairytrail.fxs` | the fairy trail / death burst effect |
| `patterns\*.txt` | shapes the swarms can draw – small LOGO programs, you can write your own |
| `Setting Presets\` | ready-made configurations |
| `AdvancedFireflies.log` | written by the plugin – check it if something is off |
| `FxResetFix.asi` | separate fix, goes next to `gta_sa.exe` |

Updating from a version with `firefly.fxs` / `fairytrail.fxs`: delete those two files – the effects
are now called `advanced_firefly` and `advanced_fairytrail`.

## In game
| Cheat | Action |
|---|---|
| `FFLIES` | reload `AdvancedFireflies.ini` (changing `Load` in `[Effects]` still needs a restart) |
| `REFLOG` | start / stop the reflection diagnostics (`AdvancedFireflies_reflections.log`) |

## Compatibility
- **FxsFuncs / NextGen Effects** – supported, recommended.
- **EffectsLoader** (tested with its Fix version) – supported: the effect files are loaded right
  before the game trims the FX memory pool, whichever loader runs.
- **"FXS FIX - CULLDIST - LOD - NAMES"** (.bat tool,
  [MixMods Discord](https://discord.com/channels/793480791509565440/1556818379086495794)) –
  fixes .fxs files whose internal names clash between mods. Not needed for this mod, but if
  `advanced_firefly` ever clashes with another mod, running it fixes the names.
- **Proper Shaders** – recommended: point lights show as highlights on car paint, and bloom/HDR
  makes the glow much nicer.

## Notes
- The game has 32 point lights per frame for everything (headlights, fire…). `SteadyLights` uses
  some of them – lower it if other lights start to disappear.
- Trails, reflections and death bursts use FX particles. If game effects start to disappear,
  lower `TrailMaxParticles` / `MaxReflections` or raise `TrailReserve`.

---

## Roadmap
- 3D model with variants, low-poly at a distance from the camera – configurable
- Collision detection against the ground and walls
- "Sticky" variants with stickiness configuration
- Sticking to the ground / walls / models with an adjustable position (for bigger models)
- Real reflections via Proper Shaders (possibly)
- Spawn improvements and a better wandering-group algorithm
- In-game debug mode – change the config of a selected group with a real-time preview
- Configurable object / ped / vehicle hooks – groups tied directly to an object
- Configurable "soul fireflies" above dead people, and "soul collection"
- Configurable panic and curiosity values
- Reaction to gunshots and explosions
- Changeable position of stationary groups – fireflies moved by wind, curiosity or panic stay there
- Configurable sound effects per group ("normal" and "fairy" sounds)

## Releases
Released on the public **MixMods** community Discord server, and here in
[Releases](https://github.com/Mickub2001/AdvancedFireflies/releases).

## Source code
The source code of AdvancedFireflies is **not public**. This repository holds the documentation and the mod's
configuration files (`mod/`); the plugin itself is in [Releases](https://github.com/Mickub2001/AdvancedFireflies/releases).

## License
See [LICENSE](LICENSE) – **no re-uploads and no modpacks**; link to this page instead.
Presets, patterns and your own screenshots / videos are welcome. No decompiling or reusing the plugin.

## Credits
- Author: **Mickub**
- Inspired by the mod "Светлячки в ночное время суток" (Fireflies at night) by
  [akiri](https://libertycity.net/files/search/?author=1&replace=&search_text=akiri) –
  no files of that mod are used.
- FxsFuncs, Proper Shaders, NextGen Effects – Junior_Djjr and the MixMods community.
