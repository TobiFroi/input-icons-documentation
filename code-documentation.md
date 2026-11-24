---
title: "Code Documentation"
layout: default
nav_order: 9
---

# Code Documentation

The tool already handles most use cases, but if you have additional need to change or update icons at runtime, the methods listed here should prove be useful. You will find most important methods on the InputIconsManagerSO as static methods.

**InputIconsManagerSO Static Methods**

| **Icon Display and Updating**                                      |                                                                                                                                                |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| **StartUpdatingIconsBehaviour**                                    | Starts to automatically change the displayed icons when the user switches devices.                                                             |
| **StopUpdatingIconsBehaviour**                                     | Stops to automatically change the displayed icons when the user switches devices.                                                              |
| **ShowDeviceIconsBasedOnSettings**                                 | Displays preferred icons based on manager settings. (Keyboard and Mouse, Gamepad, Auto)                                                        |
| **ShowGamepadIconsIfGamepadAvailable**                             | Shows gamepad icons if a gamepad is connectd.                                                                                                  |
| **ShowKeyboardIconsIfKeyboardAvailable**                           | Shows keyboard icons if a keyboard is connected.                                                                                               |
| **RequestDeviceDisplayChange**                                     | Schedules a device change after a short time (Instance.deviceChangeDelay)                                                                      |
| **CancelRequestedDeviceDisplayChange**                             | Cancels a scheduled device change. Does happen if a device change was scheduled but the previously used device was used again in the meantime. |
| **SetDeviceAndRefreshDisplayedIcons**                              | Sets the current input device and displays icon for the newly set device.                                                                      |
| **RefreshCurrentInputDeviceSprites**                               | Updates displayed icons.                                                                                                                       |
| **RefreshSteamInputDetection**                                     | Re-detects controllers behind Steam Input and updates displayed icons. Call it after your project initialized Steam.                           |
| **WasLaunchedBySteam**                                             | Returns true if the game was launched through Steam. Useful for one build on several stores.                                                   |
| **TEXT_TAG_VALUE, TEXT_OPENING_TAG_VALUE, TEXT_CLOSING_TAG_VALUE** | The tag Text Prompts replace with icons, and the rich text put around their icons. Read from and saved on the active Input Icons Manager.      |
| **HandleDeviceChange**                                             | Reacts to a InputSystem.onActionChange. If necessary, updates displayed icons to reflect the new device.                                       |
| **HandleInputBindingsChanged**                                     | Manages changes in input bindings. Updates the Style Sheet and refreshes displayed Icons                                                       |
| **SetDeviceAndRefreshDisplayedIcons**                              | Sets device and updates displayed icons.                                                                                                       |
| **UpdatePromptDisplayBehavioursManually**                          | Manually updates all prompt displays.                                                                                                          |
| **RefreshInputIconsTexts**                                         | Refreshes all registered input icon texts.                                                                                                     |

| **Device Management**            |                                                                                          |
|----------------------------------|------------------------------------------------------------------------------------------|
| **GetCurrentInputDevice**        | Returns the input device which is currently being displayed.                             |
| **CurrentInputDeviceIsKeyboard** | Checks if the current device is a keyboard or a mouse as both are treated as one device. |
| **SetCurrentInputDevice**        | Sets the Instance.currentInputDevice and inputDeviceToChangeTo values                    |

| **Player Profile Management**                         |                                                                                                                                                  |
|-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| **SwitchToPlayerProfile(int profileIndex)**           | Switches to a different player profile and immediately loads its bindings. Updates the current active profile and refreshes all displayed icons. |
| **SaveBindingsToPlayerProfile(int profileIndex)**     | Saves the current binding overrides to a specific player profile. Works with both PlayerPrefs and JSON file storage methods.                     |
| **LoadBindingsFromPlayerProfile(int profileIndex)**   | Loads binding overrides from a specific player profile without switching to it. Returns a dictionary of binding overrides.                       |
| **CopyPlayerProfile(int fromProfile, int toProfile)** | Copies all bindings from one player profile to another. Useful for duplicating control schemes or creating templates.                            |
| **DeletePlayerProfile(int profileIndex)**             | Deletes a player profile's rebind data. Cannot delete profile 0 (default). Automatically switches to profile 0 if deleting the current profile.  |
| **GetExistingPlayerProfiles()**                       | Returns a list of player profile indices that contain saved binding data. Works with both storage methods.                                       |
| **GetPlayerProfileInfo()**                            | Returns detailed information about all player profiles including storage method, file sizes, and binding counts. Useful for debugging.           |

| **Storage Method Management**                  |                                                                                                                                   |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| **GetRebindsFilePath(int playerProfile = -1)** | Returns the file path where rebind data is stored for JSON file mode. Returns empty string for PlayerPrefs mode.                  |
| **GetPlayerPrefsKey(int playerProfile = -1)**  | Returns the PlayerPrefs key used to store rebind data. Accounts for profile-specific keys when multi-player profiles are enabled. |

