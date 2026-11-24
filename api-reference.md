---
title: API Reference
layout: default
nav_order: 9
---

# Code Documentation

This page documents the key methods and classes for programmatically working with Input Icons.

## InputIconsManagerSO Static Methods

### Icon Display and Updating

| Method | Description |
|--------|-------------|
| `StartUpdatingIconsBehaviour()` | Starts automatic icon updates when devices change |
| `StopUpdatingIconsBehaviour()` | Stops automatic icon updates |
| `ShowDeviceIconsBasedOnSettings()` | Displays icons based on manager settings |
| `ShowGamepadIconsIfGamepadAvailable()` | Shows gamepad icons if available |
| `ShowKeyboardIconsIfKeyboardAvailable()` | Shows keyboard icons if available |
| `RequestDeviceDisplayChange()` | Schedules a device change |
| `CancelRequestedDeviceDisplayChange()` | Cancels a scheduled device change |
| `SetDeviceAndRefreshDisplayedIcons()` | Sets device and updates icons |
| `RefreshCurrentInputDeviceSprites()` | Updates displayed icons |
| `HandleDeviceChange()` | Reacts to InputSystem.onActionChange |
| `HandleInputBindingsChanged()` | Updates Style Sheet and refreshes icons |
| `UpdatePromptDisplayBehavioursManually()` | Manually updates all prompt displays |
| `RefreshInputIconsTexts()` | Refreshes all registered input icon texts |

### Device Management

| Method | Description |
|--------|-------------|
| `GetCurrentInputDevice()` | Returns the currently displayed device |
| `CurrentInputDeviceIsKeyboard()` | Checks if current device is keyboard/mouse |
| `SetCurrentInputDevice()` | Sets the current input device |

### Binding Override Management

| Method | Description |
|--------|-------------|
| `ResetAllBindings()` | Resets all binding overrides |
| `ResetBindingsOfAsset()` | Resets bindings for a specific asset |
| `SaveUserBindings()` | Saves current binding overrides |
| `LoadUserRebinds()` | Loads and applies saved binding overrides |
| `GetSavedBindingOverrides()` | Retrieves saved binding overrides |
| `ApplyBindingOverridesToInputActionAssets()` | Applies binding overrides to action assets |
| `RegisterInputActionAssetForRebinding()` | Registers an asset for rebinding |
| `UpdateRegisteredInputActionAssetsForRebinding()` | Updates registered assets |

## TextPrompt Methods

These methods allow changing text at runtime:

| Method | Description |
|--------|-------------|
| `SetText(string newText)` | Updates text while preserving bindings |
| `SetTextPromptData(List<TextPromptData>)` | Updates the bindings to display |
| `SetTextPromptData(II_TextPromptDataSO)` | Updates bindings using a ScriptableObject |

## Local Multiplayer Management

Access these methods through `InputIconsManagerSO.localMultiplayerManagement`:

| Method | Description |
|--------|-------------|
| `AssignDeviceToPlayer(int playerID, InputDevice device, bool tryToReassign)` | Links a device to a player |
| `SetControlSchemeForPlayer(int playerID, string controlSchemeName)` | Assigns a control scheme to a player |
| `TryReassignDevice(InputDevice reconnectedDevice)` | Tries to reassign a device based on description |
| `UnassignDeviceFromPlayer(int playerID)` | Removes device from player but keeps ID for possible reassignment |