---
title: "Button Hint Bar"
layout: default
nav_order: 4
parent: "Interaction Prompts"
---

# Button Hint Bar

**II_ButtonHintBar** shows a row of hints like “\[A\] Select \[B\] Back \[Y\] Details”, e.g. at the bottom of a menu. The icons follow the device in use and the rebinds.

- The hints (action, optional composite part, label) are stored on the component, or in an **II_ButtonHintSetSO** asset (Create \> Input Icons \> Button Hint Set) that can be used in several scenes.

- Switch the hints per screen or context with **SetHints(set)** (e.g. from a UnityEvent), **SetHints(list)** or **Clear()**.

- **Hide Disabled Actions**: hints of disabled actions are hidden.

- The bar builds the hints with its look settings (icon size, font, colors, spacing), or copies a **Hint Template** of yours (an inactive object with an II_ImagePrompt and a TMP text).
