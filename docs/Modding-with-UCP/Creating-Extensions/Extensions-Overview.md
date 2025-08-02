# Extensions Overview

Extensions are the core of UCP's modularity. They are "plug-and-play" components that can customize, expand, or completely overhaul the game. They live in the `ucp/` folder and are categorized into two types: **Plugins** and **Modules**.

## Common File Structure

All extensions share a common file structure and can contain the following files:

* `/definition.yml` **(Required)**
    * Defines the extension's metadata: its unique name, version, author, and dependencies on other extensions.

* `/options.yml` (Optional)
    * Defines configuration options that will be displayed to the user in the UCP GUI, such as toggles, sliders, or dropdowns. You must specify UI display information and default values here.

* `/config.yml` (Optional)
    * Specifies configuration *demands* placed on other extensions (dependencies). For example, a balance mod can require a specific setting from a core UCP module.

* `/locale/en.yml` (Optional)
    * Contains localization strings for translating your extension's UI options for different languages.

* `/locale/description-en.md` (Optional)
    * A Markdown file containing a rich description of your extension, displayed when a user selects it in the GUI.

* `/init.lua` (Optional)
    * The entry point for any scripted logic. If present, it must return a table with `enable` and `disable` functions. The `enable` function is called when the framework starts up.
    ```lua
    return {
      enable = function(self, config)
        -- Your setup code goes here
      end,
      disable = function(self, config)
        -- Your cleanup code goes here
      end,
    }
    ```

## Plugins

Plugins are extensions that primarily add or modify **game content**.
* **Content:** They can contain new game resources like AI files (`.aiv`, `character.json`), maps, graphics, or sound effects. These files must be placed in a `/resources/` subfolder.
* **Safety:** Plugins cannot directly modify game code. They can only interact with the game by calling Lua functions explicitly exposed by the framework or by modules.
* **Format:** Plugins are stored as regular folders (e.g., `ucp/plugins/MyMapPack-1.0.0/`).

## Modules

Modules are powerful extensions that can **modify game code**.
* **Permissions:** Modules have special permissions to directly patch the game's executable memory using the Runtime Patching System. They have access to core framework functions for creating hooks and detours.
* **Custom Code:** Modules can include compiled DLL files (`.dll`) for high-performance code. The `init.lua` script is responsible for loading the DLL and linking its functions to the game via the Lua state.
* **Security:** Because they can execute arbitrary code, modules must be cryptographically signed. The framework will only load modules that are trusted. For development, you can use the Developer Build of UCP to bypass this signature check.
* **Format:** Modules are distributed as zipped archives (e.g., `ucp/modules/MyGameplayMod-0.0.1.zip`).