# AI Editing Tutorial for UCP3

UCP3 uses AI Swapper to assign personalities, castles, portraits, speech and other character components to the game's existing AI slots. This tutorial packages a personality first, then shows how to build it into a complete custom character. Start with [Creating a Plugin](../../Modding-with-UCP/Creating-Extensions/Creating-a-Plugin.md) for the plugin definition and installation folder.

## 1. Create a character directory

Place each character under your plugin's `resources/ai/` directory:

```text
My-AI-Pack-1.0.0/
├── definition.yml
├── locale/
│   └── description-en.md
└── resources/
    └── ai/
        └── My-Abbot/
            ├── meta.json
            └── character.json
```

`My-Abbot` identifies your provider; it does not have to be the name of the game slot. Players choose which slot receives its components through AI Swapper. A pack can supply several characters by adding more directories alongside it.

## 2. Describe the character in meta.json

Create this `meta.json` for the personality-only starting example:

```json
{
  "name": "My Abbot",
  "description": "An Abbot personality focused on infantry attacks.",
  "author": "YourName",
  "link": "",
  "version": "1.0.0",
  "defaultLang": "en",
  "supportedLang": ["en"],
  "switched": {
    "binks": false,
    "speech": false,
    "aic": true,
    "aiv": false,
    "lord": false,
    "startTroops": false,
    "lines": false,
    "portrait": false
  }
}
```

`switched` tells AI Swapper which components your character supplies. Set the corresponding entries to `true` as you add and test those files. The runtime requires this object; metadata containing only a name and author is incomplete.

## 3. Put the personality under character.json's aic key

The key is lowercase `aic`. This valid JSON example changes a few fields while leaving other personality values unchanged:

```json
{
  "aic": {
    "CriticalPopularity": 4500,
    "LowestPopularity": 6000,
    "HighestPopularity": 9000,
    "AttUnitMain1": "Monk"
  }
}
```

For a complete personality, start from an existing `character.json`, preserve the full set of fields, and edit them for your intended behaviour. The [Revised Abbot character](https://github.com/UnofficialCrusaderPatch/extension-ucp2-ai-files/blob/main/resources/ai/abbot_UCP_AIC/character.json) is a working example. See [AI Character Parameters](AI-Character-Parameters.md) and [AI Personality Explained](AI-Personality-Explained.md) for behaviour and constraints. In particular, each default/weak/strong group of defence, raid and attack recruitment probabilities must total 100.

### Converting a legacy AIC JSON file

An older file can contain several `AICharacters`, each with a `Name` and `Personality`. For each character you want to publish:

1. Create its own provider directory and `meta.json`.
2. Copy the contents of its `Personality` object into `character.json` under `aic`.
3. Move the description into the metadata and pack description as appropriate. The `AICharacters`, `Name`, `CustomName` and `Personality` wrapper is not the AI Swapper character format.
4. Select the converted personality through AI Swapper and check its behaviour in a match.

Renaming the old file to `character.json` does not convert its structure. Use valid JSON without comments or trailing commas.

## 4. Add lord and starting troop settings

The same `character.json` holds `lord` and `startTroops`. A file supplying all three components has this shape:

```json
{
  "lord": {
    "StrengthMultiplier": 1.0,
    "DotCount": 2,
    "DotColour": "Blue",
    "Type": "Europ"
  },
  "startTroops": {
    "normal": { "Monk": 6, "EuropArcher": 6 },
    "crusader": { "Monk": 24, "EuropArcher": 40 },
    "deathmatch": { "Monk": 6, "EuropArcher": 6 }
  },
  "aic": {
    "CriticalPopularity": 4500,
    "LowestPopularity": 6000,
    "HighestPopularity": 9000,
    "AttUnitMain1": "Monk"
  }
}
```

Enable `lord` and `startTroops` in `meta.json` when supplying those components. Keep unit names and game-mode keys exactly as the working examples use them. Test starting forces in each mode you support.

## 5. Add castles and their mapping

Place castle files and `mapping.json` under the character's `aiv/` directory. Paths in the mapping are relative to that directory. To use two designs across all eight castle choices:

```json
{
  "castle_1": "abbot-one.aiv",
  "castle_2": "abbot-two.aiv",
  "castle_3": "abbot-one.aiv",
  "castle_4": "abbot-two.aiv",
  "castle_5": "abbot-one.aiv",
  "castle_6": "abbot-two.aiv",
  "castle_7": "abbot-one.aiv",
  "castle_8": "abbot-two.aiv"
}
```

Enable `aiv` in the metadata. **An omitted or missing castle mapping disables that choice; it does not retain the original castle.** Map all the choices you intend the game to use and check that every referenced file exists.

Test the castle with its personality: the layout needs to support the planned economy, weapon production, recruitment, defence and siege behaviour.

## 6. Build the character's presentation

Give the character a consistent identity through portraits, messages, voices and Bink videos. The resource layout is:

```text
My-Abbot/
├── meta.json
├── character.json
├── portrait.png
├── portrait_small.png
├── lines.json
├── aiv/
│   ├── mapping.json
│   └── abbot-one.aiv
├── speech/
│   ├── mapping.json
│   └── message.wav
├── binks/
│   ├── mapping.json
│   └── message.bik
└── lang/
    └── de/
        ├── lines.json
        ├── speech/
        │   ├── mapping.json
        │   └── message.wav
        └── binks/
            ├── mapping.json
            └── message.bik
```

The tree shows where each resource type belongs, not a complete set of message files. Use an existing full character such as [Pilaw's Baer](https://github.com/CrusaderPilaw/extension-Legends-of-the-Orient-AI/tree/main/resources/ai/Baer) for the message names, mappings and portrait assets, replacing the content and credits with your own work.

- `portrait.png` and `portrait_small.png` supply the two portrait resources.
- `lines.json` contains the character's name, titles, description and message text.
- `speech/mapping.json` maps message keys to audio files relative to that directory.
- `binks/mapping.json` maps message keys to videos relative to that directory.
- `lang/<language>/` supplies translations of lines, speech and videos. AI Swapper checks that localized file first and falls back to the corresponding file at the character root when it is absent.

Keep `defaultLang`, `supportedLang` and the component switches in sync with the files you supply. Check each supported language in-game and credit the creators of reused assets.

## 7. Select and test the character

Activate the plugin, then select the supplied components in AI Swapper for the slot you want to replace. A provider being installed or enabled does not itself assign it to Abbot or another slot. AI Swapper can combine one provider's personality with another provider's castles or presentation.

Start a match with the selected AI. Check that its personality loads, that each mapped castle builds, that its economy continues operating, and that raids and sieges work. Test its portraits and messages, the supported languages and starting modes, and save/load. Record the active extensions, game version, map, castle set and starting resources when reporting results.

If the character is absent, check the plugin's folder name and definition, the `resources/ai/<character>/meta.json` path and `switched` entries. If it appears but its personality is unchanged, check the lowercase `aic` key, selection in AI Swapper, and the game logs.

To release a preset that selects your character for players, see [Configuration](../../Modding-with-UCP/Creating-Extensions/Configuration.md) and [Aggressive AI Behaviour Applied](https://github.com/Krarilotus/extension-Aggressive-AI-Behaviour-Applied). Keep the provider and preset's responsibilities clear in the pack description.
