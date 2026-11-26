[< Back to Creating Extensions](../Creating-Extensions.md)

# Configuration (`options.yml` & `config.yml`)

The UCP's configuration system allows for incredible flexibility. Module creators can expose options to users, and plugin creators can then combine and configure these modules to create unique gameplay experiences. This system revolves around two key files: `options.yml` and `config.yml`.

## The URL System

Every configurable option is identified by a unique "URL" or key. This is a dot-separated string that creates a structured hierarchy, like `moduleName.feature.option`. This ensures that every setting has a unique identifier and keeps configuration files organized.

**Example:** An option for AI wood purchasing might have the URL `AIImprovements.economy.woodPurchaseAmount`.

---

## `options.yml`: Providing Options to Users

An extension can include an `options.yml` file to define settings that end-users can change in the UCP GUI. Modules should use this to expose their features, allowing for maximum customization.

* **Goal:** Make your module unopinionated. Provide toggles, sliders, and choices to let users tailor the experience.
* **Defaults:** The default values in `options.yml` should, whenever possible, replicate the vanilla game's behavior.

### Example `options.yml`

This file defines a number field, a switch, and a choice dropdown.

```yaml
# options.yml
meta:
  version: 1.0.0
options:
  - url: myModule.features.exampleAmount
    display: Number
    text: "Amount"
    contents:
      type: number
      min: 0
      max: 100
      value: 50 # Default value

  - url: myModule.features.enableSwitch
    display: Switch
    text: "Enable Feature"
    contents:
      type: boolean
      value: false # Default value

  - url: myModule.behavior.difficulty
    display: Choice
    text: "AI Difficulty"
    contents:
      type: choice
      choices:
        - name: easy
          text: "Easy Peasy"
        - name: normal
          text: "Normal"
        - name: hard
          text: "Nightmare"
      value: normal # Default value
```

---

## `config.yml`: Demanding Configurations

An extension can also include a `config.yml` file to **demand** specific settings from its dependencies. This is how a "total conversion" plugin can ensure all the modules it relies on are configured correctly.

* **Goal:** Create a specific, curated experience. An "Ultimate AI Pack" plugin would use `config.yml` to set the health of units, the aggression of AI, and other parameters from different modules.

### Required vs. Suggested

To provide flexibility, demands can be either **required** or **suggested**.

* `required-value`: Locks the option to a fixed value (including `false`) after user preferences are applied. If two active extensions set conflicting `required-value` locks on the same option, the GUI reports a conflict.
* `suggested-value`: Sets a new default value that the user can still override unless a `required-value` lock applies.
* Set a number field's `min` and `max` in the `options.yml` that defines the field; another extension's `config.yml` cannot change them.

### Example `config.yml`

Imagine a plugin "MyBalancePack" that depends on "myModule" from the example above. It suggests an amount of 90 and locks the difficulty to `"hard"`.

```yaml
# config.yml for MyBalancePack
# This file specifies demands on other extensions.
meta:
  version: 1.0.0
config-sparse:
  modules:
    myModule: # Name of the module this config applies to
      config:
        features:
          exampleAmount:
            contents:
              suggested-value: 90
        behavior:
          difficulty:
            contents:
              required-value: "hard" # Lock the difficulty to 'hard'
  plugins: {}
```

## The Final Configuration

The UCP launcher resolves `options.yml` defaults, user preferences, and `config.yml` demands from all active extensions, reports any conflicts before launch, and writes the resulting `config-full`. At game launch, the framework reads `config-full` and passes each extension its settings.