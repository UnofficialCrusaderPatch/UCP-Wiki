[Back to Creating Extensions](../Creating-Extensions.md)

# Configuration with options.yml and config.yml

An extension's `options.yml` exposes settings in the launcher. A plugin's `config.yml` can suggest or require values for settings supplied by its dependencies. These are different from an AI's `meta.json` and `character.json`, which describe its content.

## Expose settings in options.yml

The file has a `meta` object and an `options` array. An option's `url` identifies its place in the configuration. Use the display element names supported by the launcher; for example, a boolean switch uses `UCP2Switch`:

```yaml
meta:
  version: 1.0.0
options:
  - name: enable-feature
    category: [My Module]
    header: Enable feature
    text: Enable this module's feature.
    display: UCP2Switch
    url: myModule.enable-feature
    contents:
      type: boolean
      value: true
```

For translated labels, use placeholders such as `'{{enable-feature}}'` and define their strings in `locale/en.yml`. See [Map Loader's options](https://github.com/UnofficialCrusaderPatch/extension-maploader/blob/main/options.yml) for working switches, and use a current module with the same control type as a reference before introducing sliders or choices.

## Suggest or require values in config.yml

A sparse configuration wraps demands in `config-sparse`. Module settings go under `modules.<module-name>.config`. For the switch above:

```yaml
meta:
  version: 1.0.0
config-sparse:
  modules:
    myModule:
      config:
        enable-feature:
          contents:
            suggested-value: true
  plugins: {}
```

A `suggested-value` supplies a value that can be overridden. A `required-value` makes that value a requirement. Numeric constraints can also use `required-min` and `required-max` where the option supports them. The launcher resolves the active extensions' demands and reports conflicts; apply order and the other active configurations matter.

Declare every extension your preset needs in `definition.yml`. Exporting the intended setup through the launcher's **Create plugin** action in Creator mode is a useful starting point. Review the output because it captures the current configuration and dependencies, not just the setting you last changed.

## Apply an AI pack as a preset

Installing a content pack makes its characters available in AI Swapper. To select a personality automatically, a separate preset can depend on that pack and configure AI Swapper's menu.

For the `My-AI-Pack` example in [Creating a Plugin](Creating-a-Plugin.md), an applied preset's `config.yml` can contain:

```yaml
meta:
  version: 1.0.0
config-sparse:
  modules:
    aiSwapper:
      config:
        menu:
          contents:
            suggested-value:
              abbot:
                - name: My Abbot
                  root: ucp/plugins/My-AI-Pack/resources/ai/My-Abbot/
                  control:
                    aic: true
  plugins: {}
```

The `root` uses UCP's version-independent plugin path alias. It must identify the provider directory containing `meta.json`. `control` selects the components this preset applies; the example selects only the personality. Add the other supplied components when building your full preset.

The preset needs dependencies on `My-AI-Pack` and `aiSwapper`, as well as the compatible framework and frontend. Use [Aggressive AI Behaviour Applied](https://github.com/Krarilotus/extension-Aggressive-AI-Behaviour-Applied) for a complete working definition and configuration. Test the resolved configuration in the launcher and verify the selected components in a match.

## Related guides

- [AI Editing Tutorial](../../Stronghold-Crusader-Wiki/AI-Lords/AI-Editing-Tutorial.md): build the character resources.
- [Extension File Reference](Extension-File-Reference.md): files used by a plugin.
