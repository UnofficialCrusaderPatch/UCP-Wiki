# Roadmap: UCP Customization and UI/UX

This section covers ideas for improving the UCP launcher/GUI itself, ensuring it is a stable, intuitive, and powerful tool for both players and content creators.

---

### For Players: Stability & User Experience

-   **Improve Error Handling & Messaging:** This is a top priority.
    -   *Problem:* Cryptic errors like `„FATAL Failed to run main.lua (...) [callstack]“` are unhelpful and scare users.
    -   *Solution:* Replace them with clear, actionable messages (e.g., `„Outdated game version is not supported, please update!“` or `„This feature is not supported in your language version of the game.“`). Stack traces should be logged for developers but hidden from the user by default.
-   **Improve UCP Stability:** Focus on testing and double-checking new versions before public release to ensure they "just work," similar to the stability of UCP2.
-   **Add Update Checks:** Implement periodic or manual checks for new UCP versions without requiring a GUI restart.
-   **Add Translations:** The UCP GUI should be available in multiple languages, as UCP2 was.
-   **Improve Extension Naming Clarity:** Re-evaluate the name of the "UCP2 Legacy" extension to make its purpose more intuitive to new users.
-   **Allow In-Game Configuration:** Explore the possibility of making some UCP settings customizable while the game is running.

---

### For Content Creators: Quality of Life

-   **Improve Content Management & Discovery:**
    -   **Better Search:** Implement tagging of extensions and allow searching by tag or free text.
    -   **Show Dependencies:** Visually display the dependencies between extensions (and reverse dependencies).
-   **Add Tools for Content Creation:**
    -   **Plugin Templates:** Add a feature to create empty templates for new plugins (e.g., "AI pack," "map pack") that generates the required folder structure and config files.
    -   **File Explorer Integration:** Add buttons to "open extensions folder" or "show selected extension in folder" for quick access.