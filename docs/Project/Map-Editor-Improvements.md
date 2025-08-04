# Roadmap: Map Editor Improvements

The goal of these improvements is to empower players to create high-quality maps and scenarios with less hassle, integrating powerful community tools and fixing long-standing limitations of the vanilla editor.

---

### Tooling & Functionality Integration

-   **Integrate Existing Community Projects:** Bring powerful external tools into the UCP ecosystem as extensions for easier access and use.
    -   *Examples:* The map mirror tool, Altaruss's random map generator, gynt's "image-to-map" tool, and various template/utility maps.
-   **Incorporate Map Editor CE Scripts:** Integrate the functionality of various Cheat Engine scripts that add many helpful features, providing a stable and user-friendly interface for them. This includes:
    -   **Read-Only Map Info:** Displaying stats like unit counts, building counts, vegetation, etc., as a toggleable overlay.
    -   **Custom Event/Condition Editing:** Allowing for the full range of event parameters (e.g., invasion sizes beyond the UI limit) and making hidden event types accessible (e.g., `time on/off`, `cede castle`).
    -   **Direct Game Speed Control:** Allowing mapmakers to set very high or low game speeds for testing purposes.

---

### New Placeable Objects & Terrain Options

-   **Unlock Inaccessible Objects:** Make previously unavailable objects placeable in the editor, such as:
    -   All growth stages for trees.
    -   Siege tents.
    -   Apple trees on non-fertile ground.
    -   Assets from the original Stronghold (SH1 shrubs, SH1 gravel terrain).
-   **Allow Seagull Erasure:** Provide a tool to remove seagulls.

---

### Editor UI/UX and Core Functionality Fixes

-   **Improve Placement Tools & Hotkeys:**
    -   Add hotkeys to quickly switch between frequently-used objects, submenus, and brush sizes.
    -   Customize hardcoded parameters, like animal herd spawn counts or river depths.
    -   Allow setting and displaying plateau tool heights on the fly.
-   **Fix Broken Map Type Switching:** Restore the UI buttons from Stronghold 1 that allowed switching between map types (e.g., King of the Hill). This is a critical fix for mapmaking versatility.
-   **Standardize Map Properties:**
    -   **Import/Export Functionality:** Allow map properties (size, starting goods, events, etc.) to be imported and exported via a text format like JSON or YAML. This simplifies editing, allows for presets, and makes map data readable by other tools.
    -   **SHC-E Compatibility:** Provide a way to make Crusader Extreme maps compatible with the original Stronghold Crusader, or a tool to convert them.
-   **Restore SH1 Message Events:** Re-enable the "message" event type from Stronghold 1, which would make it much easier to create custom messages in scenario maps.