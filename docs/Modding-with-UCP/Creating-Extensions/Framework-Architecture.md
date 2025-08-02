# Framework Architecture

The UCP framework modifies Stronghold Crusader by intercepting the game's launch process. Here's a high-level overview of how it works, from launch to gameplay.

## 1. Hijacking the Game Launch

When you run `Stronghold Crusader.exe`, the game process loads all of its required Dynamic Link Libraries (DLLs) into memory. One of these is `binkw32.dll`, used for playing Bink video files.

The UCP replaces the original `binkw32.dll` with its own version. This custom DLL acts as a loader:
1.  **Injects Code:** It first injects the core UCP code (`ucp.dll`) into the game's main process.
2.  **Loads Original DLL:** It then renames the original game DLL to `binkw32_real.dll` and loads it, passing through all legitimate game calls to it. This ensures that in-game videos still work correctly.

The injected code from `ucp.dll` runs *before* the main game code, allowing the framework to initialize itself.

## 2. Initializing the Framework

The `ucp.dll` is the heart of the framework. It relies on two key components:
* **RPS.dll ([Runtime Patching System](https://github.com/gynt/RuntimePatchingSystem)):** A powerful library for applying patches and modifying executable code in memory at runtime.
* **lua.dll:** A Lua interpreter that allows extensions to script game behavior.

During initialization, `ucp.dll` sets up the patching environment and the Lua state. At the end of this process, it executes `main.lua`, a bootstrap script that manages user configurations and loads all active extensions.

## 3. Loading Extensions

After the framework is initialized, `main.lua` takes over and begins loading the extensions you've enabled in the UCP GUI. Extensions are loaded in a specific order and come in two types: **Modules** and **Plugins**.

For a detailed breakdown of what extensions are and how they're structured, see the [Extensions Overview](Extensions-Overview.md) page.

## 4. Handing Control Back to the Game

Once all extensions are loaded and their configurations are applied, the framework hands execution control back to the game.

* The game proceeds to its loading screen.
* Just before the main game loop begins (where events and game ticks are processed), control is briefly given back to a UCP Lua script. This script executes final setup callbacks registered by modules (e.g., applying custom AI Characters or modifying UI elements that have just been created).
* Finally, execution is returned to the game, which now runs with all UCP modifications, hooks, and detours active.