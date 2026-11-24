---
title: "Displaying A Specific Device"
layout: default
nav_order: 3
parent: "Devices and Platforms"
---

# Displaying A Specific Device

<img src="/input-icons-documentation/assets/images/guide/specific-device-1.png" alt="Screenshot" width="188">

You can open a device switching window by going to **Tools Input Icons Input Icons Switcher.** Use the buttons in that window to change the displayed icons to whichever device is supported (Keyboard, PS3, PS4, PS5, Switch, XBox, Fallback).

This can be very useful to test how the buttons look in the scene without needing to enter play mode.

These buttons make use of a static method on the input icons manager called **InputIconsSO.SetDeviceAndRefreshDisplayedIcons (InputIconSetConfiguratorSO.InputIconsDevice inputIconsDevice)**

This is not fully fledged out and might display wrong keys if some bindings exist in the keyboard control scheme and not in the gamepad control scheme and vice versa.

In the example scene 10 (ChangeDisplayedSpritesManually) is a panel which provides the same functionality, but the custom editor window makes that panel somewhat obsolete.
