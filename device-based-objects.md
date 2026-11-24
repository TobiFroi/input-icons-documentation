---
title: "Device-Based Object Control"
layout: default
nav_order: 5
parent: "Devices and Platforms"
---

# Device-Based Object Control

<img src="/input-icons-documentation/assets/images/guide/device-based-objects-1.png" alt="Screenshot" width="328">

Use **II_LocalMultiplayerDeviceBasedObjectController** when you need:

- Different UI elements or visual feedback for each player based on their input device

- Player-specific control prompts in split-screen or local multiplayer games

- Device-appropriate menus or HUD elements for each player

- Automatic switching of UI layouts when players change controllers

**Examples:**

- Player 1 using Xbox controller sees Xbox button prompts while Player 2 using PlayStation sees PlayStation prompts

- Split-screen game showing keyboard controls on one side and gamepad controls on the other

- Local co-op where each player's UI adapts to their controller type

- Fighting games with player-specific button layout displays

**Don't use II_LocalMultiplayerDeviceBasedObjectController when you need:**

- Single-player device switching (use II_CustomDeviceGraphicBehaviour instead)

- Action-specific button prompts that update with rebinding (use II_SpritePrompt or II_ImagePrompt)

- Simple global device detection without player-specific requirements

**Key Difference:** This component manages GameObject visibility per player in local multiplayer scenarios, while II_CustomDeviceGraphicBehaviour handles global device detection for single-player experiences.

**Setup:**

1.  Assign a **Player ID** (0 for Player 1, 1 for Player 2, etc.)

2.  Add **Device Configurations** for each controller type you support

3.  Assign the GameObjects that should appear for each device type

4.  Optionally enable **Gamepad Override** to show the same UI for all gamepad types

**Gamepad Override:** When enabled, any detected gamepad (Xbox, PlayStation, Switch) will show the same set of objects, ignoring device-specific configurations. This is useful when you have generic gamepad UI that works for all controller types.
