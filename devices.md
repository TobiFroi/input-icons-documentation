---
title: "Devices and Platforms"
layout: default
nav_order: 7
has_children: true
---

# Devices and Platforms

To support keyboards and gamepads, our Input Action Asset(s) need to be correctly set up (see section “[Setting Up The Input Action Asset](/input-icons-documentation/input-action-asset)”)

<img src="/input-icons-documentation/assets/images/guide/devices-1.png" alt="Screenshot" width="231">

In earlier versions, the Input Icons Manager would listen for the “Controls Changed” event on a Player Input component. Since Input Icons 1.3.0 this is no longer the case and changing between keyboard and gamepad icons now also works without a Player Input component in the scene.

**Joysticks and gamepads in DirectInput mode:** Some gamepads, like the Logitech F310, have a switch between XInput (X) and DirectInput (D) mode. In DirectInput mode, Unity detects them as generic joysticks, which \<Gamepad\> bindings don’t match, so they don’t control the game. Most players use gamepads in XInput mode, so this is rarely an issue. If your game supports joysticks with its own \<Joystick\> bindings (e.g. flight sticks), enable **Treat joysticks as gamepads** (Input Icons Settings window → Devices, or on the Input Icons Manager). Then using a joystick switches the icons to the fallback gamepad icons. The setting only affects which icons are shown, not whether a device can control the game.
