---
title: Style Tag Bindings
layout: default
parent: Displaying Bindings
nav_order: 3
---

# Displaying Bindings with TextMeshPro Style Tags

For scenarios where you want to avoid adding extra components, you can use TextMeshPro's style tag system to display input bindings. This approach requires completing the "Setup for TextMeshPro style tag" section in the setup window.

## Using Style Tags

After setup, you can display bindings by using the TextMeshPro style tag:<style=ActionMapName/ActionName>
For example, to display the bindings for a "Jump" action in the "Platform Controls" action map: Press <style=Platform Controls/Jump> to jump
To display the bindings for a "Move" action: Use <style=Platform Controls/Move> to move
This would display either WASD, arrow keys, or a gamepad stick depending on the active input device.

## Style Tag List

To see all available style tags, open:
Tools → Input Icons → Input Icons TMPro Style List Window

![Style Tag Window](/input-icons-documentation/assets/images/style-tag-window.png)

This window shows all the tags you can copy and paste into your text.

## Displaying Direction-Specific Bindings

To show only one part of a composite binding (like only the "down" key from WASD): Press <style=Platform Controls/Move/Down> to crouch

## Using SDF Fonts Instead of Sprites

Since version 2.0.0, you can display icons as special SDF fonts instead of sprites: Press <style=Font/ActionMap/Action> to perform action
For example: Press <style=Font/Platform Controls/Jump> to jump

The advantage of fonts is that they remain crisp at any size, while sprites may become pixelated when scaled up.

## Limitations

The style tag approach has some limitations:

- Multiple device types cannot be displayed simultaneously
- Only the first control scheme in your lists can be displayed
- The "show all available options" setting is global and affects all texts
- No inherent support for local multiplayer
- Requires re-setup when adding or renaming actions

{: .note }
When the game starts, the style sheet entries are automatically updated to show the correct icons for the current device (if you enabled Style Sheet Autoupdates in the setup window).