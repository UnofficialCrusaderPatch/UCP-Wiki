# Roadmap: General Gameplay Improvements

This section is a large collection of ideas for improving and expanding the core gameplay of Stronghold Crusader. The suggestions range from small bug fixes to major new features, all aimed at creating a deeper and more enjoyable experience.

---

### Core Combat & Unit Mechanics

These points focus on the behavior of units and the mechanics of combat.

-   **Improve Unit Stance Logic:**
    -   **Disable Stance Inheritance:** Prevent a group of selected units from all defaulting to the stance of the majority, which often causes unintended behavior.
    -   **Add Stance-Based Targeting:** Allow ranged units' targeting priorities to vary based on their stance (e.g., defensive stance targets units attacking allies), adding more strategic depth.
-   **Refine Unit Movement and Control:**
    -   **Add Unit Formations:** Implement commands for different formations, such as "spread out," "dense formation" (like on walls), "loose formation," or "line formation."
    -   **Fix Movement Speed on Selection:** Stop units from slowing down to a walking pace when selected. The proposed behavior is:
        -   *Default:* Units move at their individual top speeds.
        -   *With Modifier Key:* Units move together at the speed of the slowest unit in the group.
    -   **Improve Pathing Around Fire:** Units should intelligently path around fire if a safe route exists, instead of running directly into it.
-   **Rework Controversial Unit Mechanics:**
    -   **Assassin Visibility:** Propose a change where ranged units only target *Fully Visible* assassins, not *Partially Visible* ones. This would allow for more nuanced balancing of their detection range.
    -   **Gatehouse Capture Logic:** Make it so that **dead units no longer count** towards capturing or defending a gatehouse. This would remove frustrating, unintuitive, and random outcomes based on death animation lengths.
    -   **Projectile Trajectory vs. Slowed Units:** Fix ranged units constantly misfiring at targets slowed by terrain (swamps, hills). Projectiles should correctly lead the target based on its actual movement speed.
-   **Tweak Specific Unit Behaviors:**
    -   **Fire Ballista Targeting:** Rework Fire Ballistas to spread their shots across multiple targets like other ranged units, instead of focusing all firepower on a single unit and causing massive overkill.
    -   **Hunter Combat Behavior:** Allow hunters to shoot at enemy units in skirmish/multiplayer, as they already do in the campaign.
-   **Add a "Select Injured" Hotkey:** Introduce a hotkey that filters the current selection to only include units below a certain health threshold (e.g., 50%). This would make it much easier to pull back wounded units for healing.

---

### Economy, Buildings & Resources

This section covers the economic side of the game, including buildings and resource management.

-   **Improve Building Placement & Function:**
    -   **Orient Default Entrances:** Have building entrances automatically face towards the keep by default, solving unintuitive asymmetries and issues with siege tent placement.
    -   **Allow Sleeping for Individual Buildings:** Give players the ability to put a single building to sleep, rather than only having the option to sleep all buildings of that type.
    -   **Building Over Workers:** Revisit the WIP extension that allows placing buildings over workers.
        -   *Proposed Improvements:* Make it smarter by displacing units instead of killing them, or only despawning units on non-walkable tiles. Make it multiplayer-compatible and configurable.
