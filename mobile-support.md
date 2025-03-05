---
title: Mobile Support
layout: default
nav_order: 6
---

# Mobile Support (Android & iOS)

Since version 3.2.0, Input Icons supports displaying specific sprites on mobile devices, with some differences compared to keyboard and gamepad support.

## Key Differences

The main difference is that displayed sprites on mobile are **not** derived from actual bindings within an Input Action Asset. The displayed sprites are fixed and will not adapt to rebound input actions. For most mobile games, this isn't an issue as users rarely rebind touch inputs.

## Mobile Icon Sets

Instead of referencing an input action in your components, you'll use strings defined in your mobile Icon Set:

1. Find the default mobile Icon Set at "Assets/InputIcons/IconSet_Mobile_Grey"
2. Use the Custom Context list to define mobile actions you want to display
3. **Recommended**: Duplicate this asset and replace sprites with your own

![Mobile Icon Set](/input-icons-documentation/assets/images/mobile-icon-set.png)

After customizing your Icon Set:
1. Open the Setup Window (Tools – Input Icons - Input Icons Setup)
2. Navigate to the Customization section
3. Replace the default Icon Set with your own
4. Re-create the sprite asset containing your mobile sprites

## Mobile Support Components

To display mobile icons, you need both a base prompt component and a corresponding mobile override component:

| Base Component | Mobile Override | Purpose |
|----------------|-----------------|---------|
| II_SpritePrompt | II_SpritePromptMobileOverride | Override sprites for SpriteRenderers |
| II_ImagePrompt | II_ImagePromptMobileOverride | Override sprites for UI Images |
| II_TextPrompt | II_TextPromptMobileOverride | Replace `<inputaction>` tags with mobile sprites |

### How It Works

When the Base Prompt Component updates displayed sprites, it fires an event. The Mobile Support Component reacts by overriding sprites or `<inputaction>` tags with mobile-specific versions.

## Example Setup for Sprite Renderer

1. Add both `II_SpritePrompt` and `II_SpritePromptMobileOverride` to a GameObject
2. Configure the `II_SpritePrompt` component normally
3. In the `II_SpritePromptMobileOverride`:
   - Click "Add Sprite Override"
   - Reference the same SpriteRenderer used in `II_SpritePrompt`
   - Select which mobile sprite to display

![Mobile Sprite Override](/input-icons-documentation/assets/images/mobile-sprite-override.png)

## Example Setup for TextMeshPro

1. Add both `II_TextPrompt` and `II_TextPromptMobileOverride` to a GameObject
2. Configure the `II_TextPrompt` component normally
3. In the `II_TextPromptMobileOverride`:
   - Add mobile override entries
   - Each entry can replace a single `<inputaction>` tag with one or more mobile sprites

![Mobile Text Override](/input-icons-documentation/assets/images/mobile-text-override.png)