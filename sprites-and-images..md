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
| Available Binding Index | Choose which specific binding to