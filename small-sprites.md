---
title: "Quality for Small Sprites"
layout: default
nav_order: 4
parent: "Customization"
---

# Quality for Small Sprites

<img src="/input-icons-documentation/assets/images/guide/small-sprites-1.png" alt="Screenshot" width="205">

When sprites are shown smaller than their original size (the sprites of Input Icons are 256 x 256 pixels), there are not enough pixels on the screen to show all of their details. Thin lines and edges can then look jagged or flicker, e.g. for small prompts in the UI or for prompts in the game world.

**Mipmaps** solve this: Unity creates smaller, pre-smoothed copies of a texture (128, 64, 32 pixels, …) and automatically uses the one that fits the size on screen. They cost about a third more texture memory. At full size, sprites look the same.

In the setup wizard, on the page **Your Look**, the panel **Sprite Quality at Small Sizes** has two options:

**Mipmaps for icons in texts:** for the sprite assets created for TextMesh Pro (also used by the UI Toolkit extension). This is on by default. You can also change it in the Input Icons Settings window under Assets. It takes effect when the sprite assets are created or updated.

**Mipmaps for the icon sprites:** changes the import settings of the sprite textures of your chosen icon sets, which are used by II_ImagePrompt, II_SpritePrompt and the other Image and Sprite Renderer prompts. Your sprites keep their current import settings unless you change this option.

You can also do this manually for any texture: select it, enable “**Generate Mip Maps**” in the Advanced section of the import settings and hit Apply. The Mip Map Filter “Kaiser” keeps small sprites slightly sharper than “Box”.

**Note:** updating Input Icons can reset the import settings of the included sprites to the ones of the package. If you changed them, apply your settings again after an update, e.g. with the setup wizard.

<img src="/input-icons-documentation/assets/images/guide/small-sprites-2.png" alt="Screenshot" width="94">

<img src="/input-icons-documentation/assets/images/guide/small-sprites-3.png" alt="Screenshot" width="94">

The sprite assets created by Input Icons have used mipmaps by default since version 1.4.x. The setup wizard now lets you turn this off.
