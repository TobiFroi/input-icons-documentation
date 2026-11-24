---
title: "Local Multiplayer"
layout: default
nav_order: 5
parent: "Displaying Bindings"
---

# Local Multiplayer

Setting up local multiplayer is not an easy task, but Input Icons provides the tools to make it much more manageable. This section will guide you through the complete setup process.

**Overview**

The **InputIconsManagerSO** manages a dictionary of users which you can access and manage through the static field **InputIconsManagerSO.localMultiplayerManagement**. This system allows each player to have their own control scheme and device assignment while maintaining separate binding configurations.

**Example Scene Reference**: For a complete working implementation, examine the **InputIcons_ExampleScene12_LocalMultiplayerMultipleControlSchemes** scene. This example demonstrates all the concepts covered in this guide and provides a practical reference for your own implementation.

**Key Methods**

Here are the essential methods you'll use for local multiplayer management:

| **AssignDeviceToPlayer (int playerID, InputDevice device, bool tryToReassign)** | Links a device to a specific playerID. If tryToReassign is true, this method will search through existing players and link the device to the original player if the device description matches. |
|---------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SetControlSchemeForPlayer (int playerID, string controlSchemeName)**          | Assigns a control scheme to a player, making it easier for multiplayer prompts to display the correct sprites.                                                                                  |
| **TryReassignDevice(InputDevice reconnectedDevice)**                            | Attempts to reassign a device based on the device description.                                                                                                                                  |
| **UnassignDeviceFromPlayer(int playerID)**                                      | Sets the device for a specific playerID to null but keeps the playerID and device description for future reassignment.                                                                          |

**Step-by-Step Setup Guide**

**1. Configure Your Input Action Asset**

First, set up your Input Action Asset with control schemes for each player. You can use descriptive names like:

- Gamepad, Gamepad 2, Keyboard And Mouse, Keyboard And Mouse 2

- Or player-based names like Player1, Player2, Player3, Player4

Each control scheme should define which devices that player can use and contain all the actions they need.

**2. Choose Your Player Spawning Method**

You have two main approaches for spawning players:

**Option A: Unity's Player Input Manager Component**

- Attach a Player Input component to your player prefab

- Add a script that reads values from the Player Input component and sends them to InputIconsManagerSO.localMultiplayerManagement

- Since each player has a unique device, you typically need only two control schemes (keyboard and gamepad)

**Option B: Custom Player Spawner (Recommended for Advanced Setup)**

This method allows multiple players to share the same keyboard through separate control schemes:

<img src="/input-icons-documentation/assets/images/guide/local-multiplayer-1.png" alt="Screenshot" width="540">

**3. Set Up Display Components**

Use these components to show bindings for each player:

- **II_LocalMultiplayerSpritePrompt -** Displays sprite-based button prompts

- **II_LocalMultiplayerImagePrompt -** Displays image-based button prompts

- **II_LocalMultiplayerTextPrompt -** Displays text-based button prompts

**Component Choice Clarification:** Each component requires a **PlayerID** field that matches against the multiplayer dictionary to display the correct sprites for that player's control scheme and device.

**Alternative Approach**: If you're using Option B (Custom Player Spawner), you can also use the standard single-player components which may be easier to set up:

- **II_SpritePrompt** - Configure directly to a specific control scheme

- **II_ImagePrompt** - Configure directly to a specific control scheme

- **II_TextPrompt** - Configure directly to a specific control scheme

These standard components can be simpler to use since you can directly assign the control scheme rather than managing PlayerIDs, making them a good choice even for multiplayer scenarios.

**4. Implement Rebinding Support for Local Multiplayer Games**

For local multiplayer rebinding, Input Icons provides the II_LocalMultiplayerRebindReactor component that handles binding synchronization across all players.

**A. Rebinding UI Components**

- Use the **II_UIRebindInputActionImageBehaviour** script

- Or use the pre-made **II_UI_RebindActionImageObject prefab** from the Prefabs folder

**B. Rebind Reactor Component**

Add the II_LocalMultiplayerRebindReactor script to each player controller:

**Required Configuration:**

- **Original Input Action Asset**: Drag in your Input Action Asset

- **Player Input To Update**: Assign the PlayerInput component (auto-detects if on same object)

- **Log Binding Updates**: Enable for debugging rebinding issues

**How It Works:** The rebind reactor automatically subscribes to Input Icons binding events and applies changes to each player's action asset by overwriting the bindings of the the referenced input action asset.

<img src="/input-icons-documentation/assets/images/guide/local-multiplayer-2.png" alt="Screenshot" width="379">

**Key Features:**

- **Automatic Synchronization**: When any player rebinds a key, all players receive the updated bindings

- **Control Scheme Isolation**: Each player only uses bindings that match their specific control scheme

- **Persistent Storage**: Supports both file system and PlayerPrefs for saving bindings

- **Error Handling**: Includes comprehensive error handling and optional debug logging

- **Manual Testing**: Provides ForceUpdateBindings() method for testing

This system ensures that when Player 1 rebinds their "Q" key, it won't affect Player 2's "Enter" key since they use different control schemes, keeping each player's controls completely separate.

## Player Profile Support

**Note**: The previous guide statement about profiles not working with simultaneous local multiplayer was incorrect and has been removed. Player profiles work perfectly with local multiplayer games.

Player profiles are designed for family members taking turns and wanting to quickly switch between preferred bindings (e.g., one prefers WASD, another prefers arrow keys). While less critical for simultaneous multiplayer, profiles can still be useful and work automatically with Input Icons.

Use InputIconsManagerSO.SwitchToPlayerProfile(int profileIndex) to switch between saved binding configurations when needed.

**Events and Updates**

The onInputUsersChanged event is invoked when players are assigned or unassigned, causing components like II_LocalMultiplayerSpritePrompt to automatically update their displayed sprites.

**Example Implementation Summary**

Input Icons provides ready-to-use components that handle most of the complexity:

1.  **Set up your Input Action Asset** with control schemes for each player (P1-P4)

2.  **Add II_LocalMultiplayerControlSchemePlayerSpawner** to handle player joining:

    - Configure join action reference and player prefab

    - Set control scheme names to match your Input Action Asset

3.  **Use II_LocalMultiplayerPlayerInputHandler** on spawned players to manage control schemes

4.  **Add display components** (II_LocalMultiplayerSpritePrompt, etc.) with appropriate PlayerID assignments

5.  **Include II_LocalMultiplayerRebindReactor** on each player for binding customization support

6.  **Set up rebinding UI** using II_UIRebindInputActionImageBehaviour or the provided prefabs

The provided components handle device tracking, control scheme assignment, and binding synchronization automatically, so you can focus on your game logic rather than input management details.

**Troubleshooting**

If you encounter issues:

- Verify that PlayerIDs match between your spawner and display components

- Ensure control scheme names in your Input Action Asset match those used in SetControlSchemeForPlayer()

- Check that devices are properly assigned before attempting to display prompts

- Enable debug logging in II_LocalMultiplayerRebindReactor for rebinding issues

**Example Scene Reference**: The **InputIcons_ExampleScene12_LocalMultiplayerMultipleControlSchemes** scene provides a complete working implementation that you can study and use as a reference for troubleshooting your own setup.

You can use the following components to display bindings in local multiplayer games for each player:

Note this is quite a new feature and there might be bugs. If you think something important is missing, please let me know (<support@octacube-studios.com>)

### Changing displayed Bindings in II_LocalMultiplayerTextPrompts

Updating text in local multiplayer text prompts does work very similar to updating general II_TextPrompt components. Have a look at the 4.1.3.
