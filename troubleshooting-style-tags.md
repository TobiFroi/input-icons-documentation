---
title: "TextMeshPro Style Tags"
layout: default
nav_order: 1
parent: "Troubleshooting"
---

# TextMeshPro Style Tags

**Have our Sprite Assets been created correctly and does the TMPro Default Style Sheet contain our actions?**

<img src="/input-icons-documentation/assets/images/guide/troubleshooting-style-tags-1.png" alt="Screenshot" width="324">

- **Sprite Assets**: In “Assets/TextMesh Pro/Resources/Sprite Assets/” we should find assets containing the sprites of the keys we want to display. It is important that these assets have the same names as the Icon Sets in “Assets/TobiFroi/InputIcons/Icon Sets/”.

- **TMPro Default Style Sheet**: The Default Style Sheet should somewhere contain the actions defined in our Input Action Assets. Check the style sheet in “Assets/TextMesh Pro/Resources/Style Sheets/”  

<img src="/input-icons-documentation/assets/images/guide/troubleshooting-style-tags-1.png" alt="Screenshot" width="154">

<img src="/input-icons-documentation/assets/images/guide/troubleshooting-style-tags-2.png" alt="Screenshot" width="315">
  **Special case**: The styles were added correctly, but **the styles disappear once we restart Unity** … the Default Style Sheet sometimes won’t save the changes. A workaround is to make a small change manually in any of the fields of the style sheet and then undo the change. This seems to work and the changes will be saved.

<img src="/input-icons-documentation/assets/images/guide/troubleshooting-style-tags-3.png" alt="Screenshot" width="306">

**If we don’t see any input icons make sure that:**

- The “**Used Input Action Assets**” list contains all Input Action Assets we use and we have updated the Default Style Sheet with all changes we made to the Input Action Asset(s).

- All our Input Action Assets have **control schemes for keyboard/gamepad** and their names are **equal to** the ones set in the Input Icons Setup or in the **Input Icons Manager** respectively.

- The **control schemes** of our Input Action Assets have **devices** added to them (see chapter [Adding Devices To Control Schemes](/input-icons-documentation/input-action-asset#assigning-devices-to-control-schemes))

<img src="/input-icons-documentation/assets/images/guide/input-action-asset-6.png" alt="Screenshot" width="211">

**Icons are shown, but don’t get updated when a different device is used:**

- Enable “Automatic style sheet updates” in the Input Icons Settings window (Text & Style Tags), or use the fix on the Project Status page of the setup wizard

<img src="/input-icons-documentation/assets/images/guide/troubleshooting-style-tags-4.png" alt="Screenshot" width="272">

- Check section [Keyboard And Gamepad Support](/input-icons-documentation/devices)

- In some Unity versions, a **Event System** needs to be in the scene as the manager subscribes to events of the input system.
