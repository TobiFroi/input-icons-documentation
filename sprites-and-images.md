---
title: Sprites and Images
layout: default
parent: Displaying Bindings
nav_order: 1
---
# Displaying Bindings with Sprites and Images
To show current bindings in SpriteRenderers or UI Images, add the `II_SpritePrompt` or `II_ImagePrompt` script to an object in your scene. Both components function similarly and use a custom inspector to automatically adapt their appearance and functionality based on your settings.
## Component Options
These components provide two main ways to search for bindings:
### Searching by "Binding Index"
![Binding Index Search](/input-icons-documentation/assets/images/binding-index-search.png)
| Setting | Description |
|---------|-------------|
| Action Reference | The input action to display |
| Binding Index | Which binding of the action to display |
| Device Type | "Keyboard And Mouse", "Gamepad" or "Auto" |
This approach is simple but be careful: if you add/remove/move bindings in your Input Action Asset, your displayed bindings might change.
### Searching by "Binding Type"
![Binding Type Search](/input-icons-documentation/assets/images/binding-type-search.png)
This is generally the better option, offering more flexibility:
| Setting | Description |
|---------|-------------|
| Device Type | "Keyboard And Mouse", "Gamepad" or "Auto" |
| Advanced Mode | Toggle between normal and advanced mode |
| Composite Type | Automatically set in normal mode |
| Control Scheme Index | Choose which control scheme to display |
| Binding ID in List | Choose which binding to display |
#### Advanced Mode
Advanced Mode provides even more control for complex bindings:
| Setting | Description |
|---------|-------------|
| Composite Types | Display a composite binding (like WASD) or non-composite (like a gamepad stick) |
| Binding Types | Which direction (Up, Down, Left, Right, etc.) to display |
| Available Binding Index | Choose which specific binding to display when multiple options exist |

## General Settings
| Setting | Description |
|---------|-------------|
| Renderer | The Sprite Renderer or UI Image component that will display the button prompt |
| (Optional) Keyboard Icon Set | Override to always use a specific keyboard icon set instead of the current default |
| (Optional) Gamepad Icon Set | Override to always use a specific gamepad icon set instead of detecting the current gamepad type |

## Automatic Device Detection
When "Auto" is selected as the Device Type, the component will automatically switch between keyboard and gamepad sprites based on the last input device used by the player. This creates a seamless experience where button prompts match the current input method.

## Using in Dynamic UI
These components work well in dynamic UI situations:
- Pause menus that show control schemes
- Contextual prompts for interactions
- On-screen controls or HUD elements

## Tips for Best Results
- Use Binding Type search for more stable references that won't break if you modify your Input Action Asset
- If you're showing multiple directions of a composite (like showing all WASD keys), create multiple prompt components and set each to a different direction