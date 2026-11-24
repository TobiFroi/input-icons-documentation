---
title: "Interactables"
layout: default
nav_order: 1
parent: "Interaction Prompts"
---

# Interactables

**II_Interactable** shows a prompt while a player is in range and calls its own events when the prompt is completed. That way the logic of what happens (opening a chest, a door, a vending machine dropping a snack) sits on your object, and a chest prefab can always react the same way, whichever prompt it uses.

- **Prompt**: the interaction prompt (empty: the first one in the children). **Prompt Root**: the object shown and hidden, e.g. the canvas of the prompt.

- **Detect Range**: trigger colliders (2D or 3D) on the same GameObject detect players. Triggers on child objects need an **II_InteractableTrigger**. Triggers only fire if the player or the object has a Rigidbody.

- **Filter**: which objects count as players: **Tag**, **Layer** or **Component** (a component name like PlayerHealth on the object, its parents or children).

- Without range detection, call **SetInRange(true/false, player)** from your own code. There are also **ShowPrompt**, **HidePrompt** and **ResetInteractable**.

- **Single Use**: after it was completed once, the prompt is hidden and the interactable doesn’t react anymore (e.g. a chest).

- **Events**: On Started, On Completed, On Canceled, On Failed, On Entered Range and On Left Range.

- **Local multiplayer**: with **Use Player Input Of Interactor**, the prompt listens to the actions of the player in range (their PlayerInput).
