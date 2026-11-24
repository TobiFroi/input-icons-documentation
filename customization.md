---
title: Customization
layout: default
nav_order: 7
---

# Customization

Input Icons provides several ways to customize how bindings are displayed in your game.

## Using Different Sprites

To use your own custom sprites:

1. Locate the Scriptable Objects in the Assets/InputIcons folder:
   - `InputIconSetKeyboardSO` for keyboard sprites
   - `InputIconSetGamepadSO` for gamepad sprites

2. Duplicate an existing IconSet and customize it:
   - Create a new folder for your custom sprites
   - Drag the Scriptable Object into your folder
   - Click "Automatically apply button sprites of folder" in the inspector
   - The tool will try to automatically assign sprites based on their names

3. For "Custom Context" sprites, apply them manually as they cannot be assigned automatically

4. Once your Icon Sets are ready:
   - Drag them into the Customization area of the Setup Window
   - Hit the "(Re-)Create Sprite Assets" button
   - You may need to enter play mode or recompile for the new icons to appear

![Custom Icon Sets](/input-icons-documentation/assets/images/custom-icon-sets.png)

## Adding Custom Context Sprites

To add support for additional input controls:

1. Find the input binding string:
   - Add the script `II_UITextDisplayAllActions` to a TextMeshProUGUI object
   - Use a rebind button to override a binding with your new desired binding
   - The input binding string will be displayed in brackets (e.g., "Scroll" for mousewheel)

2. Add the binding to your Icon Set:
   - Open your Icon Set Scriptable Object
   - Add a new entry to the Custom Contexts list
   - Enter the binding string and assign your sprite

{: .warning }
After making changes to an Input Icon Set, you must create a new Sprite Asset or your changes won't be reflected in TextMeshPro texts.

## Performance Options

To improve performance when switching devices:

1. Open the Input Icons Manager
2. Change the Text Update Method to "Via Input Icons Text Components"
3. Make sure required text objects have an InputIconsText component attached

This avoids searching the entire scene for text objects when devices change.

## Display Settings

The InputIconsManager provides various display options:

| Setting | Description |
|---------|-------------|
| Show All Available Input Option | Toggle between showing only the first binding or all available bindings |
| Multiple Input Delimiter | Define what appears between multiple bindings (e.g., " <size=80%>or</size> ") |
| Opening/Closing Tags | Add general styling for all displayed icons (e.g., size adjustments) |
| Display Type | Choose between sprites, text, or text in brackets |
| Text Display For Unbound Actions | Text to show for unbound actions |
| Text Display Language | Display in English or System Language |
| Action name output overrides | Override displayed text for specific actions (e.g., [MOUSE] instead of [POSITION]) |

![Display Settings](/input-icons-documentation/assets/images/display-settings.png)