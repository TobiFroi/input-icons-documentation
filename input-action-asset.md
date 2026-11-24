---
title: "Setting Up The Input Action Asset"
layout: default
nav_order: 3
parent: "Getting Started"
---

# Setting Up The Input Action Asset

Our Input Action Assets (requires Input System 1.2.0 or higher … Window Package Manager) need control schemes for keyboard and gamepads (if we want to provide support for both). We have to add devices to the control schemes so the Input Icons Manager can decide which icons to display whenever we switch to gamepad or keyboard.

## Verifying Control Scheme Names

Let’s be sure that the Input Action Asset has **control schemes** set up **for keyboard and gamepad** control. Or only one of them, depending which device(s) we want to support.

**IMPORTANT**: I noticed, changing the control schemes on the Input Action Assets does not always yield immediate results for the displayed sprites, even after saving the Input Action Asset. Often, only a domain reload will update the sprites accordingly (just enter Play Mode with “Enter Play Mode Options” disabled in Project Settings Editor Enter Play Mode Settings)

<img src="/input-icons-documentation/assets/images/guide/input-action-asset-1.png" alt="Screenshot" width="396">

The InputIconsManager needs to know about these names. So if you have not already, fill in the names in the required lists in the setup window (Tools Input Icons Input Icons Setup) or in the Input Icons Manager scriptable object.

<img src="/input-icons-documentation/assets/images/guide/input-action-asset-2.png" alt="Screenshot" width="257">

**Control scheme positions and names:** Prompts and rebind components select a control scheme by its position in the manager’s keyboard or gamepad list. Since version 5.0.0 they also remember the name of the selected scheme, so adding, removing or reordering schemes in these lists doesn’t change what they show. In their inspectors, a dropdown with the scheme names is shown next to the index slider or the +/- buttons, so you can either try the positions and watch the preview, or pick a scheme by its name directly.

Neither the setup wizard nor the Project Status page reorder or remove schemes on the manager. New schemes are always added after the existing ones.

## Assigning Devices To Control Schemes

We should now have two control schemes. One for gamepads, one for keyboard and mouse. We need to add devices to these control schemes in order for the manager to know which icons to display when the user switches to a different device.

![](media/media/image17.png) 

<img src="/input-icons-documentation/assets/images/guide/input-action-asset-3.png" alt="Screenshot" width="217">

 

<img src="/input-icons-documentation/assets/images/guide/input-action-asset-4.png" alt="Screenshot" width="199">

<img src="/input-icons-documentation/assets/images/guide/input-action-asset-5.png" alt="Screenshot" width="221">

 

<img src="/input-icons-documentation/assets/images/guide/input-action-asset-6.png" alt="Screenshot" width="226">

