# Unit Power Table

Stronghold Crusader assigns an internal "power" value to each unit. This value is a crucial component in several AI decision-making processes, including:

* **Calculating Army Strength:** When an AI with the `Balanced` [Targeting Type](AI-Targeting-Types) decides who to attack, it calculates the total power of each potential target's army.
* **"Greatest Lord" Score:** The power of a player's army contributes to their overall score, which can influence AI behavior.

Below is the table of these internal power values. Note that siege engines have a base power plus an additional value for each engineer manning them.

| Unit | Power Value |
| :---: | :---: |
| **European Troops** | |
| Archer | 5 |
| Spearman| 4 |
| Maceman | 10 |
| Crossbowman | 10 |
| Pikeman | 10 |
| Swordsman | 30 |
| Knight | 35 |
| **Arabian Troops** | |
| Arabian Archer | 8 |
| Slave | 1 |
| Slinger | 2 |
| Assassin | 14 |
| Horse Archer | 15 |
| Arabian Swordsman | 20 |
| Firethrower | 16 |
| **Specialist Troops** | |
| Monk | 8 |
| Tunneler | 5 |
| Engineer | 5 |
| Ladderman | 1 |
| **Siege Engines** | |
| Catapult | 25 + (2 * 5) |
| Trebuchet | 0 + (3 * 5) |
| Siege Tower | 0 + (4 * 5) |
| Battering Ram | 0 + (4 * 5) |
| Fire Ballista | 25 + (2 * 5) |
| Portable Shield | 0 + (1 * 5) |
| Mangonel | 0 + (2 * 5) |
| Tower Ballista | 0 + (2 * 5) |