---
title: "Dynamic Device Graphics"
layout: default
nav_order: 4
parent: "Devices and Platforms"
---

# Dynamic Device Graphics

**Use II_CustomDeviceGraphicBehaviour when you need:**

- Device-specific graphics that don't represent specific input actions

- UI elements like platform logos, control scheme indicators, or branding

- Graphics that should match the current input device but remain static

- Simple setup without configuring input action references

<img src="/input-icons-documentation/assets/images/guide/device-graphics-1.png" alt="Screenshot" width="192">

**Examples:**

- PlayStation vs Xbox controller icons in your UI

- "Press any key" vs "Press any button" graphics

- Platform-specific artwork or branding elements

- Control scheme selection screens

**Don't use II_CustomDeviceGraphicBehaviour when you need:**

- Input prompts that show specific buttons (use II_SpritePrompt instead)

- UI prompts that update when players rebind controls (use II_ImagePrompt instead)

- Action-specific button displays like "Press \[A\] to jump"

**Key Difference:** This component shows *device type* graphics, while II_SpritePrompt and II_ImagePrompt show *specific button* prompts that respond to control rebinding.
