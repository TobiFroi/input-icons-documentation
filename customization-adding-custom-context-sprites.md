---

title: Adding Custom Context Sprites
layout: default
parent: Customization
nav_order: 2
---

# Adding Custom Context Sprites

The preset Input Icon Sets in the package (`Assets/InputIcons/`) already define sprites for all common input keys, gamepad buttons, and joysticks. However, additional input controls can be added to the **Custom Contexts** list in the Input Icon Sets.

## Finding the Input Binding String

To add a new binding, you need the **input binding string** and a display icon.

1. Use the script **`II_UITextDisplayAllActions`** in the example folder.
2. Attach it to a **TextMeshProUGUI** object to display current input bindings.
3. Use a **rebind button** to override the current binding with the one you want to add.
4. The input binding string will be displayed in brackets.
   - Example: The **mouse wheel** binding string is `Scroll`.

## Applying Custom Context Sprites

Whenever changes are made to an **Input Icon Set**, a **new Sprite Asset** must be created. Otherwise, the desired sprite will not be available for TextMeshPro text rendering.
