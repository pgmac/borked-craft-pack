# borked-craft-pack

[packwiz](https://packwiz.infra.link/) modpack for the BorkedCraft Minecraft server.

It is a port of henkelmax's [Hermitcraft Server Pack](https://modrinth.com/modpack/hermitcraft) 2.3.0 (Minecraft 26.2) to **Minecraft 26.3**, plus [Voxy Server Side](https://modrinth.com/mod/voxy-server-side). Not affiliated with Hermitcraft or henkelmax. Switch back to the upstream pack once it ships a 26.3 release.

## Using it

The server runs [itzg/minecraft-server](https://docker-minecraft-server.readthedocs.io/en/latest/mods-and-plugins/packwiz/), which installs the pack at startup:

```yaml
TYPE: FABRIC
VERSION: "26.3"
PACKWIZ_URL: https://raw.githubusercontent.com/pgmac/borked-craft-pack/main/pack.toml
```

Datapacks install to `/data/datapacks/`, where the Datapack Injector mod loads them into every world.

## Differences from upstream 2.3.0

| Change | Reason |
| --- | --- |
| All mods bumped to their 26.3 builds | Target version |
| Fabric loader 0.19.3 → 0.20.0 | Latest for 26.3 |
| Added Eunomia | New required dependency of Armor Hider 0.14 |
| Added Voxy Server Side | Streams Voxy LODs to clients (clients need Voxy + the Voxy Server Side jar) |
| Removed fabricexporter | No 26.3 build |
| Vanilla Tweaks datapacks replaced with their 26.3 builds | 26.2 builds fail to load on 26.3 |
| Removed Armor Statues, Name Formatting Station, Translatable, Cave Cleaner, Toggle Weather datapacks | Fail to load on 26.3 (predicate/item-modifier format change); no 26.3 release yet. See issue #2 |

## Updating

```bash
packwiz update --all     # bump Modrinth-hosted mods
packwiz refresh          # after adding or removing files in datapacks/
```

Vanilla Tweaks datapacks are not on Modrinth. Fetch new builds from [vanillatweaks.net](https://vanillatweaks.net/picker/datapacks/) and replace the zips in `datapacks/`.

CI fails if `index.toml` is out of date. Run `packwiz refresh` and commit it.
