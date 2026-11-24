---
title: "Animated Prompts"
layout: default
nav_order: 4
---

# Animated Prompts

Prompts can alternate between the normal sprite of a key and a “pressed” version of it, e.g. a mouse with and without the left button highlighted. This draws attention to a prompt and makes it clear that a button needs to be pressed. Animation is optional and only applies to keys that have a pressed sprite. If a player rebinds an action or switches devices, the animation follows the new binding; keys without a pressed sprite stay static.

<img src="/input-icons-documentation/assets/images/guide/animated-prompts-1.png" alt="Screenshot" width="205">

## Pressed Sprites

Each key and button of an icon set can have an optional pressed sprite, next to its normal sprite. To assign them quickly, export the pressed sprites into a folder and use **Automatically apply pressed sprites of folder …** in the icon set’s inspector. Sprites are matched by name: either named like the normal sprite followed by “\_pressed”, or with exactly the same name as the normal sprite (e.g. exported into a separate “Pressed” folder). You can also assign them by hand, including for custom context icons.

<img src="/input-icons-documentation/assets/images/guide/animated-prompts-2.png" alt="Screenshot" width="205">

## Animating Sprite and Image Prompts

Enable **Animate** on each entry (action reference) of a Sprite Prompt, Image Prompt or their local multiplayer versions that should animate; the other entries of the same prompt stay static. “Animation Interval” at the top of the component sets how long the normal and the pressed sprite are shown each, for all animated entries of that prompt. Prompts with the same interval switch in sync, and they keep animating while the game is paused (Time.timeScale = 0). Sprite and Image Prompts don’t need any sprite assets for this.

## Animating Text Prompts

On Text Prompts, **Animate** is set per action, so a text can animate one action and show another one statically. The interval is set on the component. Text Prompts use TextMesh Pro’s sprite animation, which needs an animated sprite asset for the icon set (see below). TextMesh Pro animates in whole frames per second, so the interval gets rounded (0.5 seconds = 2 frames per second), and animated texts don’t run in sync with Sprite and Image Prompts.

**Optional: in sync with Sprite and Image Prompts (advanced).** Set **II_TextSpriteAnimator.Enabled = true** to let Input Icons switch the sprites of texts with the same clock as Sprite and Image Prompts (then the interval isn’t rounded either). Set it before the style tags are created and before texts are shown, e.g. in a method with **\[InitializeOnLoadMethod\]** in an Editor script and one with **\[RuntimeInitializeOnLoadMethod(RuntimeInitializeLoadType.BeforeSceneLoad)\]**, and add the styles to the style sheet again afterwards. The animated sprites are then marked with a TextMesh Pro link (ID “ii_anim”), so don’t place them inside your own \<link\> tags: TextMesh Pro doesn’t support links inside links. This is why it is off by default.

## Animated Style Tags

If “Create animated style tags” is enabled (setup wizard, Input Icons Settings window or Input Icons Manager), every style sheet entry gets an animated counterpart named like the entry plus “\_anim”, e.g. \<style=Player/Jump_anim\>. The Input Icons TMPro Style List Window shows these tags too. Add the styles to the style sheet again after changing this setting.

## Animated Sprite Assets

Animated texts need an animated TextMesh Pro sprite asset for each icon set, named like the icon set plus “\_Animated”. It contains the normal and the pressed sprites as pairs, followed by all other sprites of the icon set. The setup wizard creates them for icon sets with pressed sprites if “Animated prompts” is enabled. You can also enable “Also create animated sprite asset” next to the “Pack to Sprite Asset” button of an icon set. The normal sprite assets are not changed.

**Saving memory:** If you animate many texts, enable “Use animated sprite assets for all texts”. Then static texts use the animated sprite assets too, so the normal sprite assets are never loaded by texts. Update the style sheet afterwards. If you use Addressables, assign the animated sprite assets to the TMPSpriteAssetLoader instead of the normal ones. With this setting, the memory optimization also makes icon sets use the animated atlas (see section [Memory Optimization](/input-icons-documentation/memory-optimization)).

## Tip: “Hold” Badges

To show that a button needs to be held, create an icon set with sprites that include a badge (e.g. an arrow) and assign it to the optional Keyboard/Gamepad Icon Set override fields of the prompts that need it. Other prompts keep using the normal icon sets.

To show the progress of holding as well, use a **Hold Prompt** (see [Interaction Prompts](/input-icons-documentation/interaction-prompts)).
