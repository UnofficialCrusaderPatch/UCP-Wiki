# AI Targeting Types

The `TargetChoice` parameter in an AI's `character.json` file is one of the most important settings, as it dictates how an AI lord chooses its primary attack target. Understanding these types is crucial for predicting and designing AI behavior.

| Targeting Type | Description |
| :--- | :--- |
| `Gold` | Always attacks the enemy player with the largest amount of gold. |
| `Balanced` | Attacks the enemy based on a calculated "weakness" score. This is the most complex and nuanced targeting type. |
| `Closest` | Always attacks the closest enemy, measured from keep to keep. |
| `Any` | Attacks the next enemy in the internal player list. This can appear random but follows a fixed order. |
| `Player` | Always targets a human player first. If no human players are enemies, it defaults to `Closest`. |

## The "Balanced" Targeting Formula

When an AI is set to `Balanced`, it calculates a weight for every other enemy player. It will then attack the player with the **lowest** calculated weight.

The formula is:
`weight = (target's gold / 100) + (power of target's army) + (target's available peasants) + (2 * distance_to_target)`

* **Power of Target's Army:** This is the sum of the power values of all the target's units. See the [Unit Power Table](Unit-Power-Table) for these values.
* **Distance to Target:** This is the map distance between the AI's keep and the target's keep.