| **Binding Override Management**              |                                                                         |
|----------------------------------------------|-------------------------------------------------------------------------|
| **ResetAllBindings**                         | Resets all binding overrides of used Input Action Assets.               |
| **ResetBindingsOfAsset**                     | Resets bindings for a specific asset.                                   |
| **SaveUserBindings**                         | Saves current binding overrides of used Input Action Assets.            |
| **LoadUserRebinds**                          | Loads and applies saved binding overrides of used Input Action Assets.  |
| **GetSavedBindingOverrides**                 | Retrieves saved binding overrides.                                      |
| **ApplyBindingOverridesToInputActionAssets** | Can be used to apply binding overrides to the used Input Action Assets. |

| **Enhanced Binding Override Management**                                   |                                                                                                                                                                  |
|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SaveBindingsToJsonFile(OverrideBindingDataWrapperClass bindingList)**    | Internal method that handles saving binding data to JSON files. Includes verification and fallback to PlayerPrefs on failure.                                    |
| **SaveBindingsToPlayerPrefs(OverrideBindingDataWrapperClass bindingList)** | Internal method that handles saving binding data to PlayerPrefs. Includes size limit warnings and error handling.                                                |
| **MigrateFromPlayerPrefsIfNeeded()**                                       | Automatically migrates legacy PlayerPrefs data to the current storage method. Only runs when switching to JSON file storage and migration hasn't been completed. |

**TextPrompt methods to change text at runtime**

<table>
<colgroup>
<col style="width: 42%" />
<col style="width: 57%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>SetText(string newText)</strong></th>
<th>This applies a new text and also refreshes the TMPro component.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>SetTextPromptData(List&lt;TextPromptData&gt; newTextPromptDatas)</strong></td>
<td>Use this method to update the list of bindings to display.</td>
</tr>
<tr class="even">
<td><strong>SetTextPromptData(II_TextPromptDataSO textPromptDataSO)</strong></td>
<td><p>Similar to the previous method but easier to use.</p>
<p>This can be used to update the list of bindings to display. First you need to create a Scriptable Object of type II_TextPromptDataSO. This object manages a <strong>TextPromptData</strong> list, similar to the II_TextPrompt component. Add the actions you want to display to that Scriptable Object, then call the SetTextPromptData method on the II_TextPrompt to display the bindings defined in the Scriptable Object.</p>
<p>The best way to use this is to create all the Scriptable Objects you need beforehand and assign them when needed.</p>
<p>

<img src="/input-icons-documentation/assets/images/guide/text-prompts-4.png" alt="Screenshot">

</p>
<p>Also, have a look at the TextPromptsRuntimeUpdates example scene.</p></td>
</tr>
</tbody>
</table>

**Local Multiplayer Management**

More about this in this section: [Displaying Bindings in Local Multiplayer Games](/input-icons-documentation/local-multiplayer)

| Use through: **InputIconsManagerSO.localMultiplayerManagement**                 |                                                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **AssignDeviceToPlayer (int playerID, InputDevice device, bool tryToReassign)** | Use this to link a device to a specific playerID. If tryToReassign is set to true, this method will first search through all already available players and link the device to the original player if the device description matches the description of a player. |
| **SetControlSchemeForPlayer (int playeriD, string controlSchemeName)**          | Assign a control scheme to a player. This makes it easier for II_LocalMultiplayerSprite-/ and -ImagePrompts to display the correct sprites.                                                                                                                      |
| **TryReassignDevice(InputDevice reconnectedDevice)**                            | This will try to reassign a device based on the device description                                                                                                                                                                                               |
| **UnassignDeviceFromPlayer(int playerID)**                                      | Sets the device for a specific playerID to null but keeps the playerID and the device description so the device may be reassigned in the future.                                                                                                                 |

**Animated Prompts**

| **II_SpritePrompt.IsPressedAnimationFrame(interval)**         | Shared animation clock of animated prompts: true during the pressed half of the cycle. Use it to animate your own graphics in sync with the prompts. |
|---------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| **InputIconSetBasicSO.GetPressedSprite(...)**                 | Returns the pressed sprite of a key (by name) or of a normal sprite, or null if the icon set has none.                                               |
| **InputIconSetBasicSO.GetAnimatedSpriteTags(text, interval)** | Static. Replaces the sprite tags in a text with animated tags for keys that have a pressed sprite in an animated sprite asset.                       |
| **InputIconSetConfiguratorSO.GetPressedSprite(sprite)**       | Static. Finds the pressed sprite of a normal sprite in the icon sets of the configurator.                                                            |
