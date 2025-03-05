---
title: Style Tag Setup
layout: default
parent: Setup
nav_order: 3
---

# Setup for TextMeshPro Style Tag

After completing the Base Setup and creating TMP_SpriteAssets, you can set up the TextMeshPro style tag integration. This approach allows you to display input bindings without adding components to your objects.

## Overview

The style tag approach uses TextMeshPro's built-in style system to display input bindings with simple tags like `<style=ActionMapName/ActionName>`.

## Advantages and Limitations

### Advantages
- No additional components needed on text objects
- Easy integration with existing text
- Works well with other systems that use TextMeshPro tags

### Limitations
- Multiple device types cannot be displayed simultaneously
- Only the first control scheme in each list can be displayed
- The "show all available bindings" option affects all texts globally
- No inherent support for local multiplayer
- Requires re-setup when adding or renaming actions

## Setup Process

1. **Complete Prerequisites**:
   - Finish the [Base Setup](base-setup.md)
   - Create TMP_SpriteAssets through the [TextMeshPro Setup](tmp-setup.md)

2. **Add Input Action Assets**:
   - In the setup window, ensure your Input Action Assets are added to the "Used Action Assets" list
   - Verify that the control scheme names match those defined in the Base Setup

3. **Verify Action Detection** (Optional):
   - Open Tools → Input Icons → Input Icons TMPro Style List Window
   - This window shows all available actions that can be referenced through style tags
   - Verify your actions appear correctly in the list

   ![Style List Window](/input-icons-documentation/assets/images/style-list-window.png)

4. **Generate Style Sheet Entries**:
   - In the "Setup for TextMeshPro style tag" section of the setup window, choose one of these options:
     - **Quick Setup**: Automatically adds all actions from your Input Action Assets
     - **Manual Setup**: Lets you select specific actions to add

5. **Enable Style Sheet Autoupdates**:
   - Check the "Enable Style Sheet Autoupdates" option
   - This ensures the style tags update automatically when the input device changes

## How It Works

When you add style tags to the TMP Default Style Sheet, each tag gets associated with sprite or font references for each supported device type. At runtime, the InputIconsManager updates these tags based on the current input device.

## Using the Style Tags

After setup, you can use tags like this in any TextMeshPro text field:
Press <style=Platform Controls/Jump> to jump
Use <style=Platform Controls/Move> to move

For font-based icons:
Press <style=Font/Platform Controls/Jump> to jump

For specific directions in composite bindings:
Press <style=Platform Controls/Move/Down> to crouch

## Updating the Style Sheet

You need to update the style sheet whenever you:
- Add new actions to your Input Action Assets
- Rename existing actions
- Add new Input Action Assets

To update, simply return to the setup window and re-generate the style sheet entries.

## Troubleshooting

If your style tags don't work:

- **Style Sheet Not Saving**: Make a small manual change to any field in the style sheet and undo it to force a save
- **Missing Sprites**: Ensure the sprite assets exist and are properly referenced
- **Action Not Found**: Verify the action exists in the Style List Window
- **Incorrect Tag Format**: Double-check the exact format: `<style=ActionMapName/ActionName>`

{: .note }
When entering Play mode, the style sheet is automatically updated if you enabled Style Sheet Autoupdates. This ensures the correct icons appear based on the current input device.