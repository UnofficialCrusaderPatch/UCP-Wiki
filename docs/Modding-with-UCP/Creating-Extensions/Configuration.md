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

This file defines a slider, a switch, and a choice dropdown.

```yaml
# options.yml
meta:
  version: 1.0.0
options:
  - url: myModule.features.exampleSlider
    text: "Example Slider"
    tooltip: "Controls the intensity of the feature."
    display: Slider
    contents:
      type: number
      min: 0
      max: 100
      step: 5
      value: 50 # Default value

  - url: myModule.features.enableSwitch
    text: "Enable Feature"
    tooltip: "Toggles the entire feature on or off."
    display: Switch
    contents:
      type: boolean
      value: true # Default value

  - url: myModule.behavior.difficulty
    text: "AI Difficulty"
    tooltip: "Select the AI's combat difficulty."
    display: Choice
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

* `required-value`: This is a hard requirement. If two active extensions have conflicting `required-value` demands for the same option, the GUI reports a conflict.
* `suggested-value`: This acts as a new default value. It can be overridden by other suggestions higher in the load order or by any `required-` demand.

### Example `config.yml`

Imagine a plugin "MyBalancePack" that depends on "myModule" from the example above. It suggests a default value of 90 for the slider and forces the difficulty to `hard`.

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
          exampleSlider:
            contents:
              suggested-value: 90
        behavior:
          difficulty:
            contents:
              required-value: "hard" # Force the difficulty to 'hard'
```

## The Final Configuration

The UCP backend processes the `options.yml` from all modules and then applies the `config.yml` demands from all active extensions in their specified load order. This resolves all requirements and suggestions into a single, final configuration that is passed to the game. The GUI is responsible for detecting and reporting any conflicts to the user before they launch the game.