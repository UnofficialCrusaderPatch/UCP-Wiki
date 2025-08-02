# AI Personality Explained

The AI's behavior is more than just a list of parameters; it's a system of priorities and states. Understanding these systems is key to creating a believable and effective custom AI.

## Unit Recruitment Logic

The AI recruits units based on a priority system, regardless of the probabilities you set in the AIC.

**The absolute priority is always Sortie units.** If the AI needs to respond to an attack on its economy, it will recruit its defined `SortieUnitRanged` and `SortieUnitMelee` above all else.

### Recruitment States and Probabilities

After its initial castle is built and basic defenses are up, the AI enters a recruitment cycle based on its perceived power state (Weak, Default, or Strong). In each cycle, it uses the `RecruitProb` values to decide whether to recruit a **Defensive**, **Raid**, or **Attack** unit.

* `RecruitProbDef...`
* `RecruitProbRaid...`
* `RecruitProbAttack...`

These three probabilities for a given state (e.g., `Default`) should sum to 100. The AI "rolls a die" to pick a category, then attempts to recruit a unit from the corresponding list (`DefUnit1-8`, `RaidUnit1-8`, etc.). It tries to recruit from the top of the list down, skipping any unit it cannot afford.

### Gold and Recruitment Speed

* **`RecruitGoldThreshold`**: This is a critical parameter. If the AI's gold is below this threshold, it will **stop recruiting** any units for its main defensive or attack armies. It will *only* recruit sortie units and build resource buildings. This is often used to ensure Crusader lords have enough gold for workshops.
* **`RecruitInterval`**: This controls the speed of recruitment. A higher value means the AI recruits more slowly. Vanilla values are typically low (0-8).

## Resource Management

The AI's handling of its economy is governed by a set of clear rules.

### Selling Resources

The `SellResource01-15` list is absolute. If a resource is on this list, the AI will sell it immediately upon receiving it. This can cause problems if misconfigured. For example, if you tell an AI to sell `Wood` but it needs wood to build a fletcher's workshop, it might get stuck in a loop of buying and instantly selling wood, draining its gold.

### Maximum Stock (`Max...`)

These values define the AI's target inventory. The `MaxResourceVariance` parameter gives it a small buffer. Once the stock of a resource exceeds `MaxValue + MaxResourceVariance`, the AI will sell the excess.

* **Stone:** A good value is typically `[cost of most expensive stone building in AIV] + 10`.
* **Wood:** Should be at least `20`. A good estimate is `[# of wood-using workshops] * 8`.
* **Equipment:** A balanced value is `[# of armories] * 50 / [# of weapon types used]`.

### Aiding Allies

The `MinimumGoodsRequiredAfterTrade` parameter controls the AI's generosity. When an ally requests goods, the AI checks if sending the requested amount would leave it with less than this minimum value. If so, it denies the request.