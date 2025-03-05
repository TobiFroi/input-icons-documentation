---
title: TextMeshPro Setup
layout: default
parent: Setup
nav_order: 2
---

# TextMeshPro Setup

To display bindings in TextMeshPro texts, we use the sprite tag to display key icons alongside other text. This requires creating TMP_SpriteAssets that contain all the sprites we need.

## Prerequisites

Before continuing with the TextMeshPro setup, ensure you have:
- Completed the [Base Setup](base-setup.md)
- TextMeshPro 2.1.6 or higher installed in your project

## Setup Process

1. Open the Input Icons Setup window (Tools → Input Icons → Input Icons Setup)

![TMP Setup Window](/input-icons-documentation/assets/images/tmp-setup.png)

2. **Base Setup**: Choose Control Schemes and Manage Input Action Assets

3. **TextMeshPro Setup**: If you moved the TextMeshPro folder to a different location, update the path values before proceeding
   - Default Sprite Assets path: "Assets/TextMesh Pro/Resources/Sprite Assets/"
   - Default Style Sheet path: "Assets/TextMesh Pro/Resources/Style Sheets/"

4. **SDF Fonts Option**: Enable the "Use fonts" checkbox if you want the ability to display bindings as SDF fonts
   - SDF fonts maintain sharp edges at all sizes
   - Sprites may become blurry at large sizes
   - Fonts have less visual detail than sprites

5. **Create Sprite Assets**: Click the "Create TMP_SpriteAssets" button
   - This creates sprite assets for each device type (keyboard, different gamepads, etc.)
   - If you selected "Use fonts", SDF font assets will also be created

6. **Recompile**: You may need to recompile your project or enter play mode for the new Sprite Assets to take effect

7. **Style Tag Setup**: You can display prompts without the need for additional components by using the TMP style tag.
   - Add style sheet entries to the default style sheet
   - The styles update at runtime to display keyboard or gamepad sprites

## What Gets Created

This process creates several assets:
- TMP_SpriteAssets for each device type (keyboard, Xbox, PlayStation, etc.)
- SDF font assets (if enabled) for displaying bindings as text

These assets are placed in your TextMeshPro Resources folder, making them available to all TextMeshPro components in your project.

## Next Steps

After completing this setup, you can:
1. Use the [II_TextPrompt](../displaying-bindings/tmpro-bindings.md) component to display bindings in your text
2. Set up the [TextMeshPro style tag](../displaying-bindings/style-tag-bindings.md) for component-free integration

## Quality Settings for Small Sprites

If your sprites appear blurry when displayed at small sizes, you can improve their readability:

1. Select the texture in your sprite assets folder
2. Enable "Generate Mip Maps" in the Import Settings
3. Click Apply

Since version 1.4.x, this setting is enabled by default for generated sprite assets.

## Troubleshooting

If sprites don't appear in your TextMeshPro text:
- Ensure all TMP_SpriteAssets were created successfully
- Check that the paths in your TextMeshPro settings match the actual locations
- Make sure you're using either the proper sprite tags or the II_TextPrompt component
- Try entering play mode - sometimes the sprite assets need to be loaded at runtime first

For more detailed troubleshooting, see the [Troubleshooting](../troubleshooting.md) section.