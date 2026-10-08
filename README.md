# AdvancedFireflies

ASI plugin for **GTA San Andreas (PC, 1.0 US)** – fireflies, fairies and butterflies as living groups and swarms:
they hover over meadows and water, wander across the sky, glow and flare up, light up their surroundings, beat
real 3D wings, leave glowing fairy trails, draw shapes in the sky, are reflected in water, bounce off vehicles and
people, get blown away by rotors – and can be killed. Every group type is one small `.ini` file you can share.

**Current version:** v2.0.0 (build 103) – see [Releases](https://github.com/Mickub2001/AdvancedFireflies/releases)
and the [changelog](CHANGELOG.md).

> Media for every feature will be added soon.

---

## Features

### Groups
- Every group type is **one `.ini` file** in `GroupsSettings\` – the file name is its name. Up to **100** group
  types at once; each type can have up to 64 groups in the world.
- Sharing is easy: drop someone's group file into `GroupsSettings\` – names never clash. `Enabled = 0` switches a
  file off without deleting it.
- **Stationary groups** hover where they were born (`HoverHeight` above the ground or water), **wandering swarms**
  fly across the map at configurable heights and speeds.
- Spawn areas: map levels (countryside, LS, SF, LV) and/or zones from `info.zon` –
  zone names: [GTA SA territories map](https://static.wikia.nocookie.net/gtawiki/images/4/40/TerritoriesNamesGTASA-map.png/revision/latest?cb=20160714130032)
- Hours and weathers per group (fireflies at night, butterflies by day…), over land and/or water, roads allowed or not
- **Interiors** – groups can appear indoors too, or only indoors
- **AttachTo** – groups pinned to objects (by model name or ID, e.g. fire hydrants), to any ped, any vehicle or to
  the player (fairy companions that follow you); offset, lag and the model's front are configurable
- `FixedMembers` – a group keeps exactly its members until it despawns
- Ready-made groups: fireflies (stationary and wandering), fairy groups, fire / water / wind / star / Cupid fairies,
  a fairy army, hydrant fairies, fairy companions, butterflies by day

### Look
- Auto-generated textures (no .txd needed) – glow, glow with a tiny insect, wings, bodies
- Size, colour, brightness, flare, rotation and other values – with variants per firefly or per group
- **3D wings** (`FairyWings = 2`) – two real wings beating with the flight speed, glowing or solid, with
  11 patterns: classic fairy, water, wind, feathers with hearts, star, flame, dragonfly, beetle, and
  4 butterflies (monarch, swallowtail, peacock, morpho)
- **3D bodies** – a slim insect body for butterflies, or a **firefly beetle whose tail glows** in the firefly's
  colour and flares with it
- **Core discs** – solid coloured cores with colour rings under or over the glow
- Flat wings (`FairyWings = 1`) – camera-facing FX sprites with a 4-frame wing beat
- Smooth fade in / out, detail follows the camera (sniper scope and photo camera zoom included)

### Light
- Glow and flaring of every firefly
- Atmospheric light (game point lights) from the nearest fireflies – a steady, dimmer light
  (`SteadyLights`, `IdleLight`) that brightens when they flare up; can be switched off per group (`Lights`)
- Optional coronas

### Behaviour
- Configurable motion inside a group (jitter, wandering, pull to the centre), wind drift per group
- Wandering swarms with meandering, climbing and descending to their preferred heights
- Flight patterns – swarms draw shapes with their fairy trails, from small LOGO-like programs in
  `patterns\*.txt` (heart, star, HELLO!, anime girl, chibi – or write your own)
  - several patterns in a row, plane (`Viewer` / `Flight` / `Ground`), speed, scale
  - `PatternContinuous` – the trail does not break between patterns

### Interaction
- Collisions with peds, the player and vehicles
- Death: a fast hit kills, so do several slower hits (`HitsToKill`) and spinning rotors – per group
- Death animation – the firefly bursts into fairy-trail particles of its own colour
- Vehicle wind – helicopters, the Hydra (VTOL) and the Vortex blow fireflies away; by default smoke too
  (tear gas, flares, exhaust…), the list of affected effects is configurable

### Fairy trails
- Glowing trails behind fireflies – rate, life, spread, drift, size, brightness per group
- Trails are scattered by passing aircraft (`TrailWake`)

### Water reflections
- Fireflies, their trails, wings, bodies and core discs are reflected in water
- Hidden correctly behind buildings, shores and boats
- Works with the original water and with Proper Shaders
- `REFLOG` cheat – diagnostic log for reflection problems

### Other
- `FFLIES` cheat – reload all settings and group files in game
- `FFNEAR` cheat – writes the models around the player to the log (names / IDs for `AttachTo`)
- Own effect files with unique names – no clashes with other mods' effects
- Freeze watchdog – if the game ever freezes, `AdvancedFireflies_freeze.log` shows where
- `FxResetFix.asi` – fixes an original game crash while loading a save (`gta_sa.exe+0xAA3A1`, `FxSystem_c::Stop`)

---

## Requirements
- GTA San Andreas **1.0 US** executable. Other versions (1.01, Steam, Definitive Edition) are not supported – like
  most ASI mods, the plugin calls game functions at fixed addresses of the 1.0 US executable.
- An ASI loader (Silent's ASI Loader) or Modloader.
- **FxsFuncs** (Junior_Djjr) with a raised `LimitAdjusterMult` – at least 8; 16–32 for the default set of groups
  with many long trails (otherwise trails are only partly generated). EffectsLoader works too.

## Installation
**With Modloader (recommended):** copy the `AdvancedFireflies` folder into `modloader\`.

**Without Modloader:** copy the contents of `AdvancedFireflies` next to `gta_sa.exe` (or into the `scripts` folder
of your ASI loader). Keep everything together – `AdvancedFireflies - Base.ini`, the `.fxs` files and the
`GroupsSettings` and `patterns` folders are looked for next to `AdvancedFireflies.asi`.

**FxResetFix.asi – optional, but strongly recommended:** copy it next to `gta_sa.exe`. The crash it fixes is a bug
of the original game, but this mod creates many effects, which makes that crash much more likely.

**Updating from v1.0 (build 64 or older):** delete the old `AdvancedFireflies` folder first. The single
`AdvancedFireflies.ini` and the `Setting Presets` are replaced by `AdvancedFireflies - Base.ini` and the group files
in `GroupsSettings\` – old ini files are not read any more.

### Files
| File | |
|---|---|
| `AdvancedFireflies.asi` | the plugin |
| `AdvancedFireflies - Base.ini` | global settings: effects, glow, textures, reflections, trail wake, death burst |
| `GroupsSettings\*.ini` | one file per group type – every key is described inside |
| `advanced_firefly.fxs` | the firefly / fairy effect |
| `advanced_firefly_big.fxs` | the same effect 2.5× bigger (the default fireflies) |
| `advanced_fairytrail.fxs` | the fairy trail / death burst effect |
| `advanced_fairywings.fxs` | the flat wings (`FairyWings = 1`) |
| `patterns\*.txt` | shapes the swarms can draw – small LOGO programs, you can write your own |
| `AdvancedFireflies.log` | written by the plugin – check it if something is off |
| `FxResetFix.asi` | separate fix, goes next to `gta_sa.exe` |

## Group files
- Every `.ini` in `GroupsSettings\` with a `[Groups]` section and `Enabled = 1` is loaded, in the order of the file
  names. `Enabled = 0` = skipped.
- **A new group** = a copy of any group file under a new name. Change `Wandering`, the places, hours, look…
- **Sharing:** send just your group file – the other player drops it into `GroupsSettings\`.
- `FFLIES` reads the folder again – new, changed and removed files take effect without restarting the game
  (a new effect in `[Effects]` `Load` still needs a restart).

## In game
| Cheat | Action |
|---|---|
| `FFLIES` | reload the Base file and all group files |
| `FFNEAR` | write the models around the player to the log (for `AttachTo`) |
| `REFLOG` | start / stop the reflection diagnostics (`AdvancedFireflies_reflections.log`) |

## Compatibility
- **FxsFuncs / NextGen Effects** – supported, recommended.
- **EffectsLoader** (tested with its Fix version) – supported: the effect files are loaded right before the game
  trims the FX memory pool, whichever loader runs.
- **"FXS FIX - CULLDIST - LOD - NAMES"** (.bat tool,
  [MixMods Discord](https://discord.com/channels/793480791509565440/1556818379086495794)) – fixes .fxs files whose
  internal names clash between mods. Not needed for this mod, but if `advanced_firefly` ever clashes with another
  mod, running it fixes the names.
- **Proper Shaders** – recommended: point lights show as highlights on car paint, bloom/HDR makes the glow much
  nicer. Wings, bodies and discs are drawn so that its screen effects (water caustics) do not paint over them.

## Notes
- The game has 32 point lights per frame for everything (headlights, fire…). `SteadyLights` uses some of them –
  lower it if other lights start to disappear.
- Trails, reflections, death bursts and flat wings use FX particles. If game effects start to disappear, lower
  `TrailMaxParticles` / `MaxReflections` or raise `TrailReserve`.
- 3D wings and bodies are drawn by the plugin and use no FX particles; the ones too small to see (far away) are
  skipped.
- More enabled group types and bigger groups cost performance – switch off what you do not need (`Enabled = 0`).

---

## Roadmap
- Collision detection against the ground and walls
- "Sticky" variants with stickiness configuration
- Sticking to the ground / walls / models with an adjustable position (for bigger models)
- Real reflections via Proper Shaders (possibly)
- Spawn improvements and a better wandering-group algorithm
- In-game debug mode – change the config of a selected group with a real-time preview
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
If you need access to the code for a good reason (a bigger project, compatibility work), get in touch.

## License
See [LICENSE](LICENSE) – **no re-uploads and no modpacks**, link to this page instead. **Your own group files,
patterns, screenshots and videos are welcome.** No decompiling or reusing the plugin.

## Credits
- Author: **Mickub**
- Inspired by the mod "Светлячки в ночное время суток" (Fireflies at night) by
  [akiri](https://libertycity.net/files/search/?author=1&replace=&search_text=akiri) – no files of that mod are used.
- FxsFuncs, Proper Shaders, NextGen Effects – Junior_Djjr and the MixMods community.
