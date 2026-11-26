# AI Character Parameters (AIC)

The personality of each AI lord in Stronghold Crusader is defined by a set of 169 parameters. These control everything from their economy and castle building to their military strategy.

> [!IMPORTANT]
> In UCP3, AIC Loader can load personality files, and AI Swapper can load the lowercase `aic` object in `character.json`. The vanilla parameters below retain their meaning. See [Fields added by modules](#fields-added-by-modules) for the extra AIV Troop Behaviour and Ox Tethers fields, their provider modules, required versions and activation settings.

| Name | Value Type | Description |
| :--- | :--- | :--- |
| **Economy & Popularity** | | |
| `CriticalPopularity` | 0-10000 | 10000 = 100 popularity. Below this, the AI sells goods aggressively to raise gold. |
| `LowestPopularity` | 0-10000 | Below this, AI sets taxes towards `TaxesMin` and gives extra rations until `HighestPopularity` is reached. |
| `HighestPopularity` | 0-10000 | Above this, AI increases taxes until a stable popularity modifier of 0 to -3 is achieved. |
| `TaxesMin` | 0-12 | Minimum tax level allowed. Maps to the in-game tax settings from +7 to -24 popularity. |
| `TaxesMax` | 0-12 | Maximum tax level allowed. |
| **Resource Management** | | |
| `Farm1` - `Farm8` | FarmBuilding | An array of 8 farm building slots. The AI builds these in sequence. |
| `PopulationPerFarm` | Integer | The AI builds one farm for every X peasants. Set to 0 to disable. |
| `PopulationPerWoodcutter`| Integer | Builds one woodcutter for every X peasants. |
| `PopulationPerQuarry` | Integer | Builds one stone quarry for every X peasants. |
| `PopulationPerIronmine` | Integer | Builds one iron mine for every X peasants. |
| `PopulationPerPitchrig` | Integer | Builds one pitch rig for every X peasants. |
| `MaxFarms` | Integer | Maximum number of farms the AI will build. |
| `MaxWoodcutters` | Integer | Maximum number of woodcutters. |
| `MaxQuarries` | Integer | Maximum number of quarries. |
| `MaxIronmines` | Integer | Maximum number of iron mines. |
| `MaxPitchrigs` | Integer | Maximum number of pitch rigs. |
| `BuildInterval` | Ticks | Game ticks between construction attempts. Only applies when gold is <= 5000. |
| `ResourceRebuildDelay`| Ticks | Delay before the AI rebuilds a destroyed resource building. |
| `MaxFood` | Integer | Max stock for each individual food type (apples, cheese, etc.). |
| `MinimumApples` | Integer | Emergency reserve. AI will buy apples if stock falls below this. |
| `MinimumCheese` | Integer | Emergency reserve for cheese. |
| `MinimumBread` | Integer | Emergency reserve for bread. |
| `MinimumWheat` | Integer | AI will prioritize buying wheat if stock falls below this. |
| `MinimumHop` | Integer | AI will prioritize buying hops if stock falls below this. |
| `TradeAmountFood` | Integer | The quantity of food/wheat/hops bought in a single transaction. |
| `TradeAmountEquipment`| Integer | The quantity of weapons/armor bought in a single transaction. |
| `DoubleRationsFoodThreshold` | Integer | The AI gives double rations if its stock of a food type exceeds this value. |
| `MaxWood` | Integer | Maximum wood to store in the stockpile. |
| `MaxStone` | Integer | Maximum stone to store in the stockpile. |
| `MaxResourceOther` | Integer | Maximum stock for hops, iron, pitch, and flour. |
| `MaxEquipment` | Integer | Maximum stock for each individual weapon/armor type. |
| `MaxBeer` | Integer | Maximum beer to store in the stockpile. |
| `MaxResourceVariance` | Integer | Tolerance for all goods before the AI sells excess back down to its max stock level. |
| `SellResource01`-`15` | Resource | An array defining which resources the AI sells immediately upon acquiring them. |
| **Military & Recruitment** | | |
| `RecruitGoldThreshold`| Gold | AI will not recruit attack/defense units (except sorties) or buy workshop resources if its gold is below this value. |
| `RecruitProbDefDefault`| Percent | Probability (0-100) of recruiting a defensive unit when in a 'default' power state. |
| `RecruitProbDefWeak` | Percent | Probability of recruiting a defensive unit when in a 'weak' power state. |
| `RecruitProbDefStrong` | Percent | Probability of recruiting a defensive unit when in a 'strong' power state. |
| `RecruitProbRaidDefault`| Percent | Probability of recruiting a raid unit (Default, Weak, Strong probabilities should sum to 100). |
| `RecruitProbRaidWeak` | Percent | Probability of recruiting a raid unit when weak. |
| `RecruitProbRaidStrong` | Percent | Probability of recruiting a raid unit when strong. |
| `RecruitProbAttackDefault` | Percent | Probability of recruiting an attack unit. |
| `RecruitProbAttackWeak` | Percent | Probability of recruiting an attack unit when weak. |
| `RecruitProbAttackStrong`| Percent | Probability of recruiting an attack unit when strong. |
| `RecruitInterval` | Ticks | Base interval between recruitment attempts. |
| `RecruitIntervalWeak`| Ticks | Recruitment interval when the AI is weak (e.g., <8 troops, <200 gold). |
| `RecruitIntervalStrong`| Ticks | Recruitment interval when the AI is strong (e.g., >=40 troops, >=200 gold). |
| **Defense** | | |
| `DefTotal` | Integer | Total number of defensive units (wall + patrol) the AI aims to maintain. |
| `DefUnit1` - `DefUnit8` | Unit | An array of 8 defensive unit slots. The AI recruits from this list in order. |
| `DefDiggingUnit` | DiggingUnit | Unit type used to dig the AI's own moat. |
| `DefDiggingUnitMax`| Integer | Maximum number of moat diggers. |
| `DefWallPatrolGroups` | Integer | Number of defensive wall-patrol groups used by native and custom patrol movement. |
| `DefWallPatrolRallyTime` | Ticks | Time for patrol groups to move between AIV-defined rally points. |
| `DefSiegeEngineGoldThreshold` | Gold | Gold threshold for building defensive siege engines. |
| `DefSiegeEngineBuildDelay` | Ticks | Delay before building/rebuilding AIV-defined defensive siege engines. |
| **Sorties (Reaction Force)** | | |
| `SortieUnitRanged` | Unit | Ranged unit sent to guard recently attacked buildings. |
| `SortieUnitRangedMin`| Integer | Minimum number required before sending them out. |
| `SortieUnitMelee` | Unit | Melee unit sent to attack enemies attacking the AI's buildings/workers. |
| `SortieUnitMeleeMin` | Integer | Minimum number required before sending them out. |
| **Raids (Harassment)** | | |
| `RaidUnitsBase` | Integer | Base number of units in a raid force. |
| `RaidUnitsRandom` | Integer | Maximum random number of additional units for a raid. |
| `RaidUnit1` - `RaidUnit8` | Unit | An array of 8 raid unit slots. |
| `RaidRetargetDelay` | Ticks | Time until raiding units are given a new command. |
| `HarassingSiegeEngine1`-`8` | SiegeEngine | Array of harassing siege engines the AI can build. |
| `HarassingSiegeEnginesMax` | Integer | Maximum number of harassing siege engines (capped at 10). |
| **Attacks (Main Sieges)** | | |
| `TargetChoice` | TargetingType | Defines how the AI chooses its main attack target (Gold, Balanced, Closest, etc.). |
| `AttForceBase` | Integer | The base number of units in a main attack force. |
| `AttForceRandom` | Integer | Maximum random number of additional units in an attack. |
| `AttForceSupportAllyThreshold` | Integer | If the attack force exceeds this size, the AI will assist allies. |
| `AttForceRallyPercentage`| Percent | Percentage of the attack force that must gather before launching the assault (0-100). |
| `AttAssaultDelay`| Ticks | Delay before the main army attacks after siege engines are in position. |
| `AttMaxEngineers` | Integer | Maximum number of engineers in an attack force. |
| `AttMaxLaddermen` | Integer | Maximum number of laddermen. |
| `AttMaxTunnelers`| Integer | Maximum number of tunnelers. |
| `AttMaxAssassins` | Integer | Maximum number of assassins. |
| `AttUnitMain1`-`4`| Unit | The four primary unit types for the main attack army. Recruited in order of cost/priority. |
| `AttMaxDefault` | Integer | The number of main army units to recruit before filling out other specialist roles (laddermen, assassins, etc.). |
| `SiegeEngine1`-`8`| SiegeEngine | Array of siege engines for the main attack. |
| `CowThrowInterval` | Integer | Number of stones thrown by catapults/trebs before launching a diseased cow. 0 disables, -1 is cows only. |

## Fields added by modules

These fields are registered by the named module through [AIC Loader](https://github.com/UnofficialCrusaderPatch/extension-aicloader). Installing a UCP framework version alone does not add them. Enable the provider module and its AIC mode, and declare the provider in your AI extension's `definition.yml` dependencies when your AI relies on these rules. A field supplied without its provider is unknown to the loader.

The fields belong to an **AI personality**, not a player slot. Players using the same personality share the settings. Supply them either in `Personality` in an AIC Loader file, or in the lowercase `aic` object in AI Swapper's `character.json`. AI Swapper is needed only for the latter route, not for these extra fields themselves. Field names and string values are case-sensitive.

### AIV Troop Behaviour

**Introduced by:** `aiv-troops-behaviour` 0.2.0 ([feature PR](https://github.com/DanielFleger/ucp3-fixes/pull/2)). These are the named-value fields in the proposed module; the feature is not yet a stable store release. The former narrow `aiv-troop-spot-fix` does not provide them.

**Requirements:** Crusader or Crusader Extreme 1.41, framework >=3.0.4, frontend >=1.0.16, and `aicloader >=1.1.0`. Enable the module, then **Troop settings** and **Use AIC overrides** under **AI → AIV Troop Behaviour**. The position-loading fix alone does not enable the extra behavior fields. AI Swapper is optional.

The two settings are independent:

- **InitialRole:** `"defend"` assigns unassigned starting/scenario troops to defense; `"dig"` assigns capable troops to moat digging. This does not replace normal recruitment settings or reassign units already in a group.
- **Movement:** `"hold"` keeps a defensive group at its assigned AIV slot; `"patrol"` cycles between slots using `DefWallPatrolGroups` and `DefWallPatrolRallyTime`. Holding does not disable combat or special duties. Zero patrol groups means no cycling; absent AIV slots produce no custom slot order.

Omit a field to inherit the next applicable setting. Priority is **troop AIC → common AIC → troop menu choice → game behavior**, including enabled fixes. There are no public numeric values or explicit native/inherit values. No overrides and untouched menu settings preserve game behavior.

The common role accepts only `"defend"`. Select `"dig"` explicitly for Engineers, Crusader archers, Spearmen, Pikemen, Macemen or Slaves. Other troops cannot dig. If a capable unit's live digging flag is disabled, a digging request falls back to defense; digging also needs moat tiles.

| Field | Allowed values | Applies to |
| --- | --- | --- |
| `AIVTroops_InitialRole` | `"defend"` | Common starting/scenario role |
| `AIVTroops_Movement` | `"hold"`, `"patrol"` | Common defender movement |
| `AIVTroops_InitialRole_Engineer` | `"defend"`, `"dig"` | Engineers: starting/scenario role |
| `AIVTroops_Movement_Engineer` | `"hold"`, `"patrol"` | Engineers: defender movement |
| `AIVTroops_InitialRole_Archer` | `"defend"`, `"dig"` | Crusader archers: starting/scenario role |
| `AIVTroops_Movement_Archer` | `"hold"`, `"patrol"` | Crusader archers: defender movement |
| `AIVTroops_InitialRole_Crossbowman` | `"defend"` | Crossbowmen: starting/scenario role |
| `AIVTroops_Movement_Crossbowman` | `"hold"`, `"patrol"` | Crossbowmen: defender movement |
| `AIVTroops_InitialRole_Spearman` | `"defend"`, `"dig"` | Spearmen: starting/scenario role |
| `AIVTroops_Movement_Spearman` | `"hold"`, `"patrol"` | Spearmen: defender movement |
| `AIVTroops_InitialRole_Pikeman` | `"defend"`, `"dig"` | Pikemen: starting/scenario role |
| `AIVTroops_Movement_Pikeman` | `"hold"`, `"patrol"` | Pikemen: defender movement |
| `AIVTroops_InitialRole_Maceman` | `"defend"`, `"dig"` | Macemen: starting/scenario role |
| `AIVTroops_Movement_Maceman` | `"hold"`, `"patrol"` | Macemen: defender movement |
| `AIVTroops_InitialRole_Swordsman` | `"defend"` | Swordsmen: starting/scenario role |
| `AIVTroops_Movement_Swordsman` | `"hold"`, `"patrol"` | Swordsmen: defender movement |
| `AIVTroops_InitialRole_Knight` | `"defend"` | Knights: starting/scenario role |
| `AIVTroops_Movement_Knight` | `"hold"`, `"patrol"` | Knights: defender movement |
| `AIVTroops_InitialRole_Slave` | `"defend"`, `"dig"` | Slaves: starting/scenario role |
| `AIVTroops_Movement_Slave` | `"hold"`, `"patrol"` | Slaves: defender movement |
| `AIVTroops_InitialRole_Slinger` | `"defend"` | Slingers: starting/scenario role |
| `AIVTroops_Movement_Slinger` | `"hold"`, `"patrol"` | Slingers: defender movement |
| `AIVTroops_InitialRole_Assassin` | `"defend"` | Assassins: starting/scenario role |
| `AIVTroops_Movement_Assassin` | `"hold"`, `"patrol"` | Assassins: defender movement |
| `AIVTroops_InitialRole_ArabianArcher` | `"defend"` | Arabian archers: starting/scenario role |
| `AIVTroops_Movement_ArabianArcher` | `"hold"`, `"patrol"` | Arabian archers: defender movement |
| `AIVTroops_InitialRole_HorseArcher` | `"defend"` | Horse archers: starting/scenario role |
| `AIVTroops_Movement_HorseArcher` | `"hold"`, `"patrol"` | Horse archers: defender movement |
| `AIVTroops_InitialRole_ArabianSwordsman` | `"defend"` | Arabian swordsmen: starting/scenario role |
| `AIVTroops_Movement_ArabianSwordsman` | `"hold"`, `"patrol"` | Arabian swordsmen: defender movement |
| `AIVTroops_InitialRole_FireThrower` | `"defend"` | Fire throwers: starting/scenario role |
| `AIVTroops_Movement_FireThrower` | `"hold"`, `"patrol"` | Fire throwers: defender movement |

Example AIC Loader file, referenced through `aicloader.aicFiles`:

```json
{
  "AICharacters": [
    {
      "Name": "Rat",
      "Personality": {
        "AIVTroops_InitialRole": "defend",
        "AIVTroops_InitialRole_Slave": "dig",
        "AIVTroops_Movement": "hold",
        "AIVTroops_Movement_Spearman": "patrol",
        "DefWallPatrolGroups": 2,
        "DefWallPatrolRallyTime": 10
      }
    }
  ]
}
```

For AI Swapper, put the same fields in `character.json`'s `aic` object:

```json
{
  "aic": {
    "AIVTroops_InitialRole_Slave": "dig",
    "AIVTroops_Movement_Spearman": "patrol"
  }
}
```

Restart and start a new match after editing. AIC reset clears this module's overrides and returns to the menu defaults. Merely omitting a field from a later partial AIC write does not clear a value already applied in that session. Earlier unreleased builds accepted numbers: replace role 1/2 with `"defend"`/`"dig"`, movement 1/2 with `"hold"`/`"patrol"`, and remove -1/0 fields. Removing an old explicit 0 now inherits other configured choices.

### AI: Ox Tethers

**Introduced by:** [`ai-ox-tethers` 1.0.0](https://github.com/gynt/ucp-extension-ai-ox-tethers/tree/26c92fa). These seven fields remain numeric in 1.0.3 and the proposed 1.0.4 menu update; the AIV string enums do not apply to them.

**Requirements:** `ai-ox-tethers >=1.0.0`, framework >=3.0.4, frontend >=1.0.2 and `aicloader >=1.1.0`. Enable the module's **Ox Tethers** switch under **AI → Buildings → Ox Tethers**, then select its AIC mode (`oxtethers.mode: use_aic`). The other mode (`override_aic`) uses menu settings and does not register these fields. AI Swapper is optional. Disable the overlapping initial-ox-tether patch in `ucp2-legacy` if it causes a hook conflict.

These fields change whether an AI builds more tethers and which quarry it builds them for. A *linked tether* is associated with the quarry its worker last collected stone from. The five dynamic limits/thresholds apply when `AIOxTethers_Logic` is 1; the initial-tether switch is independent.

| Field | Values | Meaning |
| --- | --- | --- |
| `AIOxTethers_DisableInitialOxTether` | 0 or 1 | 0 keeps the automatic tether when a quarry is built/rebuilt; 1 disables it. |
| `AIOxTethers_Logic` | 0 or 1 | 0 uses the game's additional-tether decision; 1 uses the module's dynamic rules below. |
| `AIOxTethers_MaxOxTethers` | Non-negative integer | Stop requesting additional tethers when the player's total reaches this limit. |
| `AIOxTethers_DynamicMaxOxTethers` | Non-negative number | Stop requesting additional tethers when the total reaches this multiplier × quarry count. |
| `AIOxTethers_MinimumOxTethersPerQuarry` | Non-negative integer | Request a tether for a quarry below this linked-tether count, subject to the two total limits. |
| `AIOxTethers_MaximumOxTethersPerQuarry` | Non-negative integer | Exclude a quarry from stone-load requests when its linked count is at or above this value. Keep the minimum at or below this maximum. |
| `AIOxTethers_ThresholdStoneLoad` | Non-negative number | Request another tether when stored stone / linked tethers exceeds this value. With no linked tether, use stored stone directly. A full stone pile is 48. |

These limits govern new requests; they do not delete existing tethers or cap the game's separate automatic initial-tether placement. Use the initial-tether switch too if that automatic placement should stop. The current AIC handler checks numeric type only, so use the meaningful ranges shown above; it does not enforce the Customizations slider limits.

On initial enable, the menu seeds each AI's values and supplied AIC fields replace them. An AIC reset (including character replacement) instead restores fixed module defaults: initial tether **0**, logic **0**, total **100**, quarry multiplier **3**, minimum **1**, maximum **3**, threshold **20**. Omitted fields after reset retain those reset defaults, which can differ from your menu choices. Explicitly provide the fields your AI depends on.

Example personality fragment (inside `Personality` or `aic` as described above):

```json
{
  "AIOxTethers_DisableInitialOxTether": 1,
  "AIOxTethers_Logic": 1,
  "AIOxTethers_MaxOxTethers": 100,
  "AIOxTethers_DynamicMaxOxTethers": 4,
  "AIOxTethers_MinimumOxTethersPerQuarry": 1,
  "AIOxTethers_MaximumOxTethersPerQuarry": 6,
  "AIOxTethers_ThresholdStoneLoad": 20
}
```

Implementation references: [Ox Tethers registration/reset](https://github.com/gynt/ucp-extension-ai-ox-tethers/blob/main/dynamic/aic.lua), [dynamic decisions](https://github.com/gynt/ucp-extension-ai-ox-tethers/blob/main/dynamic/init.lua), [AIV fields and policy](https://github.com/Krarilotus/ucp3-fixes/blob/feature/aic-troop-behavior/aiv-troops-behaviour/behavior/policy.lua), and [AI Swapper's character AIC reader](https://github.com/UnofficialCrusaderPatch/extension-aiSwapper/blob/main/scripts/aic.lua).
