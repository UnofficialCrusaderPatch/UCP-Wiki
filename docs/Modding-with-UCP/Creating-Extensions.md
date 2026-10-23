# Creating Extensions

This section covers the practical steps and core concepts for creating your own UCP extensions. All custom content for the UCP is packaged as an **Extension**. They are "plug-and-play" components that can customize, expand, or completely overhaul the game. They live in the `ucp/` folder and are categorized into two types: **Plugins** and **Modules**.

## Plugins vs. Modules

### Plugins
Plugins are extensions that primarily add or modify **game content**.
* **Content:** They can contain new game resources like AI files (`.aiv`, `character.json`), maps, graphics, or sound effects. These files must be placed in a `/resources/` subfolder.
* **Safety:** Plugins cannot directly modify game code. They can only interact with the game by calling Lua functions explicitly exposed by the framework or by modules.
* **Format:** Plugins are stored as regular folders (e.g., `ucp/plugins/MyMapPack-1.0.0/`).

### Modules
Modules are powerful extensions that can **modify game code**.
* **Permissions:** Modules have special permissions to directly patch the game's executable memory using the Runtime Patching System. They have access to core framework functions for creating hooks and detours.
* **Custom Code:** Modules can include compiled DLL files (`.dll`) for high-performance code. The `init.lua` script is responsible for loading the DLL and linking its functions to the game via the Lua state.
* **Security:** Because they can execute arbitrary code, modules must be cryptographically signed. The framework will only load modules that are trusted. For development, you can use the Developer Build of UCP to bypass this signature check.
* **Format:** Modules are distributed as zipped archives (e.g., `ucp/modules/MyGameplayMod-0.0.1.zip`).

---
## Getting Started Guides

Here are the guides to help you build your own extension.

* **[Creating a Plugin](./Creating-Extensions/Creating-a-Plugin.md)**
    * The best place to start. A step-by-step tutorial showing you how to use the UCP GUI to generate a clean plugin template and add your content.

* **[Configuration (`options.yml` & `config.yml`)](./Creating-Extensions/Configuration.md)**
    * Learn how to make your mod customizable by adding user-facing options (like switches and sliders) to the UCP GUI.

* **[Extension File Reference](./Creating-Extensions/Extension-File-Reference.md)**
    * **For reference.** A detailed breakdown of every optional file (`definition.yml`, `locale/`, etc.) that can be included in an extension.

* **[Framework Architecture](./Creating-Extensions/Framework-Architecture.md)**
    * For a deeper technical understanding of how the UCP injects itself into the game and manages the loading of all your custom extensions.