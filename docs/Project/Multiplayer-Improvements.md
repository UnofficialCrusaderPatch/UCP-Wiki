# Roadmap: Multiplayer Improvements

The primary goal for multiplayer is to make it more accessible, stable, enjoyable, and configurable, allowing different communities to play to their liking.

---

### Quality of Life (QoL) & UI

-   **Lobby Improvements:**
    -   Allow players to **change their color** in the lobby, perhaps via a chat command.
    -   Display a **warning if a player has a different UCP config** than the host.
    -   Enable an option to **sync the host’s UCP config** with all lobby participants.
    -   Fix issues with player names and chat messages sometimes turning invisible.
-   **In-Game Improvements:**
    -   Provide **improved in-game and end-game statistics**.
    -   Add a **better chat history** display.
    -   Allow the host to **change the game speed** during a match.
-   **Improve the Autosave System:**
    -   Cycle between several autosave slots instead of overwriting one file.
    -   Add player names or timestamps to autosave filenames.
    -   Allow for shorter autosave intervals.

---

### Stability, Connectivity & New Game Modes

-   **Improve Network Stability:** Investigate and improve the networking code to reduce desyncs. Allow customization of parameters like input latency ("fake lag").
-   **Integrate Steamworks (RedirectPlay):** Polish and fully integrate the existing system for easier lobby discovery and joining directly through Steam.
    -   *Ensure Stability:* Host migration, preventing late-joining, proper handling of private/friends-only lobbies.
    -   *Improve UX:* Better lobby creation/password UI, more info in the lobby search list (player count, running game indicator).
-   **Enable Dynamic Alliances:** Restore the multiplayer lobby option from Stronghold 1 that allows alliances to be changed mid-game.
-   **Implement New Game Modes:**
    -   **King of the Hill:** Restore this game mode from Stronghold 1.
    -   **Ranked Play:** Potentially create a system for ranked games with leaderboards visible on the UCP website.
    -   **2-Player Co-op:** Allow two human players to share control of a single castle/army.
    -   **Multiplayer Scenarios:** Support maps with scripted events and AI opponents that can be played cooperatively.

---

### Community & External Integration

-   **Finish the Replay System:** This is a critical feature for both competitive analysis and content creation.
-   **Provide Better Guidance:** Make information about how to play multiplayer with UCP more available in the GUI, promoting relevant Discords, setups, etc.
-   **Cooperation with the SHCPlayer Mod:** Explore potential cooperation with the creator of this popular mod.
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