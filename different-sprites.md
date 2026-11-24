---
title: "Using Different Sprites"
layout: default
nav_order: 2
parent: "Customization"
---

# Using Different Sprites

The following steps describe how to use different sets of sprites:

1.  In the **Assets/TobiFroi/InputIcons folder** are 2 types of Scriptable Objects that store the sprites used by the tool: one for keyboard sprites (InputIconSetKeyboardSO) and one for gamepad sprites (InputIconSetGamepadSO).

2.  To use a different set of sprites, we can duplicate an IconSet and assign our desired sprites to the new Scriptable Object. One efficient way to do this is to drag the Scriptable Object into a folder containing our sprites and then click on “Automatically apply button sprites of folder” in the inspector of the Scriptable Object. This will try to assign as many sprites as possible (the success of this process depends on the names of the sprites). Pressed sprites (named “…\_pressed” or in a “Pressed” folder) are ignored here, use “Automatically apply pressed sprites of folder…” for them.

3.  To create a new style of an existing icon set (e.g. the same keys in a different color), duplicate the icon set, move the copy into the folder with the new sprites and click “Match sprites of template in this folder”. Every entry gets the matching sprite of the folder, with the same assignments as before: entries without a sprite stay empty, custom context icons are included and pressed sprites are only assigned where the original has one. Sprites are matched by name, e.g. “Mouse_Middle_Key_Dark” becomes “Mouse_Middle_Key_Azure”. Optionally, choose another icon set as the template.

4.  Once we have our Icon Sets ready, we can choose them on the “Your Look” page of the setup wizard and run the setup, or assign them on the configurator and use “Re-create sprite assets” on the Project Status page.

5.  Sometimes, we may need to enter play mode or recompile the code for the new icons to be displayed.

<img src="/input-icons-documentation/assets/images/guide/different-sprites-1.png" alt="Screenshot" width="278">

 

<img src="/input-icons-documentation/assets/images/guide/different-sprites-2.png" alt="Screenshot" width="236">

