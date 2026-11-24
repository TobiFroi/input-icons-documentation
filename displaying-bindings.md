---
title: "Displaying Bindings"
layout: default
nav_order: 3
has_children: true
---

# Displaying Bindings

Depending on where you want to show the bindings, there are several ways to display them. All of them update by themselves when the player switches devices or rebinds an action.

| | Sprite Renderers and UI Images | TextMesh Pro with components | TextMesh Pro with style tags |
|---|---|---|---|
| **Components** | II_SpritePrompt, II_ImagePrompt (and their local multiplayer versions) | II_TextPrompt, II_LocalMultiplayerTextPrompt | No components needed |
| **Requirements** | Matching control scheme names (Input Action Assets and the setup) | Sprite assets for TextMesh Pro (created by the setup wizard) | The styles added to the default style sheet (setup wizard) |
| **More information** | [Sprite and Image Prompts](/input-icons-documentation/sprites-and-images) | [Text Prompts](/input-icons-documentation/text-prompts) | [Style Tags](/input-icons-documentation/style-tags) |

The older components II_SpritePromptBehaviour and II_ImagePromptBehaviour are deprecated. Use II_SpritePrompt and II_ImagePrompt instead.

For prompts the player interacts with (hold, mash, timing) see [Interaction Prompts](/input-icons-documentation/interaction-prompts). For UI Toolkit see [UI Toolkit](/input-icons-documentation/ui-toolkit).
