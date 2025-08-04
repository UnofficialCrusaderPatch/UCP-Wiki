# Roadmap: Game UI, UX & Visual Improvements

This section focuses on ideas for improving the in-game user experience (UX), user interface (UI), and general visuals. These changes are aimed at providing better quality of life, easier access to information, and a more polished graphical experience.

---

### In-Game Interface & Information Display

These points focus on what the player sees and how they receive information during gameplay.

-   **Make Hidden Menus Visible in Crusader Extreme:** Restore the buttons for "Create Scenario Maps," "Play Custom Scenario," and "Play Castle Builder" in SHC Extreme. These menus are fully functional but were inexplicably hidden.
-   **Improve Granary Interface:** Add a trade button or shortcut to the granary panel, similar to the stockpile and armoury, to make trading food more intuitive.
-   **Enhance the Minimap:**
    -   Provide an option for a **full-map minimap** that shows the entire battlefield at once.
    -   Slightly **increase the size of unit dots** on the minimap for better readability.
-   **Add a Unit Cap Indicator:** Display an in-game indicator when a player is approaching or has reached the global unit limit. See [GitHub Issue #50](httpss://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/50).
-   **Fix Broken Cathedral Rally Points:** Monks should consistently gather at the set rally point, instead of ignoring it after the first monk arrives.
-   **Fix Invisible Map Descriptions:** Ensure that map descriptions in the skirmish and multiplayer lobby screens are always visible.
-   **Enable Load Button in Skirmish Lobby:** Allow players to load a saved game directly from the skirmish lobby screen. See [GitHub Issue #42](https://github.com/UnofficialCrusaderPatch/UnofficialCrusaderPatch/issues/42).

---

### Visuals & Graphics

This section contains ideas for small-scale visual improvements that provide value with reasonable effort, without requiring a complete engine overhaul.

-   **Improve Texture Handling:**
    -   Allow **changing texture packs at runtime**.
    -   Enable using **multiple texture packs simultaneously** (e.g., one per player for their unique buildings and Lord).
-   **Enhance Building & Environment Sprites:**
    -   **Add new building overlays** for structures that lack them in vanilla (e.g., some towers, gatehouses), similar to the existing watchtower overlay.
    -   **Make wall and cliff textures configurable** to prevent the ugly, repeating texture loop on very tall structures.
    -   Utilize the unused **second "growth stage" sprite for dead trees**, which already exists in the game files.
    -   Adjust the **tower entrance door overlay** so its height correctly matches the height of adjacent walls, preventing it from floating in the air.
-   **Fix Visual Bugs & Annoyances:**
    -   **Fix endlessly spawning ravens** from skull piles.
-   **Add Customizable Corpse Despawn Time:** Introduce a multiplier to control how long dead unit corpses remain on the battlefield, allowing for either more immersive, dramatic battlefields or a cleaner, faster experience.

---

### Audio Fixes

These points address long-standing bugs and inconsistencies in the game's audio.

-   **Fix Directional Sound Bug:** Correct the issue where sounds are only played from the top-left portion of the game window on certain resolutions (e.g., 1024x768).
-   **Standardize Video Volume:** Make sounds from in-game videos (like AI taunts) respect the master sound volume settings.
-   **Fix Initial FX Volume:** The FX sound setting should be correctly applied when the game starts, not initialized to the wrong value.