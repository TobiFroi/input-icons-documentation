---
title: "Interaction Prompts"
layout: default
nav_order: 5
has_children: true
---

# Interaction Prompts

Interaction prompts show the key or button of an action, react when the player uses it and call events when the interaction is **started**, **completed**, **canceled** or **failed**. Typical uses are “Hold \[E\] to open”, “Mash \[A\] to break free” or “Press when the ring closes”. There are four types:

- **II_TapPrompt**: a single press (completes on press, or on release).

- **II_HoldPrompt**: the action has to be held, a ring around the icon fills up. Can also be used to charge and release.

- **II_MashPrompt**: the action has to be pressed repeatedly, the ring drains when the player stops. Optionally alternating between two actions.

- **II_TimingPrompt**: an approach ring shrinks onto the prompt, the player has to press at the right moment (Perfect, Good or Missed).

The example scenes **2_1 Interaction Prompts**, **2_2 Prompt Sequences** and **2_3 Tutorials and Hints** show all components of this chapter in use.

## Using the Prompt Prefabs

Each type has a prefab in **Input Icons/Prefabs/InteractionPrompts**: **II_UI_Tap_Prompt**, **II_UI_Hold_Prompt**, **II_UI_Mash_Prompt** and **II_UI_Timing_Prompt**. We recommend duplicating the prefab you need and using the duplicate in your project, so you can change its look without your changes being overwritten by updates of Input Icons.

The prefabs are about 1 unit wide at scale 1, which fits a **World Space canvas** (e.g. a canvas as a child of a chest, so the prompt moves with it). In a Screen Space canvas, scale the parent of the prompt up (e.g. to 100) or change the size of the prefab.

Each prompt has an **Image Prompt** that shows the icon. Set the action on the interaction prompt: with **Sync Image Prompt** enabled (default), the Image Prompt shows the same action automatically, and the inspector previews the keyboard and gamepad icons.

## Settings of All Interaction Prompts

- **Action**: the action to use. **Composite Part**: only a part of a composite action counts, e.g. Up of Move (WASD, arrow keys, D-Pad and the stick's up direction).

- **Additional Actions**: actions that have to be held at the same time (chords like \[Space\] + \[S\]). The icons are shown with a “+”. For rebindable chords, an action with a One Modifier composite works as well.

- **Use Unscaled Time** (e.g. for pause menus and slow motion) and **Pause When Time Scale Is Zero**.

- **After Completed**: Nothing (can be used again if **Repeatable**, after the **Reset Delay**), **Disable** or **Destroy** a target, e.g. for things that can only be done once.

- **Display**: the Progress Image (ring), an optional Slider, idle objects (e.g. arrows shown while nothing is pressed), a pulse, a press effect, the pressed sprite of the icon set while pressed, and an optional Timer Image.

- **Events**: On Started, On Completed, On Canceled and On Failed (also as C# events). Your code can also call **SetProgress**, **Complete** and **ResetProgress**.

The prompts only react while they are active. Hide them when the player can’t interact, or use an [II_Interactable](/input-icons-documentation/interactables).

## Tap Prompt

**Complete On**: Press, or Release. With Release and a **Max Tap Duration**, holding too long cancels the tap, so the same button can also be used for a Hold Prompt. For repeatable taps, the Reset Delay works as a cooldown.

## Hold Prompt

- **Progress Source**: **Hold Interaction** uses the duration of the action’s Hold or Slow Tap interaction (actions without one use Hold Duration), **Hold Duration** uses the seconds set on the prompt, **Manual** lets your code set the progress (e.g. if you already have your own hold logic).

- **Release Speed**: how fast the ring drains when released early.

- **Release Mode**: **Complete When Full** (a normal hold), **Release In Sweet Spot** (charge and release: releasing inside the sweet spot completes it, outside fails it; the sweet spot is shown on the ring) or **Release Any Time** (completes on release; **Charge** and **On Released** give the charge, e.g. for throw strength).

## Mash Prompt

- **Presses Needed**, **Drain Per Second** and **Drain Delay** (how fast the progress is lost when the player stops), and an optional **Time Limit**. The inspector shows how many presses per second the player needs.

- **Alternate Action**: the action and the alternate action have to be pressed in turns (e.g. left and right for rowing). Both icons are shown, the next one is highlighted.

## Timing Prompt

- **Approach Duration**: the seconds until the approach ring reaches the prompt (the perfect moment), after an optional **Start Delay**.

- The perfect moment is when the approach ring covers the **Window Indicator** (the thin target ring). With **Highlight Window**, the target ring lights up while a press counts.

- **Perfect Window** and **Good Window**: seconds before and after the perfect moment. **Early Press Fails**: pressing too early fails it (otherwise early presses are ignored).

- **On Result** is called with Perfect, Good or Missed. **LastResult** and **LastOffset** give the result in code.
