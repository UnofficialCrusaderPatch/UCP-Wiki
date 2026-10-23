# Creating a Plugin

A plugin packages content and settings for UCP3. This guide creates a plugin the launcher can discover and explains how its content reaches the game. See [Creating Extensions](../Creating-Extensions.md) for the distinction between plugins and code-modifying modules.

## 1. Choose what your plugin provides

An **AI content pack** provides characters players select through AI Swapper. An **applied preset** selects content and settings through `config.yml`. A **map pack** provides maps through Map Loader.

Adding files to a plugin does not automatically select an AI or replace every matching game file. Use the module responsible for that content. See the [AI Editing Tutorial](../../Stronghold-Crusader-Wiki/AI-Lords/AI-Editing-Tutorial.md) for a complete AI example, and [Map Loader](https://github.com/UnofficialCrusaderPatch/extension-maploader) for maps.

## 2. Create the plugin folder and definition

In the game installation selected by the launcher, create:

```text
ucp/plugins/My-AI-Pack-1.0.0/
```

Place `definition.yml` directly inside it. The folder name must match the definition's `name` and `version`. Use a short internal name without spaces, and a separate `display-name` for the title players see.

For an AI pack using AI Swapper:

```yaml
name: My-AI-Pack
display-name: My AI Pack
author: YourName
version: 1.0.0
type: plugin
dependencies:
  framework: ^3.0.0
  frontend: ^1.0.0
  aiSwapper: ^1.1.0
meta:
  version: 1.0.0
```

Dependencies are a mapping from the actual extension name to a compatible version range. The module is named `aiSwapper`, even when the launcher displays a friendlier title. Declare the dependencies your plugin uses and test those versions.

### Exporting settings from the launcher

For a configuration preset, the configuration editor offers **Create plugin** in Creator mode. It exports the current settings and active dependencies as `definition.yml` and `config.yml`. It does not build AI resource folders or copy resources from other installed plugins. Review the exported dependencies and settings so the preset contains the setup you intend to distribute.

## 3. Add your content

An AI plugin can have this layout:

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

`meta.json` tells AI Swapper which parts the character supplies. `character.json` contains the personality under a lowercase `aic` key, along with lord and starting troop settings when supplied. Continue with the [AI Editing Tutorial](../../Stronghold-Crusader-Wiki/AI-Lords/AI-Editing-Tutorial.md) for working examples, castle mappings, portraits, speech and dialogue.

Keep each character in its own directory. A legacy JSON file containing `AICharacters` and `Personality` needs conversion; putting it in `resources/ai/` or renaming it is not enough.

## 4. Describe the pack

Create `locale/description-en.md` at the plugin root. Explain the intended gameplay, what content the pack provides, how to select it, which setups you tested, and who created its assets. Add gameplay screenshots so players can see the result. Other languages use the same naming pattern, such as `description-de.md`.

For example:

```markdown
# My AI Pack

An Abbot personality focused on sustained infantry attacks.

Enable this plugin, open AI Swapper, and select My Abbot's personality
for the Abbot slot. Use the castle set listed below for the tested setup.

## Tested setup

List the game, framework, extensions, castle set and match settings here.

## Credits

List the creators of the personalities, castles, artwork and audio here.
```

Use hosted image URLs for screenshots that must also appear in the website's Content browser. Check the description in both the launcher and website before submission.

## 5. Activate and check the result

1. Reload the game folder in the launcher so it discovers the new plugin.
2. Activate it in **Content** and resolve any dependency or configuration errors.
3. For AI content, select the supplied components for an existing AI slot in AI Swapper. Enabling a content provider alone does not apply all its characters.
4. Apply the configuration, launch a match, and check that the selected content appears. Inspect the launcher/game logs if the AI is absent or values are not applied.
5. Test the intended gameplay and supported game setups. Record the castle set, active extensions and starting settings so others can reproduce the result.

To make a preset that applies your characters automatically, follow [Configuration](Configuration.md) and use an existing applied AI pack as a reference.

## 6. Share a reviewable release

Keep the source files in the repository, include installation instructions and credits, and give each release a version. If distributing a plugin ZIP, `definition.yml` must be at the archive root rather than inside an extra wrapper directory. Check it in a separate game installation before asking the UCP team to review it for the Store. Technical loading and gameplay quality are separate parts of that review.

## Working examples

- [Legends of the Orient AI](https://github.com/CrusaderPilaw/extension-Legends-of-the-Orient-AI): full AI characters with castles and presentation assets.
- [Revised AI Files](https://github.com/UnofficialCrusaderPatch/extension-ucp2-ai-files): separate providers for personalities and castles.
- [Aggressive AI Behaviour Applied](https://github.com/Krarilotus/extension-Aggressive-AI-Behaviour-Applied): a preset selecting components from another pack.
- [Extension File Reference](Extension-File-Reference.md): the role of files at the plugin root.
