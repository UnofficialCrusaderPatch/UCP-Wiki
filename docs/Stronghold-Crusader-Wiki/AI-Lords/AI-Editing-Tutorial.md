# AI Editing Tutorial (UCP3)

This guide will walk you through the process of creating a custom AI character for Stronghold Crusader using the modern UCP3 framework. Creating a new AI involves packaging it as a **Plugin Extension**.

## Prerequisites

This tutorial assumes you have a basic understanding of how to create a UCP3 Plugin. It is **highly recommended** to use the UCP3 GUI to create a blank plugin template first, rather than creating folders and files manually.

> **TODO:** Create and link to a `Creating-a-Plugin.md` tutorial page. For now, users should refer to the UCP3 GUI's functionality for creating new, empty plugins.

Once you have your empty plugin, you can begin adding your AI files to it.

---

## The AI Extension Structure

An AI character is defined as a collection of resources inside your plugin folder. The framework expects a specific folder structure within your plugin's `resources` directory:

`ucp/plugins/YourPlugin-1.0.0/resources/ai/<AI_LORD_NAME>/`

* **`<AI_LORD_NAME>`**: This should be the internal name of the AI you are replacing (e.g., `Rat`, `Snake`, `Wolf`, `Saladin`). All files for that AI go inside this folder.

Here is a complete view of what a fully custom AI folder might contain:

```
YourPlugin-1.0.0/
└── resources/
    └── ai/
        └── Wolf/
            ├── aiv/
            │   ├── Wolf_Castle_1.aiv
            │   ├── Wolf_Castle_2.aiv
            │   └── mapping.json
            ├── binks/
            │   ├── wolf_taunt.bik
            │   └── mapping.json
            ├── lang/
            │   ├── de/
            │   │   ├── speech/
            │   │   │   └── ... (German audio files)
            │   │   └── lines.json
            │   └── en/
            │       ├── speech/
            │       │   └── ... (English audio files)
            │       └── lines.json
            ├── portrait.png
            ├── portrait_small.png
            ├── character.json
            └── meta.json
```

Let's break down each component.

### `meta.json` (Required)
This file contains metadata about your AI.
```json
{
  "name": "Custom Wolf",
  "version": "1.0.0",
  "author": "YourName",
  "description": "A new version of the Wolf with a focus on siege."
}
```

### `character.json` (Required)
This is the heart of your AI's personality, replacing the old `.aic` files. It contains all the key-value pairs that define the AI's behavior.

For a full list of parameters and what they do, see these essential resources:
* [AI Character Parameters (AIC)](AI-Character-Parameters)
* [AI Personality Explained](AI-Personality-Explained)

```json
{
  "AIC": {
    "CriticalPopularity": 3000,
    "LowestPopularity": 5000,
    "AttUnitMain1": "Swordsman",
    "AttMaxEngineers": 16
    // ... all other AIC parameters
  }
}
```

### Portraits (Optional)
* `portrait.png`: The main portrait of the lord shown in the lobby.
* `portrait_small.png`: The small icon shown on the minimap.

### `aiv/` Folder (Optional)
This folder holds the AI's castle designs (`.aiv` files).

* `mapping.json`: This file is crucial. It maps the game's 8 castle slots to your specific `.aiv` filenames. This means you don't have to provide all 8 castles.
    ```json
    {
      "castle_1": "Wolf_Castle_1.aiv",
      "castle_3": "Wolf_Castle_2.aiv"
    }
    ```

### `binks/` Folder (Optional)
This folder contains custom video messages (`.bik` files) for taunts, requests, etc.
* `mapping.json`: Maps internal game message identifiers to your video files.
    > **TODO:** Add a reference link to a list of all message identifiers.

### Language and Dialogue
Dialogue is split between text (`lines.json`) and audio (`speech/`). You can provide translations and localized audio by creating subfolders in `lang/`.

#### `lang/en/lines.json` (Optional)
This file contains the text displayed for the AI's messages in English.
> **TODO:** Add a reference link to a list of all message identifiers and their format.

#### `lang/en/speech/` (Optional)
This folder holds the `.wav` audio files for the AI's dialogue in English.
* `mapping.json`: Maps internal game message identifiers to your audio files.

---

## Advanced: The AI Swapper Extension

The UCP framework includes a powerful built-in extension called the **AI Swapper**. This tool allows you to mix and match components from different AI characters, even from different AI plugins.

For example, you could take:
* The **castles** from your custom Wolf AI.
* The **personality** (`character.json`) from the vanilla Rat.
* The **dialogue and portrait** from the vanilla Saladin.

And combine them to replace the Pig in the game.

![Image placeholder for AI Swapper GUI](https://raw.githubusercontent.com/UnofficialCrusaderPatch/UCP-Wiki/main/docs/images/ai-swapper-placeholder.png)
*(Image showing the AI Swapper interface in the UCP GUI)*

This provides incredible flexibility for creating unique opponents without having to create every single asset from scratch. To use it, simply enable the AI Swapper extension in the UCP GUI and configure your desired swaps in its options panel.