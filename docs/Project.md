# Project Roadmap & Ideas

Welcome to the project hub for the Unofficial Crusader Patch. This page contains a collection of high-level project goals and ideas for future development, taken directly from community suggestions and developer plans.

The roadmap is structured by importance, with key strategic initiatives detailed directly on this page. For longer, more comprehensive lists of specific feature requests, please see the linked sub-pages.

---

## 1. Custom Hotkeys & Controls

*A core priority is to modernize the game's control scheme to match user expectations for an RTS game. The ultimate goal is to abstract the input layer to allow for comprehensive customization.*

-   **Implement a Full Key-Remapping System:** Allow players to customize all gameplay hotkeys.
    -   *This can be implemented incrementally.* A first version could be configurable via a text file, providing immediate value while a full UI is developed.
-   **Introduce New Gameplay Hotkeys:** The community has requested several specific hotkeys to improve game flow:
    -   **Batch Actions:** Use modifier keys (e.g., `Shift` / `Ctrl`) for batch-recruiting units and batch-buying/selling goods at the market.
    -   **Building Selection:** Create hotkeys to select different building categories (e.g., food, industry, military).
    -   **Menu Shortcuts:** Add hotkeys to open frequently used menus, such as the trading post or granary.

---

## 2. Communication and Guidance

*To grow the community and make the UCP more accessible, improving our outreach and documentation is paramount.*

-   **Improve In-GUI Information:** Include more info directly in the GUI, or embed/link to resources like showcase videos on YouTube. The UCP2 release pages used images and GIFs to illustrate features; something similar in the UCP3 GUI could help visualize how things work.
-   **Create Modular Tutorials:** Instead of a single 30-minute "UCP tutorial for all the things", create more structured and modular videos that are easier to watch and keep updated.
-   **Bridge the Gap from UCP2 to UCP3:** A good UX-centered video or infographic could help people understand how "old and known" aspects of UCP2 correspond to what's in UCP3.
-   **Integrate Feedback Channels:** Add a feedback form or direct links to the Discord feedback section and GitHub issue trackers in the UCP GUI.
-   **Increase Visibility of Resources:** Guide people to the Discord and the UCP website more prominently from the GUI. Currently, these links are hard to find.
-   **Simplify Onboarding:** The first hurdle for new users is finding the correct GitHub repository and the right download. We must improve this process to reduce the need for manual assistance.
-   **Leverage Info Graphics:** These can go a long way in explaining complex topics.
    -   *They can explain the UCP itself* (e.g., "How To Create an Extension", "How To Use a Pack", "Feature Before-and-After").
    -   *They can explain game mechanics* (e.g., "Hotkeys", "Multiplayer Troubleshooting", "Unit Stances", hidden map editor features). Many players are still unaware of basic hotkeys, and making this information accessible is a huge QoL improvement.
    <details><summary>Example: Settlers United ("the UCP for _Settlers IV_") uses this approach. (**show image**)</summary>

    ![Settlers United Hotkeys Infographics](https://github.com/user-attachments/assets/892da70b-0a29-4fd4-8fca-c5c9b7020108)

    </details>
-   **Centralize Documentation:** Establish this wiki as the single source of truth where all relevant info can be found, and ensure it's easily discoverable from the GUI, Website, and Discord.
-   **Enhance the UCP GUI's Visuals:** The GUI is currently a "text monster." It needs more visual elements and built-in help resources to be less overwhelming for new users.
-   **Clarify Issue Reporting:** Guide people to the correct GitHub repositories for creating issues.

---

## 3. In-GUI Modding & UCP Experience

*The UCP launcher itself needs to be as user-friendly and powerful as possible, both for players and content creators.* The core goal is to improve stability, error handling, and the tools available for managing content.

-   **Key Goals:**
    -   **Improve Error Handling & Messaging:** Replace cryptic errors with clear, actionable messages.
    -   **Enhance Content Management:** Implement better content search (tagging, free text) and visually show dependencies between extensions.
    -   **Add QoL for Content Creators:** Provide tools like plugin templates and "open in folder" buttons.

> For the full, comprehensive list of all related ideas, see the **[UCP Customization page](./Project/UCP-Customization.md)**.

---

## 4. Game Visuals & UI Improvements

*While avoiding a total engine rewrite, many small-scale visual and UI improvements can be made. These ideas focus on providing value with reasonable effort.*

-   **Core Principle:** **Do not waste time on hugely complex visual changes** like rewriting the rendering pipeline. The focus is on quality-of-life fixes.
-   **Key Visual Ideas:**
    -   Allow changing texture packs at runtime.
    -   Enable using multiple texture packs simultaneously.
    -   Add overlays for more buildings (towers, gatehouses).
-   **Key UI Ideas:**
    -   Make hidden menus (like the scenario editor) visible in Crusader Extreme.
    -   Enhance the minimap with options for full-map view and larger unit dots.
    -   Fix numerous audio bugs related to volume and directional sound.

> For a full list of all visual and UI ideas, see the **[Game UI, UX & Visual Improvements page](./Project/Game-UI-UX.md)**.

---

## 5. User-Generated Content

*The lifeblood of the UCP is its community content. We need to make it easier for people to create, share, and use new content.*

-   **Core Goals:**
    -   Enable support for **custom campaigns** and **custom skirmish trails**.
    -   Enable **scenario events on skirmish maps** to allow for co-op multiplayer missions.
    -   Improve the handling of shared game files like `cr.tex` to make texture and text modding more modular.

> For the full list of ideas on this topic, see the **[User-Generated Content page](./Project/User-Generated-Content.md)**.

---

## Other Detailed Idea Collections

For other major categories, please see the dedicated pages containing comprehensive lists of ideas.

* **[AIV-Editor Improvements](./Project/AIV-Editor-Improvements.md)** - Quality-of-life fixes and new features for the classic AI castle editor.
* **[AI Improvements](./Project/AI-Improvements.md)** - Fixing long-standing AI issues and adding more depth and customization to AI behavior.
* **[General Gameplay Improvements](./Project/General-Gameplay-Improvements.md)** - A massive list of ideas for new features, balance changes, and bug fixes to core gameplay mechanics.
* **[Map Editor Improvements](./Project/Map-Editor-Improvements.md)** - Integrating community tools and adding new features to make map creation easier and more powerful.
* **[Multiplayer Improvements](./Project/Multiplayer-Improvements.md)** - A focus on stability, new game modes, and quality-of-life features for online play.

---