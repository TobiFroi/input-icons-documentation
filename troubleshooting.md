---
title: "Troubleshooting"
layout: default
nav_order: 10
has_children: true
---

# Troubleshooting

**Compile errors on import**

- In an empty project with TMPro and the new Input System installed, you should not face compile errors. If you do however, please contact me as there might be some issues I don’t know of in specific Unity versions.

- **Steamworks / InputIconsSteamworksExtensionSO / InputIconsFacepunchSteamworksExtensionSO**: If you get a compile error stating that the type or namespace name ‘Steamworks’ could not be found, then you probably have STEAMWORKS_NET in your Scripting Define Symbols in the Project Settings and are using some type of plugin to make calls to the Steam API. For Input Icons I used the open source framework Steamworks.NET (<https://github.com/rlabrecque/Steamworks.NET/releases>), and if you don’t have that package in your project (while having STEAMWORKS_NET in your Scripting Define Symbols), you might face the above mentioned compile error(s). Adding that package should fix the problems. Similar for Facepunch Steamworks (<https://wiki.facepunch.com/steamworks/>). When using Facepunch Steamworks, make sure you have FACEPUNCH_STEAMWORKS added to your Scripting Defining Symbols. If you experience compile errors anyways, check the Assembly Definition called "**InputIcons**" in the "**Assets/TobiFroi/InputIcons/Scripts/Runtime/**" folder. **[com.rlabrecque.steamworks.net](http://com.rlabrecque.steamworks.net)** should be added to the Assembly Definition References. **If you want to use a different framework** and not Steamworks.NET or Facepunch Steamworks, you might have to add some custom code for Steam games. The **InputIconsSteamworksExtensionSO and InputIconsFacepunchSteamworksExtensionSO** tell Input Icons the real controller type of each gamepad through **InputIconSetConfiguratorSO.deviceTypeResolver**. You can register your own resolver there, using the framework of your choice.

Most other problems appear from an incorrect setup. Remember, whenever you make changes to an Input Action Asset, to also update the style sheet (Project Status page of the setup wizard, or the classic setup window). The Project Status page also finds many other setup issues.

Also make sure, the control scheme names in the setup window match the control scheme names in your Input Action Assets (sometimes an empty space slips in at the end of a string, it can happen to everyone)

If you have updated to a new version of Input Icons and your active Input Icons Manager is still the one inside the Input Icons folder, its values might have changed to the default ones. Run the setup wizard: it creates your own copies of the manager and configurator outside of the Input Icons folder, so this can’t happen again.

**Error: “… The type or namespace name '…' does not exist in the namespace ‘…’ (are you missing an assembly reference?)”**

- Assembly Definitions got added in v1.3.22. To properly include them, the folder structure of the asset needed to be changed. When updating to the latest version you could end up with a wrong folder structure, making the Assembly Definitions not work correctly. To solve the issue, **delete the content of the “Scripts” folder in “InputIcons/Scripts” and reimport the asset** or the Scripts folder again.

**The tool does not behave like configured in the Input Icons Manager or in the Input Icon Set Configurator**

- It could be that you have two Input Icon Manager or Configurator assets in your project and they are fighting for which one actually gets used. Find your Manager and Configurator in the project and make sure “Is Actual Manager” or “Is Actual Configurator” is checked on the one you want to use.

<img src="/input-icons-documentation/assets/images/guide/updating-1.png" alt="Screenshot" width="317">

<img src="/input-icons-documentation/assets/images/guide/troubleshooting-1.png" alt="Screenshot" width="265">

**When you rebind using the rebind prefabs, the icons are updated correctly, but the controls don’t change.**

- This can happen when you use a generated C# class to handle player input. The rebind prefabs can only rebind the actions of the Input Action Asset and not the actions of a generated C# class. Check section [Rebinding Using A Generated C# Class](/input-icons-documentation/rebinding#rebinding-using-a-generated-c-class).

**Controls are weird or do not work anymore**

- The reason might be that you have several active Player Input components in the scene. Search the hierarchy for “Player Input”.

- Another reason could be that the Unity Editor or a build of your game is connected to Steam. Once the Unity Editor has been connected to Steam, it stays connected until you close Unity, which can cause gamepads to stop responding. Restart Unity and see chapter [Steam Input Troubleshooting](/input-icons-documentation/steam) for more information.

**The icons change correctly in the editor but not in the build**

- Make sure there is only one active Input Icons Manager and Configurator in your project (see the previous points). The Input Icons Settings window shows the path of the active manager at the top.

- In some strange cases you might have to recreate the Input Action Asset. I had users reporting that they created their Input Action Asset with Input System 1.3.0, then updated to 1.4.4 and had to recreate their Input Action Asset. Otherwise somehow in the final build the 1.3.0 version was still present.

**A gamepad doesn’t control the game and the icons don’t switch**

- Some gamepads have a switch between XInput (X) and DirectInput (D) mode. In DirectInput mode, Unity detects them as generic joysticks, which \<Gamepad\> bindings don’t match. Switch the gamepad to XInput mode (see section [Keyboard And Gamepad Support](/input-icons-documentation/devices)).

**Prompts don’t animate**

- Make sure “Animate” is enabled on the entry (action reference) that should animate. On all prompts, “Animate” is set per entry.

- Only keys with a pressed sprite animate. Check the icon set used for the current device.

- Text Prompts and animated style tags need an animated sprite asset for the icon set. The Project Status page of the setup wizard shows missing or outdated sprite assets.

- For animated style tags, “Create animated style tags” must be enabled and the styles must have been added to the style sheet again afterwards.

<!-- -->

- A text only shows the first sprite of the animation: a script probably calls **ForceMeshUpdate()** on it (e.g. a text effect or typewriter script, or one that reads the text info). Rebuilding the mesh stops TextMesh Pro’s sprite animation of that text, because the animation keeps changing the old mesh data. Read the text info without ForceMeshUpdate, or avoid rebuilding texts with animated sprites.
