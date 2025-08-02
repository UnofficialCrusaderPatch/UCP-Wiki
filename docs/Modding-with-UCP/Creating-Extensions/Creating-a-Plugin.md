# Creating a Plugin

Plugins are the primary way to add new content to Stronghold Crusader with UCP. This guide will walk you through the creation of a basic plugin.

## Step 1: Use the GUI to Create a Template

**Do not create plugin folders manually.** This can lead to errors. The UCP GUI has a built-in tool to create a perfectly structured empty plugin for you.

> **TODO:** Add a screenshot of the "Create New Plugin" button in the GUI's Content tab.

1.  Navigate to the **Content** tab in the UCP GUI.
2.  Click the "Create New Plugin" button.
3.  Fill in the details:
    * **Name:** A human-readable name for your plugin (e.g., "My Awesome Map Pack").
    * **Version:** Start with `1.0.0`.
    * **Author:** Your name.
4.  Click "Create". The GUI will generate a new folder in `ucp/plugins/` with the correct structure, including a `definition.yml` file.

## Step 2: Understand the `definition.yml`

Open the newly created `definition.yml` file in a text editor. This file is the identity card of your plugin.

```yaml
name: "My Awesome Map Pack"
version: "1.0.0"
author: "YourName"
description: "A collection of symmetrical maps for multiplayer."
# If your plugin relies on another extension (e.g., the AI Swapper),
# you would list it as a dependency here.
dependencies:
  - name: "AI Swapper"
    version: ">=1.0.0"
```

## Step 3: Add Your Content to the `resources` Folder

All game content (maps, AI, etc.) must go inside the `resources` subfolder of your plugin. The UCP framework uses this folder to virtually overlay your files onto the game.

* **For Custom Maps:** Place your `.map` files in `resources/maps/`.
* **For Custom AI:** Follow the structure outlined in the [AI Editing Tutorial](../AI-Lords/AI-Editing-Tutorial). Place your AI folders in `resources/ai/`.

## Step 4: Adding User Options (Optional)

If you want users to be able to configure your plugin, you can create an `options.yml` file. See the [Configuration](Configuration) guide for details.

## Step 5: Activate and Test

Go back to the UCP GUI's **Content** tab. Your new plugin will appear in the "Inactive Extensions" list. Drag it to the "Active Extensions" list, launch the game, and test if your new content appears correctly.