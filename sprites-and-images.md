---
title: "Sprite and Image Prompts"
layout: default
nav_order: 1
parent: "Displaying Bindings"
---

# Sprite and Image Prompts

To show current bindings in **SpriteRenderers or UI Images** we can add the **II_SpritePrompt or the II_ImagePrompt** script to an object in the scene. Both components function in a similar way and use a custom inspector to automatically change their appearance and functionality based on the chosen settings.

<img src="/input-icons-documentation/assets/images/guide/sprites-and-images-1.png" alt="Screenshot" width="254">

 

<img src="/input-icons-documentation/assets/images/guide/sprites-and-images-2.png" alt="Screenshot" width="261">

Searching by “Binding Index”

<table>
<colgroup>
<col style="width: 34%" />
<col style="width: 65%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Action Reference</strong></th>
<th>The action we want to display. The tool will search for bindings fitting the defined control scheme names defined in the setup window.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Searching by Binding Index</strong></td>
<td><p>The sliders below control which binding of the action to display.</p>
<p><strong>Simple, but beware</strong>: If you add/remove/move bindings in the Input Action Asset under that action, your displayed bindings might change.</p></td>
</tr>
<tr class="even">
<td><strong>Device Type</strong></td>
<td>The device to display. Can be “Keyboard And Mouse”, “Gamepad” or “Auto”. When Auto is selected, the displayed sprite will switch between keyboard and gamepad depending on which device is being used.</td>
</tr>
</tbody>
</table>

<img src="/input-icons-documentation/assets/images/guide/sprites-and-images-3.png" alt="Screenshot" width="303">

 

<img src="/input-icons-documentation/assets/images/guide/sprites-and-images-4.png" alt="Screenshot" width="296">

  
Searching by “Binding Type” Normal Mode

| **Search Binding By “Binding Type”** | This is generally the better option. It will give you additional fields depending on the input action you referenced.                                                                                                                                                                                |
|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Device Type**                      | The device to display. Can be “Keyboard And Mouse”, “Gamepad” or “Auto”. When Auto is selected, the displayed sprite will switch between keyboard and gamepad depending on which device is being used.                                                                                               |
| **Advanced Mode**                    | Switches between normal and advanced mode. While in most situations normal mode is enough, **advanced mode offers more flexibility** – especially when we need to display **composites** (like WASD) **and non composites** (like a gamepad stick)                                                   |
| **Composite Type (disabled)**        | In normal mode the composite type (composite or non-composite) gets determined automatically and will be composite if there is a composite binding assigned to the action. If keyboard and gamepad use different composite types (e.g. WADS and gamepad stick) you should use advanced mode instead. |
| **Keyboard Control Scheme Index**    | If the tool detects several possible keyboard bindings but with different control schemes, this field lets you choose which control scheme to display                                                                                                                                                |
| **Gamepad Control Scheme Index**     | Same as the option above but for gamepad control schemes.                                                                                                                                                                                                                                            |
| **Binding ID in List**               | If there are several possible bindings in the chosen control scheme, choose which one to display. E.g. you have defined WASD and the arrow keys for the keyboard control scheme. This lets you choose between W and the up arrow for example.                                                        |

<img src="/input-icons-documentation/assets/images/guide/sprites-and-images-5.png" alt="Screenshot" width="398">

Searching by “Binding Type” Advanced Mode

| **Control Scheme Index**    | Similar to the normal mode, you can select the control scheme index for keyboard and gamepad.                                                                                                                                                               |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Composite Types**         | This lets you choose between displaying a composite (like WASD) or non composite (like a gamepad stick or a single button) binding. The field gets automatically set in the OnValidate method if there is only one type available on the referenced action. |
| **Binding Types**           | If we chose a composite type in the field above, we can choose which direction (Up, Down, Left, Right, …) should be displayed.                                                                                                                              |
| **Available Binding Index** | If there are still several options left, we can choose which one we want to display (e.g. W or the Up Arrow)                                                                                                                                                |

General settings

| **Renderer**                     | The Sprite Renderer or UI Image component which will display the button prompt                                                                                                                      |
|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **(Optional) Keyboard Icon Set** | If the displayed sprite is a keyboard sprite and this value is set, it will always display the sprite of the selected icon set instead of displaying the sprite of the currently used gamepad type. |
| **(Optional) Gamepad Icon Set**  | Same as the option above, but for gamepads                                                                                                                                                          |

<img src="/input-icons-documentation/assets/images/guide/sprites-and-images-6.png" alt="Screenshot" width="216">

