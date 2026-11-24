---
title: "Display Settings"
layout: default
nav_order: 7
parent: "Customization"
---

# Display Settings

The InputIconsManager provides options for how we want to display the input action bindings with style tags. You find them on the manager and in the Input Icons Settings window (Text & Style Tags). Except for tinting, they don’t affect Text Prompt components.

**Show All Available Input Option**: We can switch between showing only the first available binding, e.g. “WASD” or all available bindings, e.g. “WASD or Up Left Down Right” for a move action.

**Multiple Input Delimiter**: If we show all available options, we can define a delimiter between these actions. This delimiter can have TMPro tags for customization. The standard delimiter is “ \<size=80%\>or\</size\> “ and will therefore display a slightly smaller “or” between different bindings.

**Opening and Closing Tag**: Here we can add general styling options for the displayed icons. For example we can write \<size=120%\> in the opening tag and \</size\> into the closing tag to make all displayed icons a little bit bigger.

**Display Type**: input actions as sprites, text, or text in brackets.

**Text Display For Unbound Actions**: If we display bindings as Text or TextInBrackets, we can choose which text should be displayed for an unbound action.

**Text Display Language**: If we display bindings as Text or TextInBrackets, we can decide if we want to display this text in English or in System Language (the language currently used by the device, might produce very different results in text length and is generally not recommended).

**Action name output overrides**: If we use Text or TextInBrackets as the option to display input actions, we can override the text which would be displayed. For example it makes more sense to display \[MOUSE\] instead of \[POSITION\] for pointer controls.
