# AI Character Parameters (AIC)

The personality of each AI lord in Stronghold Crusader is defined by a set of 169 parameters. These control everything from their economy and castle building to their military strategy.

> [!IMPORTANT]
> In UCP3, these parameters are no longer edited in `.aic` text files but are part of a modern `character.json` format within an AI extension. However, the meaning and function of these vanilla parameters remain the same and are foundational to understanding and creating custom AI. Future UCP modules may add *new* parameters to this list, which will be documented by the modules that introduce them.

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