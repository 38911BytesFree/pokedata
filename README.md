# pokedata

Game data for the PokeMagic app. The app ships with a copy of this data and downloads newer versions from here, so balance changes don't need an app release.

These files are generated and signed by PokeMagic's data pipeline, so don't edit them by hand. An edited bundle fails its signature check, and the app ignores it.

## Layout

- `v2/manifest.json`: the current revision, with the bundle's size, SHA-256 hash and Ed25519 signature.
- `v2/game_data.json`: species, moves, CP multipliers, power-up costs, the type chart, the league rankings with the moves PvPoke's battles use for each Pokémon, and the cups: PvPoke's rankings where it has them, and each cup's rules (types, tags, bans, evolution stage, level cap) so the app can estimate the rest. Rankings are stored as compact rows that refer to species and moves by their place in those lists.
- `v1/`: the same data in schema 1 for apps built before schema 2 (up to TestFlight build 2); it isn't updated any more.

The folder number is the data schema version. An app reads only the schema it was built for, so a format change goes in a new folder and older apps keep working on the old one.

## Sources

- Most of the data comes from [PvPoke](https://github.com/pvpoke/pvpoke), used under the MIT License (see `third_party/pvpoke/LICENSE`). That includes species, moves, CP multipliers, the type chart, and the league and cup rankings, which come from PvPoke's battle simulations.
- Power-up costs are game mechanics compiled for PokeMagic and checked against in-game recordings.

PokeMagic is unofficial and not affiliated with Niantic, Nintendo, Creatures or Game Freak.
