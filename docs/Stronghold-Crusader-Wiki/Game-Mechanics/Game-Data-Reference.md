# Game Data Reference

This page serves as a reference for the various enumerations (enums) and data types used throughout the UCP and in AI configuration files like `character.json`.

## Farm Buildings

Used in the `Farm1` - `Farm8` AIC parameters.

| Value | Building |
| :--- | :--- |
| `None` | No Building |
| `WheatFarm`| Wheat Farm |
| `HopFarm` | Hop Farm |
| `AppleFarm`| Apple Orchard |
| `DairyFarm`| Dairy Farm |

## Resources

Used in `SellResource` parameters and for trade/economy logic.

| Value | Resource |
| :--- | :--- |
| `None` | None |
| `Wood` | Wood |
| `Hop` | Hops |
| `Stone` | Stone |
| `Iron` | Iron |
| `Pitch` | Pitch |
| `Wheat` | Wheat |
| `Bread` | Bread |
| `Cheese`| Cheese |
| `Meat` | Meat |
| `Apples`| Apples |
| `Beer` | Ale |
| `Flour` | Flour |
| `Bows` | Bows |
| `Crossbows` | Crossbows |
| `Spears`| Spears |
| `Pikes` | Pikes |
| `Maces` | Maces |
| `Swords`| Swords |
| `LeatherArmors` | Leather Armor |
| `IronArmors` | Metal Armor |

## Workshop Settings

Used in `BlacksmithSetting`, `FletcherSetting`, and `PoleturnerSetting`.

| Fletcher Settings | Poleturner Settings | Blacksmith Settings |
| :--- | :--- | :--- |
| `Bows` | `Spears` | `Maces` |
| `Crossbows`| `Pikes` | `Swords` |
| `Both` | `Both` | `Both` |

## Unit Types

Used in all `...Unit...` parameters (`DefUnit1`, `AttUnitMain1`, etc.).

| European Units | Arabian Units | Specialist Units |
| :--- | :--- | :--- |
| `EuropArcher` | `ArabArcher` | `Monk` |
| `Crossbowman` | `Slave` | `Tunneler` |
| `Spearman` | `Slinger` | `Engineer` |
| `Pikeman` | `Assassin` | `Ladderman` |
| `Maceman` | `HorseArcher` | |
| `Swordsman` | `ArabSwordsman`| |
| `Knight` | `FireThrower` | |

## Siege Engines

Used in `SiegeEngine` and `HarassingSiegeEngine` parameters.

| Value | Siege Engine |
| :--- | :--- |
| `None` | None |
| `Catapult` | Catapult |
| `Trebuchet` | Trebuchet |
| `Mangonel`| Mangonel |
| `SiegeTower`| Siege Tower |
| `BatteringRam`| Battering Ram |
| `Shield` | Portable Shield |
| `TowerBallista`| Tower Ballista |
| `FireBallista` | Fire Ballista |