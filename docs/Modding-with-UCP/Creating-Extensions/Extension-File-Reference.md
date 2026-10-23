# Extension File Reference

These paths are relative to the extension's root. See [Creating a Plugin](Creating-a-Plugin.md) for a complete starting example.

## definition.yml

Defines the internal name, display name, version, author, extension type, dependencies and metadata format version. The installed directory or ZIP name uses `<name>-<version>`. Dependencies can be written as a mapping from internal extension names to version ranges.

## resources/

Contains the content your plugin provides. The responsible module determines how it is loaded; this is not a general instruction to overwrite files in the game installation.

AI Swapper discovers character providers under `resources/ai/<character>/`. Each has a `meta.json` identifying its components. `character.json` supplies `aic`, `lord` and `startTroops`; castles and presentation assets have their own files and mappings. Follow the [AI Editing Tutorial](../../Stronghold-Crusader-Wiki/AI-Lords/AI-Editing-Tutorial.md) for their exact layout.

## config.yml

Suggests or requires settings from dependency modules and plugins. A content provider can leave selection to the player; an applied preset uses configuration to select a setup. See [Configuration](Configuration.md) for the `config-sparse` structure and an AI Swapper example.

## options.yml

Defines settings exposed by the extension in the launcher. The file includes `meta` and an `options` list, with supported display controls, URLs and default values. See [Configuration](Configuration.md).

## locale/en.yml

Contains translated labels and descriptions referenced by `{{placeholders}}` in the extension's UI definitions. Other languages use their language code as the filename.

## locale/description-en.md

Contains the pack's Markdown description shown in the launcher and Store. Include the intended gameplay, content, activation instructions, supported setup, screenshots and credits. Other languages use `description-<language>.md`. The directory is named `locale`, not `locales`.

## init.lua

Provides scripted behaviour through the extension lifecycle. Content packs that are already handled by existing modules do not need a private loader. Reuse the relevant module's exported API when scripting is needed; game-code changes belong in a module. See [Creating Extensions](../Creating-Extensions.md) and [Framework Architecture](Framework-Architecture.md).
