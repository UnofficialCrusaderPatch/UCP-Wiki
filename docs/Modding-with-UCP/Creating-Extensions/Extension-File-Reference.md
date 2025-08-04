# Extension File Reference

This page provides a detailed breakdown of the common file structure used by all UCP extensions.

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
    * +++lua
    return {
      enable = function(self, config)
        -- Your setup code goes here
      end,
      disable = function(self, config)
        -- Your cleanup code goes here
      end,
    }
    +++