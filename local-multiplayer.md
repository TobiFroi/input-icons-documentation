---
title: Local Multiplayer
layout: default
nav_order: 5
---

# Displaying Bindings in Local Multiplayer Games

Input Icons provides robust support for local multiplayer games, allowing you to display the correct input prompts for each player based on their assigned device.

## Overview

In local multiplayer scenarios, you need to track which device belongs to which player and display the appropriate bindings. The `InputIconsManagerSO` manages a dictionary of users that you can access through `InputIconsManagerSO.localMultiplayerManagement`.

## Player and Device Management

### Key Methods

| Method | Purpose |
|--------|---------|
| `AssignDeviceToPlayer(int playerID, InputDevice device, bool tryToReassign)` | Links a device to a specific playerID |
| `SetControlSchemeForPlayer(int playeriD, string controlSchemeName)` | Assigns a control scheme to a player |
| `TryReassignDevice(InputDevice reconnectedDevice)` | Attempts to reassign a device based on its description |
| `UnassignDeviceFromPlayer(int playerID)` | Removes device from player but keeps ID for possible reassignment |

### Implementation Approaches

Depending on how your game spawns and manages players, you can use different approaches:

#### Using Unity's Player Input Manager

If you're using Unity's PlayerInputManager for spawning players:

1. Attach a script to your player prefab that reads values from the PlayerInput component
2. Send these values to `InputIconsManagerSO.localMultiplayerManagement`
3. Since every player has a unique device, you only need to define two control schemes (keyboard and gamepad)


// Attach to player prefab
public class PlayerSetup : MonoBehaviour
{
    void Start()
    {
        PlayerInput playerInput = GetComponent<PlayerInput>();
        int playerIndex = playerInput.playerIndex;
        InputDevice device = playerInput.devices[0];
        
        // Register the player with Input Icons
        InputIconsManagerSO.localMultiplayerManagement.AssignDeviceToPlayer(
            playerIndex, device, false);
    }
}

## Using a Custom Player Spawner
For more advanced setups, such as allowing multiple players to use the same keyboard with different control schemes:

Listen for a "join" action
Check if the control scheme that triggered the join action is available
Spawn a player and assign the device and control scheme

// Example player spawner
public void OnJoinActionPerformed(InputAction.CallbackContext context)
{
    // Get device and control scheme
    InputDevice device = context.control.device;
    string controlSchemeName = GetControlSchemeForDevice(device);
    
    // Check if this control scheme is already in use
    if (IsControlSchemeAvailable(controlSchemeName))
    {
        // Spawn player
        PlayerInput playerInput = PlayerInput.Instantiate(playerPrefab, 
            controlScheme: controlSchemeName, 
            pairWithDevice: device);
            
        // Register with Input Icons
        InputIconsManagerSO.localMultiplayerManagement.AssignDeviceToPlayer(
            playerInput.playerIndex, device, false);
        InputIconsManagerSO.localMultiplayerManagement.SetControlSchemeForPlayer(
            playerInput.playerIndex, controlSchemeName);
    }
}

## Multiplayer-Specific Components
To display bindings for specific players, use these components:
## For Sprites and Images

* II_LocalMultiplayerSpritePrompt: Displays bindings in SpriteRenderers
* II_LocalMultiplayerImagePrompt: Displays bindings in UI Images

These components work similarly to the regular prompt components but add a PlayerID field to specify which player's bindings to display.

## For TextMeshPro

II_LocalMultiplayerTextPrompt: Displays bindings in TextMeshPro text

This component functions like the standard II_TextPrompt but displays bindings for a specific player.

## Runtime Control
When a device is assigned or unassigned, the onInputUsersChanged event is invoked, causing the multiplayer prompt components to update their displayed icons automatically.

## Changing Displayed Bindings at Runtime
Updating text in local multiplayer text prompts works similarly to updating regular text prompts:

// Update the text while preserving bindings
localMultiplayerTextPrompt.SetText("Press <inputaction> to jump");

// Update the bindings to display
localMultiplayerTextPrompt.SetTextPromptData(newTextPromptDataList);

// Use a preconfigured ScriptableObject for bindings
localMultiplayerTextPrompt.SetTextPromptData(textPromptDataSO);

## Example Scene
For a complete implementation example, see the "Local Multiplayer Prompts" example scenes included with the package.
{: .note }
Local multiplayer support is a relatively newer feature and may receive updates. If you encounter issues or have feature requests, please contact the developer.
    
