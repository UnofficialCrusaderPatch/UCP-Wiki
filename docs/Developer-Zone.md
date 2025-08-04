[< Back to Home](../Home.md)

# Contributor Tutorial: Creating a Module

This guide is for advanced users and developers who want to contribute new features or code changes to the UCP framework. Unlike Plugins, which primarily handle content, **Modules** are extensions that can directly modify the game's code at runtime.

## The Goal: A Code-Modifying Module

The core of UCP3's power comes from its ability to patch the game's memory. As a contributor, your goal is to create a self-contained Module that:
1.  Identifies a specific piece of game code.
2.  Patches it to change behavior or add new functionality.
3.  Exposes any new options to the user via the UCP GUI.

## 1. The Module Structure

A Module is a zipped extension that lives in the `ucp/modules/` folder. Its structure is similar to a plugin, but its purpose is different.

* `definition.yml`: Defines the module's name, version, and dependencies.
* `options.yml`: **Crucial for modules.** This is how you expose toggles, sliders, and other controls for your new feature to the user.
* `init.lua`: The entry point for your code. This Lua script will execute the patches.
* (Optional) `*.dll`: For complex, high-performance features, you can include a compiled DLL and call its functions from your `init.lua` script.

## 2. The `init.lua` Entry Point

All module logic starts here. Your script must return a table containing an `enable` function. This function is called by the framework at startup.

```lua
-- init.lua
return {
    -- The 'config' parameter contains the final, resolved values
    -- for all options defined in your options.yml
    enable = function(self, config)
        -- Your patching logic goes here
        print("My Custom Module has been enabled!")

        if config.myModule.myFeature.enabled then
            -- Apply the patch only if the user enabled it in the GUI
            apply_feature_patch()
        end
    end,

    disable = function(self, config)
        -- Logic to undo patches (if necessary)
    end,
}
```

## 3. Patching Game Code with Lua

The UCP framework exposes powerful functions to your Lua script for finding and modifying game code. The core concept is **AOB Scanning** (Array of Bytes). Instead of relying on fragile memory addresses, you define a unique sequence of bytes to locate the code you want to change.

> **Note:** This is a conceptual example. The exact function names and parameters are documented within the framework's core Lua files.

```lua
local ucp = require("ucp.internal")

-- This function will apply our patch
function apply_feature_patch()
    -- 1. Define the unique byte signature to find
    local signature = "8B 4D 08 83 C1 04 51" -- Example signature

    -- 2. Find the address of this signature in the game's memory
    local address = ucp.aob_scan(signature)

    if address then
        -- 3. If found, write new bytes to modify the code.
        -- Here, we replace the original code with NOP (No-Operation) instructions,
        -- effectively disabling it.
        ucp.patch(address, "90 90 90 90 90")
        print("Feature patch applied successfully at address: " .. address)
    else
        print("ERROR: Could not find signature for feature patch!")
    end
end
```

## 4. Exposing Options with `options.yml`

To allow users to control your new feature, you must define it in `options.yml`.

```yaml
# options.yml
- name: My Awesome New Feature
  url: myModule.myFeature.enabled
  description: "Check this box to enable the new gameplay mechanic."
  display: switch
  contents:
    type: boolean
    value: true # Default value is 'on'
```

The framework will read this file and display a switch in the GUI. The final value chosen by the user will be passed into your `init.lua` script inside the `config` table, which you can check as shown in the Lua example above.

## Getting Started

1.  **Get the Developer Build:** Download the "Developer" version of UCP3, which disables security checks for loading unsigned modules.
2.  **Explore Existing Modules:** The best way to learn is to unzip and examine the code of existing UCP modules.
3.  **Join the Discord:** The UCP Discord server is the best place to ask questions and get help from experienced developers.