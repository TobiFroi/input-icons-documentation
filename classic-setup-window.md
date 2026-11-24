---
title: "Classic Setup Window"
layout: default
nav_order: 2
parent: "Getting Started"
---

# Classic Setup Window

The classic setup window is still available (Tools → Input Icons → Input Icons Setup). It offers the same setup steps on separate tabs, plus some customization tools like restoring the backups of the memory optimization.

Open the classic setup window from the toolbar: **Tools → Input Icons → Input Icons Setup**

In the setup you find the necessary fields to configure Input Icons. Some customization options are also available in this window, but you might also want to check out the InputIconsManager and the InputIconSetConfigurator. More on that later.

The setup window is split into two parts, namely the Base Setup and the Setup for TextMeshPro.

- The **Base Setup** is enough to display dynamic bindings with SpriteRenderers and UI Images

- In the **Setup for TextMeshPro** we will create TMP_SpriteAssets for each device and add a bunch of entries to the default TMP Style Sheet. This will allow us to also display dynamic bindings along with other text. (If you don’t need this feature, you might want to skip this part as the created TMP_SpriteAssets can take up 10-50Mb of space which you could otherwise save)

<img src="/input-icons-documentation/assets/images/guide/classic-setup-window-1.png" alt="Screenshot" width="604">

## The Base Setup (for Sprites and UI Images)

With the setup window open (**Tools/Input Icons/Input Icons Setup**) all we need to do is to define the control scheme names we want to use in our Input Action Assets (if you need help with that, have a look at: [Setting Up The Input Action Asset](/input-icons-documentation/input-action-asset)). We have separate lists for keyboard and gamepad control schemes. This way the tool can better differentiate between these two device types.

<img src="/input-icons-documentation/assets/images/guide/updating-4.png" alt="Screenshot" width="332">

With the control scheme names set up you should already be able to display bindings with sprites and images using the scripts which come with this tool.

Note: You can define as many control scheme names as you want but I recommend using as few as possible and to reuse them in your Input Action Assets if you have several.

If you want to let users rebind their keys, you can fill the Used Action Assets list with your asset(s) and the tool will automatically save/load the overridden bindings when necessary.

With this done you can display the actions of your Input Action Assets with SpriteRenderers and UI Images (have a look at: [Displaying Bindings with Sprites and Images](/input-icons-documentation/sprites-and-images))

## The Setup for TextMeshPro

To display bindings in TMPro texts, we use the sprite-tag to display our key sprites along with other text. But first we need to create TMP_SpriteAssets holding all sprites we will need.

If you moved the TextMeshPro folder to a different location, you need to update the path values before creating the TMP_SpriteAssets.

<img src="/input-icons-documentation/assets/images/guide/classic-setup-window-2.png" alt="Screenshot" width="357">

Enable the “Use fonts” checkbox, if you also want the ability to display bindings as a special SDF font. This is a font which holds symbols for each key/button instead of letters of the alphabet. The SDF font has the advantage that the edges will look sharp at all sizes while sprites can become blurry at a large size. But unfortunately they don’t have much detail.

After pressing the button in this setup area, the TMP_SpriteAssets will be created (and if we selected the “Use fonts” checkbox above, the SDF font assets will also be created. You might need to recompile or enter play mode for the new Sprite Assets to take effect.

Have a look at [Displaying Bindings in TMPro](/input-icons-documentation/text-prompts) to see how you can display bindings along other text.

## (optional) The Setup for TextMeshPro style tag

After completing the Base Setup and creating the TMP_SpriteAssets in the Setup for TextMeshPro we can also decide to make use of the style tag of TMPro. The advantage of displaying bindings with the style tag is that we don’t need any components and that this solution might work better in combination with other systems which also make use of tags.

However, this method also comes with limitations. Some of them are:

- Multiple device types can not be displayed at the same time

- Only the first control scheme in the control scheme list(s) can be displayed

- The option to display all available bindings for actions is global and affects all texts at the same time

- No inherent support for local multiplayer

- When adding actions or renaming actions, you need to do the setup below again to reflect the changes

<img src="/input-icons-documentation/assets/images/guide/classic-setup-window-3.png" alt="Screenshot" width="291">

Here is what we need to do in order to make the style tags work

- Create our Input Action Asset(s) and assign them to the “Used Action Assets” list in the setup window. Also define the same control scheme names we defined in the Base Setup (on how to do that look at: [Setting Up The Input Action Asset](/input-icons-documentation/input-action-asset))

- (optional) You can check beforehand if your actions got detected correctly by opening the style list window: **Tools – Input Icons – Input Icons TMPro Style List Window**

- Generate Style Sheet entries via either the Quick Setup section or the Manual Setup section

<img src="/input-icons-documentation/assets/images/guide/classic-setup-window-4.png" alt="Screenshot" width="479">

And that's it! For more information on how to display bindings with the style tag look at: [Displaying Bindings in TMPro using the style tag](/input-icons-documentation/style-tags)
