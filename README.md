# PocketMine-MP — Protocol 1001 (Minecraft v26.30)

Fork of [PocketMine-MP](https://github.com/pmmp/PocketMine-MP) updated to support **Minecraft: Bedrock Edition v26.30** (network protocol **1001**).

## What changed

| Package | Before | After |
|---|---|---|
| `pocketmine/bedrock-protocol` | `57.1.0+bedrock-1.26.20` | `dev-bedrock-1.26.30` |
| `pocketmine/bedrock-data` | `6.6.0+bedrock-1.26.20` | `dev-bedrock-1.26.30` |
| `pocketmine/bedrock-block-upgrade-schema` | `5.2.0+bedrock-1.21.110` | `5.2.0` |
| `pocketmine/bedrock-item-upgrade-schema` | `1.17.0+bedrock-1.26.20` | `1.17.0` |

### Protocol info
- **Protocol:** `1001`
- **Minecraft version:** `v26.30` / `1.26.30`
- **PocketMine-MP base:** `5.43.3+dev`

### Fixes applied
- `StartGamePacket::create()` — added `isLoggingChat` parameter introduced in protocol 1001
- Block data regenerated from new `canonical_block_states.nbt` (bedrock-1.26.30)
- `pocketmine.yml` — `settings.enable-dev-builds: true` required (dev packages)

## Requirements

- PHP **8.2** (included in `bin/php/`)
- Windows x64

## Setup

```
1. Download or clone this repo
2. Run start.cmd
```

## Building from source

```bash
# Install Composer
php composer.phar install --no-dev --ignore-platform-reqs

# Run codegen (after updating bedrock-data)
php build/codegen/block-serializer-consts.php vendor/pocketmine/bedrock-data/canonical_block_states.nbt
php build/codegen/bedrockdata-path-consts.php
php build/codegen/biome-ids.php
php build/codegen/item-type-names.php vendor/pocketmine/bedrock-data/required_item_list.json
php build/codegen/known-translation-apis.php
php build/codegen/pocketmine-yml-property-consts.php
php build/codegen/registry-interface.php src generated

# Build phar
php -dphar.readonly=0 build/server-phar.php
```

## License

LGPL-3.0 — see [LICENSE](LICENSE)