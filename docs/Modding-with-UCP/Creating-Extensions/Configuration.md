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
# options.yml - An array of UI elements
- name: Example Slider
  url: myModule.features.exampleSlider
  description: "Controls the intensity of the feature."
  display: slider
  contents:
    type: number
    min: 0
    max: 100
    step: 5
    value: 50 # Default value

- name: Enable Feature
  url: myModule.features.enableSwitch
  description: "Toggles the entire feature on or off."
  display: switch
  contents:
    type: boolean
    value: true # Default value

- name: AI Difficulty
  url: myModule.behavior.difficulty
  description: "Select the AI's combat difficulty."
  display: choice
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

* `required-*`: This is a hard requirement. If two active extensions have conflicting `required-` demands for the same option, the UCP will throw an error.
* `suggested-*`: This acts as a new default value. It can be overridden by other suggestions higher in the load order or by any `required-` demand.

### Example `config.yml`

Imagine a plugin "MyBalancePack" that depends on "myModule" from the example above. It wants to force the slider to be between 80 and 100, and suggests a default value of 90.

```yaml
# config.yml for MyBalancePack
# This file specifies demands on other extensions.

modules:
  myModule: # Name of the module this config applies to
    features:
      exampleSlider:
        contents:
          required-min: 80
          required-max: 100
          suggested-value: 90
    behavior:
      difficulty:
        contents:
          required-value: "hard" # Force the difficulty to 'hard'
```

## The Final Configuration

The UCP backend processes the `options.yml` from all modules and then applies the `config.yml` demands from all active extensions in their specified load order. This resolves all requirements and suggestions into a single, final configuration that is passed to the game. The GUI is responsible for detecting and reporting any conflicts to the user before they launch the game.