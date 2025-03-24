---
title: Using Different Sprites
layout: default
parent: Customization
nav_order: 1
---

# Using Different Sprites

The following steps describe how to use different sets of sprites:

1. In the `Assets/InputIcons` folder, there are two types of Scriptable Objects that store the sprites used by the tool: one for keyboard sprites (`InputIconSetKeyboardSO`) and one for gamepad sprites (`InputIconSetGamepadSO`).
2. To use a different set of sprites, duplicate an Icon Set and assign your desired sprites to the new Scriptable Object. You can drag the Scriptable Object into a folder containing your sprites and then click **"Automatically apply button sprites of folder"** in the inspector of the Scriptable Object. This will attempt to assign as many sprites as possible based on their names.
3. "Custom Context" sprites must be assigned manually as they cannot be assigned automatically.
4. Once your Icon Sets are ready, drag them into the **Customization** area of the **Setup Window** and click **"(Re-)Create Sprite Assets"**.
5. You may need to enter **Play Mode** or **recompile the code** for the new icons to appear.
