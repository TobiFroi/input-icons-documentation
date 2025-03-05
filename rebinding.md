---
title: Rebinding
layout: default
nav_order: 7
---

# Rebind Buttons

Input Icons includes built-in support for creating rebindable inputs in your game, allowing players to customize their control scheme.

## Using the Rebind Button Prefab

In the prefab folder, you'll find `II_UI_RebindActionImageObject`, a prefab for creating rebindable action buttons. This prefab serves as a good starting point, but you may want to create your own custom version with your game's visual style.

![Rebind Button](/input-icons-documentation/assets/images/rebind-button.png)

## Rebind Button Configuration

The rebind button component offers several configuration options:

| Setting | Description |
|---------|-------------|
| Action Reference | The input action to rebind |
| Search Method | "Binding Type" or "Binding Index" |
| Binding Type Settings | Same as other prompt components (see [Sprites and Images](displaying-bindings/sprites-and-images)) |
| Allow Rebinding | When disabled, shows the binding but prevents changing it |
| Ignore Other Buttons | Keeps this binding even if another button gets bound to the same key |
| Action Display Name | Text to show as the action's label |
| Rebind Behavior | How to handle conflicts when rebinding |

## Rebind Behaviors

The "Rebind Behavior" setting (also available globally in the Input Icons Manager) offers three options:

1. **Override Existing**: The new binding is accepted, and any conflicting action is unbound
2. **Cancel Override If Binding Already Exists**: Displays a message like "Binding already in use" and cancels the rebind
3. **Always Apply And Keep Other Bindings**: Accepts the new binding without affecting other bindings that use the same input

## Rebinding with Generated C# Classes

If you're using a generated C# class from an Input Action Asset and want to use the rebind buttons:

1. Call these methods in your Awake function where `inputActions` is your generated class instance:

```csharp
// Register your generated class's asset for rebinding
InputIconsManagerSO.RegisterInputActionAssetForRebinding(inputActions.asset);

// Apply any saved binding overrides to your asset
InputIconsManagerSO.UpdateRegisteredInputActionAssetsForRebinding(inputActions.asset);
```

2. These two lines ensure that:

* The Input Icons Manager knows about your generated class's asset
* Binding changes made through rebind buttons are applied to your generated class
* Saved binding overrides are loaded and applied to your asset


For a complete example, see the "InputIcons_ExampleScene6_GeneratedCode" scene included with the package.

## Custom Rebinding Implementation
If you prefer to implement your own rebinding system:

1. Use the InputIconsManagerSO.ApplyBindingOverridesToInputActionAssets method to apply binding overrides to assets managed by the InputIconsManager

```csharp
// After applying rebinds to your generated class
YourInputActions inputActions = new YourInputActions();
inputActions.Jump.ApplyBindingOverride("<Keyboard>/space");

// Sync the changes with Input Icons
InputIconsManagerSO.ApplyBindingOverridesToInputActionAssets();
```

2. This ensures the InputIconsManager displays the correct sprites after your custom rebinding process

## Saving and Loading Bindings
The InputIconsManager automatically handles saving and loading binding overrides for registered Input Action Assets. You can also manually trigger these operations:
```csharp
// Save current binding overrides
InputIconsManagerSO.SaveUserBindings();

// Load saved binding overrides
InputIconsManagerSO.LoadUserRebinds();

// Reset all bindings to defaults
InputIconsManagerSO.ResetAllBindings();

// Reset bindings for a specific asset
InputIconsManagerSO.ResetBindingsOfAsset(inputActionAsset);
```

## Event System Integration
The rebind buttons integrate with Unity's Event System for seamless UI navigation:

* When a rebind operation starts, other UI elements are temporarily disabled
* When completed, UI navigation is restored
* The "listening for input" state has a visual indicator