-   **Rework Production & Resource Chains:**
    -   **Priest & Religion Rework:** Overhaul the religion system beyond simple value changes. See [GitHub Issue #48](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/48).
    -   **Stable Rework:** Reduce the base horse spawn rate but allow stables to "refill" their four horse spots without requiring the previously recruited knights to die first. This makes knights more viable for AIs and could improve multiplayer balance.
    -   **Fix/Improve Deer Breeding:** The deer population in vanilla Crusader always goes extinct over time due to a dysfunctional breeding mechanic. This should be fixed to work as it did in Stronghold 1.
    -   **Fix Hunter Pathfinding:** Hunters should be able to target deer that are very close to them.
    -   **Add an Automarket:** Implement an automarket building that comes with balancing costs (e.g., requires a worker, has a trading tax).
-   **Address Fire and Destruction Mechanics:**
    -   **Limit Instant Fire Spreading:** Slow down or limit the rate at which fire instantly spreads between adjacent buildings.
    -   **Disable Resources from Burning Buildings:** Prevent players from gaining back resources by deleting a building that is already on fire.

---

### Game Rules, Modes & Settings

These ideas focus on high-level game rules, new ways to play, and settings that can be configured before a match.

-   **Expand Skirmish & Multiplayer Options:**
    -   Allow map settings (trading restrictions, building restrictions, etc.) to be used in skirmish and multiplayer matches.
    -   Allow recruitment restrictions to be set for the Cathedral and Engineer's Guild.
    -   **Implement an AIV Selector in Skirmish Lobby:** Add a button for each AI player that allows the host to cycle through which `.aiv` castle file (1-8) that AI will use, or set it to random.
-   **Introduce New Game Modes & Features:**
    -   **Official Spectator Mode:** Formally add and support "active spectator mode" (human + AI on the same player slot) and "passive spectator mode" (AI only). Add a toggle in the lobby to configure this for player 1.
    -   **"Castle Preset" System:** An extension of spectator mode where a player can design a castle as an AIV, choose it in the lobby, and have the player 1 AI build it for them, with certain AI behaviors (like army control) disabled for the player to manage.
    -   **Finish the Replay System:** A much-requested feature for singleplayer, multiplayer, and content creation.
-   **Bring Back Features from Stronghold 1:**
    -   **Difficulty Tiers for Scenarios:** Re-enable the four difficulty tiers (Easy, Normal, Hard, Very Hard) that existed for scenario missions in the original Stronghold.
    -   **End-of-Mission Score Screens:** Restore the score screen after scenario missions to allow players to track their performance and compete for high scores.
-   **Fix Spawner Unit Behavior:** Spawner units should benefit from UCP attack behavior improvements instead of using vanilla logic.
-   **Add Option to Disable Ambient Units:** Provide a setting to disable the spawning of non-essential units (hovel children, jesters, ghosts, chickens, etc.) to save on the global unit limit, especially in games with many AIs.

---

### Quality of Life (QoL) & Control Improvements

These points focus on making the game feel smoother and less tedious to control.

-   **Improve Gameplay "Fluidity":** Investigate potential improvements to reduce lag, such as optimizing pathfinding or AI trade calculations that cause lag spikes.

---

### General Bug Fixes

-   **Fix Disappearing Control Groups:** Units should not disappear from a control group when they move onto a gatehouse.
-   **Fix Blocked Keep Entrance:** Address the pathfinding bug that can cause the keep's entrance to become temporarily blocked.
-   **Fix Ignored Weapon Restrictions:** Weapon restriction settings for blacksmiths, fletchers, etc., should be respected on scenario maps.
-   **Make Trebuchet/Catapult Accuracy Balanceable:** The current accuracy is effectively a boolean (either 100% accurate or wildly inaccurate). It should be adjustable.
-   **Allow Parallel Game Instances:** Make it possible to run SHC and SHC-E at the same time for easier testing and development.

---

### Potential Community Collaborations

-   **Cooperation with the SHCPlayer mod:** Explore potential cooperation with the creator of this popular mod, which has already implemented many fixes and features.
    <details><summary>SHCPlayer contents (Full List): (**show list**)</summary>

    - custom ingame UI for some settings adjustments and new features
    - fixed detection of invisible units and structures: you can no longer detect invisible enemy units and structures with the preview of a building
    - fixed double workers: you can no longer use sleep trick to assign more that one worker to the production
    - fixed stone teleport: blocking path to stone quarry no longer teleports stone to ox tether
    - fixed fire watchers stay at 0 popularity: fire watchers no longer stay with you at 0 popularity
    - fixed apple orchard size: apple orchard size after its construction has been changed from 11x11 to 12x12. it correspond to the size of its preview
    - fixed moat restoring under draw bridge: closing of the draw bridge no longer restores moat under it
    - fixed tunneler selection using bind keys: you can no longer select tunneler with bind keys after you send him to dig tunnel
    - added King of the Hill game mode. /koth lobby command
    - added observer mode. /observer or /obs lobby command
    - option to toggle window mode
    - option to change player color and /color lobby command
    - option to change network latency
    - save lobby settings in config file
    - improved moat planning in multiplayer matches
    - adapted avatar transfer to fit modern network bandwidth
    - adapted map transfer to fit modern network bandwidth
    - framerate independent camera movement
    - fixed v1.41 send map button
    - fixed destruction of siege engines. now engineers are destroyed together with siege
    - fixed unit binding in multyplayer. now bind group is available immediately
    - fixed bug that lead to cow carcass disappearing when it hit nearby area of siege unit
    - fixed incorrect destination point for military units
    - fixed route stuck for all labour units
    - fixed fast workers bug
    - fixed building's destruction gives double resources bug
    - fixed rally point sprite for horse archer
    - fixed attack focus of quarry stone pile
    - fixed missing space warning for destroyed buildings
    - fixed draw bridge destruction when neighbor building is destroyed
    - fixed cathedral rally point
    - fixed situation when labour and siege units stuck in a moat
    - fixed destruction of units hidden inside building
    - fixed bug that lead to climbing on a ladder back and forth
    - fixed assassin attack during climbing
    - fixed plants visualization for some maps
    - fixed stockpile destruction
    - fixed color table for some units
    - fixed save file name in multiplayer matches
    - deselect preview of the unique buildings after placement
    - tent and tunnel deselection disabling has been improved
    - draw preview of the building during camera movement
    - show version mismatch message in lobby chat
    - changed order of armory, stockpile and market products so they match each other
    - tons of other less significant bug fixes
    - Shift + drag to draw moat line (similar to building a wall)
    </details>