---
title: Steam Integration
layout: default
nav_order: 10
---

# Steam Input Troubleshooting

When integrating Input Icons with Steamworks.NET, you may encounter some challenges due to how Steam can interact with Unity's Input System.

## Understanding the Issue

Steam's Input system can take over XInput in certain scenarios, causing Unity's Input System to misidentify devices. For example, a PS4 controller might be detected as an Xbox controller.

This behavior depends on:
1. The player's Steam settings
2. Whether Steam Input is enabled for specific controllers
3. Whether the game is running through Steam

## Steam Controller Settings

The simplest way to ensure consistent behavior is through Steam's controller settings:

1. Open Steam settings: Steam → Settings → Controller
2. Ensure that controller support is disabled for each controller type

![Steam Controller Settings](/input-icons-documentation/assets/images/steam-controller-settings.png)

During development, disabling these settings is recommended as it can also affect device responsiveness in the Unity Editor when Steam is running.

## Per-Game Settings

Players can also override these settings for individual games:

1. Right-click the game in the Steam library
2. Select "Properties..." → "Controller"
3. Choose "Disable Steam Input" from the dropdown menu

![Steam Game Properties](/input-icons-documentation/assets/images/steam-game-properties.png)

You might want to recommend this setting to your players in your game's documentation, although most players have Steam Input disabled by default.

## Steamworks Integration Settings

On your game's Steamworks page, you can control which controllers opt into Steam Input:

![Steamworks Settings](/input-icons-documentation/assets/images/steamworks-settings.png)

The recommended approach is to leave these unchecked so that Steam Input won't interfere with Unity's Input System by default.

## Steam Input Extension Behavior

The `InputIconsSteamworksExtensionSO.cs` script included with Input Icons handles the case when Steam Input is enabled for specific controllers. When it detects a controller with Steam Input enabled, it overrides the Icon Set detected by Unity's Input System with the Icon Set matching the first connected Steam Input controller.

### Behavior Examples

If a player has enabled Steam Input for Switch Pro Controllers:

| Connected Controller | Unity Detects | Icons Shown |
|---------------------|---------------|-------------|
| Switch Pro | Xbox controller | Switch icons |
| PlayStation | PlayStation controller | Switch icons |
| Xbox | Xbox controller | Switch icons |
| None (only PS controller) | PlayStation controller | PlayStation icons |
| None (only Xbox controller) | Xbox controller | Xbox icons |

This behavior enables players to see the correct icons for their physical device, even when Steam is reporting it as a different type.

### Customizing Steam Integration

If you need to modify this behavior:

1. You can edit the `InputIconsSteamworksExtensionSO.cs` script
2. Remove the script entirely if you don't need Steam integration
3. Remove the creation of its instance in the `OnEnable` method of `InputIconsManagerSO.cs`

{: .warning }
Removing the Steam integration means players who enable Steam Input for specific devices may not see the correct icons.

## Local Multiplayer with Steam Input

Currently, there are limitations when supporting local multiplayer games with Steam Input enabled for certain gamepad types. If Steam Input is enabled for PlayStation and Switch Pro controllers, players using these controllers will see Xbox icons since Unity's Input System detects them as Xbox controllers.

Most players won't have these settings enabled (they're disabled by default), so this shouldn't be a major concern for most games.

If players report incorrect icons, suggest that they disable Steam Input for your game through the Steam properties menu.

{: .note }
If you discover better ways to handle Steam Input integration with Unity's Input System, please contact the developer.