# Roadmap: AI Improvements

This document outlines potential improvements to the AI's core behavior, focusing on fixing long-standing bugs, adding more nuanced strategic options, and giving AI modders greater control through new AIC parameters.

---

## General Bugs & Pathfinding Fixes

These items address general bugs that cause the AI to behave illogically or get stuck.

-   **Fix AIV Castle Offset:** Prevent AI castles built from `.aiv` files from being offset to one side based on the player's starting keep rotation.
-   **Prevent Attack Armies from Freezing:** Fix the bug where AI attack armies freeze indefinitely if all their laddermen are killed during an assault.
-   **Prevent AI from Despawning Attack Units:** Fix the bug where an AI despawns its own attack army if it cannot find a path back to its own keep.
-   **Fix Pathing Through Enemy Gates:** Prevent AI troops from assuming they can walk through unconquered enemy gatehouses.
    -   *Current Problem:* Troops march to a closed gate, get stuck, repath to another closed gate, and repeat this loop instead of attacking.
    -   *Proposed Solution:* AI should correctly identify enemy gates as obstacles and either attack them or path around them.
-   **Address Engineer Recruitment Bugs:** Investigate and fix issues related to the AI incorrectly counting or managing its engineers. *(Further details needed)*.

---

## AIC Parameter Enhancements

This section focuses on exposing hardcoded behaviors as new **AIC (AI Character) parameters**, giving modders more precise control over an AI's personality.

-   **Improve Attack Army Composition (`AttMaxDefault`)**
    -   Refine the logic of this crucial AIC parameter, which determines the size of the main fighting force before specialists are recruited. See the related [GitHub Issue #49](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/49).
-   **Improve "Any" Targeting (`TargetChoice`)**
    -   Implement a truly randomized "Any" target choice, instead of the current version which follows a fixed internal player list. See the related [GitHub Issue #52](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/52).
-   **Add Maximum Siege Engines per Attack:** Introduce a new AIC parameter to control the maximum number of siege engines in a single attack wave. The AI should iterate through its list of preferred siege engines to meet this number.
-   **Add Minimum Wood Reserve:** Introduce an AIC parameter to set a minimum wood reserve, preventing the AI from selling or using its last pieces of wood when it's critical for other buildings.
-   **Make Well-Sleeping Behavior Configurable:** The AI currently sets its wells to sleep when gold is low based on hardcoded logic.
    -   *Proposal:* Expose this via AIC parameters, allowing modders to define:
        a) The gold threshold for what constitutes "low on gold."
        b) The duration the AI must be below that threshold before wells are put to sleep.
-   **Make Sortie Recruitment Configurable:** The AI's decision to launch a sortie (a defensive counter-attack) is currently hardcoded and often drains an AI's resources for little gain.
    -   *Proposal:* Add AIC parameters to control the *probability* of recruiting sortie units, giving modders the ability to create AIs that are less reactive or that save resources for main attacks.
-   **Improve and AIC-ify AI Panic Tributes:** The logic for when an AI sends gold to a player threatening it should be more nuanced and controllable via the AIC. See the related [GitHub Issue #47](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/47).
-   **AIC-ify Attack Force Scaling:** Rework the hardcoded "attack increase factor" into AIC parameters.
    -   *Goal:* Allow for more diverse AI attack patterns. For example, one AI could start with small attacks that scale up quickly, while another could build very large armies that attack less frequently.
    -   *Implementation:* This could be a base value in the AIC, potentially with a multiplier that still respects the global game settings (e.g., Deathmatch advantage).
-   **Improve Pitch Ditch Logic:**
    -   **Prevent Friendly Fire:** Stop the AI from lighting allied or enemy pitch ditches with fire arrows. This behavior is not possible for human players and often results in the AI burning down allied castles.
    -   **Make Trigger Configurable:** Turn the "enemy power threshold" required to light a pitch ditch into an AIC variable. This would prevent all AIs from being equally (and overly) trigger-happy.

---

## Unit Behavior & Recruitment

These suggestions focus on how the AI recruits, deploys, and uses its defensive units.

-   **Fix and Expand Defensive Melee Unit Spots:**
    -   *Problem:* The AI currently ignores AIV troop spots for Swordsmen, Pikemen, and Arabian Swordsmen.
    -   *Solution (a):* Fix the AI to correctly use all existing melee troop spots.
    -   *Solution (b):* Add the missing ability for modders to place troop spots for Monks and Tunnelers in the AIV editor.
-   **Make Defensive Patrol Behavior an AIC Parameter:** Currently, whether a defensive melee unit patrols or stands still is hardcoded by unit type (e.g., Spearmen patrol, Knights stand still). This should be a choice in the AIC to allow for more flexible castle defense designs.
-   **Create Separate "Outer Patrol" Unit Slots:** Add a new list of defensive unit slots in the AIC specifically for patrols *outside* the castle walls.
    -   *Benefit:* This allows modders to design more logical defenses, using fast cavalry (Knights, Horse Archers) for outer patrols while keeping infantry (Pikemen, Swordsmen) on the walls, instead of forcing one unit type to do both.
-   **Offer an Alternative Defensive Recruitment Logic:** Add an AIC toggle for a new recruitment mode.
    -   *Current Behavior:* The AI tries to recruit equally from all `DefUnit` entries, skipping any it can't afford. This can lead to unbalanced army compositions.
    -   *Proposed New Behavior:* The AI tries to maintain a target ratio for each defensive unit type, only recruiting a unit if it's below its target percentage. This gives modders much better control over long-term defensive army composition.
-   **Enable AI-to-AI Help Requests:** Allow allied AI players to request resources from each other, just as a human player can.

---

## Attack & Siege Logic

These points address specific behaviors during offensive maneuvers.

-   **Improve Assassin Attack Pathing:**
    -   **Assassins in the attack force should be smarter:**
        a) They should *only* target the gatehouses of their designated attack victim, not other players on the map.
        b) They should prioritize attacking gatehouses that *do not* have a drawbridge.
    -   **The rest of the army should be smarter:**
        a) Other units should recognize when assassins have successfully opened a gate.
        b) They should then path *through the open castle* to the keep, instead of getting stuck attacking walls.
-   **Fix Unreliable Siege Engine Behavior:**
    -   Prevent attacking Catapults and Fire Ballistas from rolling into enemy melee range without firing.
    -   Fix the bug where the AI often stops building harassment siege engines late in a match.
    -   Prevent the AI from building new harassment siege engine tents directly on top of existing ones.
-   **Improve Raid Targeting:** Change the raid logic from "attack the oldest enemy building on the map" to "attack a *nearby* enemy building." This will prevent suicidal raids where units run across the entire map to attack a single woodcutter's hut.
-   **Fix Stuck Harassment Siege Engines:** Improve pathing to prevent harassment siege engines from getting stuck inside or behind the AI's own castle.
-   **Expand Allowed Units for Raids/Sorties:**
    -   Allow **Monks** and **Tunnelers** to be used as sortie units.
    -   Allow **Tunnelers** to be used as raid units.
    -   Allow **Battering Rams** to be used in harassment armies.