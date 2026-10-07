# Changelog

## v2.0.0 (build 103)
Everything since build 63 (the last build released on Discord), including v1.0.0 (build 64).

### Settings: one file per group type
- The single `AdvancedFireflies.ini` is gone. Global settings are in `AdvancedFireflies - Base.ini`, and every group
  type is its own file in `GroupsSettings\` – the file name is the group's name, the section inside is `[Groups]`.
- Every file there with `Enabled = 1` is loaded automatically – up to **100** group types (was 4 + 10 custom).
  Shared group files never clash: just drop them into the folder.
- `FFLIES` also picks up new, changed and removed group files.
- All files are sorted into topic blocks (when, where, birth and despawn, flight, look, wings…), every block
  explained right above its keys.
- Old ini files and the old `Setting Presets` are not read any more – delete the old mod folder before updating.

### New: wings and bodies
- **3D wings** (`FairyWings = 2`): two real wings drawn by the plugin, beating faster and deeper with the flight
  speed, body pitch by speed, optionally turned towards the player.
- **11 wing patterns** (`WingPatterns`): classic fairy, water, wind, feathers with hearts, star, flame, dragonfly,
  beetle hind wing, and 4 butterflies (monarch, swallowtail, peacock, morpho). A list = a random one per firefly.
- **Glowing or solid wings** per group (`WingStyle`); `WingCover` makes glowing wings hide what is behind them.
- **3D bodies** (`WingBody`, `WingBodyStyle`): a slim insect body with antennae (butterflies) or a **firefly
  beetle** whose tail glows in the firefly's colour and flares with it (`WingBodyGlow`).
- **Flat wings** (`FairyWings = 1`): camera-facing sprites with a 4-frame wing beat (`advanced_fairywings.fxs`).
- Wings and bodies fade in and out smoothly, are reflected in water and are skipped when too small to see.

### New: look
- **Core discs** (`CoreDisc…`): solid coloured cores with colour rings, smooth or sharp, under or over the glow,
  with an extra soft glow around them.
- `Rotation` – tilt variants of the sprite; `InsectWings` – the texture's insect without its own small wings.
- `[TrailLook]` – the trail and death-burst particles have their own texture settings.
- Level of detail follows the camera, the sniper scope and the photo camera zoom included.
- **Fireflies redone:** a 3D firefly beetle with a glowing tail, 2.5× bigger (`advanced_firefly_big.fxs`), the
  soft "atmospheric" glow without core discs.

### New: groups and behaviour
- **AttachTo**: groups pinned to objects (model names or IDs – e.g. fire hydrants), to any ped, any vehicle or to the
  player. Offset, front angle, lag and snap distance; a ped or vehicle never hits its own fireflies; when it is
  gone, its group bursts. Cheat `FFNEAR` lists the models around you.
- **Interiors**: groups indoors too, or only indoors (`Interiors`, `InteriorSpawnRadius`).
- `HoverHeight` – how high stationary groups hover.
- `Lights = 0` – a group that never lights up its surroundings (e.g. butterflies by day).
- `WindDrift` – how much a group is blown by the weather wind (before, whole swarms were blown away in windy weather).
- `KillOnHit`, `KillByRotor`, `KillOnHitSpeed`, `HitsToKill` per group.
- New ready-made groups: butterflies by day (stationary and wandering), hydrant fairies, fairy companions that
  follow the player, and themed wings and colours for the existing fairies (fire, water, wind, Cupid, star,
  HELLO, the fairy army).

### Proper Shaders, reflections, performance
- Wings, bodies and discs are drawn after the water and the grass, also in interiors, and write depth, so Proper
  Shaders' water caustics no longer paint over them.
- Reflections hide reliably behind buildings (cached line-of-sight checks), also under heavy load.
- Much faster per-frame lookups – many groups and big swarms cost far less CPU; more FX systems (1024) and winged
  fireflies (4096) can be handled.
- Freeze watchdog: if the game ever freezes, `AdvancedFireflies_freeze.log` shows where (for bug reports).
- Several crash fixes.

### v1.0.0 (build 64)
- Own effect files with unique names: `advanced_firefly.fxs`, `advanced_fairytrail.fxs` (no clashes with other
  mods – delete the old `firefly.fxs` / `fairytrail.fxs`).
- Fairy trail colours no longer shift through other colours before fading.
- Presets updated to the new effect names.
