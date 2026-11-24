---
title: "The Setup Wizard"
layout: default
nav_order: 1
parent: "Getting Started"
---

# The Setup Wizard

On the Welcome page, choose between the **Quick Setup** (recommended for most projects) and the **Advanced Setup**, which shows all options, e.g. font assets, texture compression, text display settings and memory optimization. You can switch between the two at any time with “Show advanced options” in the sidebar.

Below, the **Requirements** panel checks what Input Icons needs in your project and offers a button for anything missing:

- **Input System active**: “Active Input Handling” in the Player settings must be “Input System Package (New)” or “Both”.

- **TextMesh Pro resources**: imports the TMP Essential Resources, or the TMP Examples & Extras if the default style sheet is still missing (needed for style tags).

- **2D Sprite package**: installs the package, which is needed to create the sprite assets for texts. Input Icons also asks once after importing if it is missing.

The wizard remembers your choices for each project (in the UserSettings folder of the project), so you can close it and continue later.

## Your Input

The wizard lists the Input Action Assets of your project. Assets that are very likely the ones your game uses are preselected, e.g. the project-wide actions asset or assets used in the scenes of your build settings. Check the assets your game uses.

The example Input Action Assets of Input Icons are selected too, so the example scenes work right away. Uncheck them if you don’t need the examples.

Below, the control schemes of the selected assets are sorted into keyboard & mouse and gamepad schemes, based on the devices they require. You can move a scheme to the other list or ignore it with its dropdown. Schemes that are already set on the Input Icons Manager keep their position, new ones are added after them, so components in your scenes keep showing the same schemes.

<img src="/input-icons-documentation/assets/images/guide/setup-wizard-1.png" alt="Screenshot" width="455">

## Your Look

Choose the icon style for keyboard & mouse and for each kind of gamepad (Xbox, PlayStation 5/4/3, Nintendo Switch and a fallback for other gamepads). Each card shows a few sample sprites of the icon set. By default, each platform shows the icon sets made for it. With “Use another icon set …” you can choose any gamepad icon set, e.g. PS4 icons for PS5 controllers. If you always want to show the same icons, no matter which controller is connected, enable “Use the same icons for every gamepad”.

Icon sets are grouped by their folder, e.g. “Vol 1” and “Vol 2” of the sprite packs or a folder with your own icon sets. Each folder starts a new row. In the advanced options, you can also choose an icon set for touch controls on mobile devices (shown with the mobile override components, e.g. II_ImagePromptMobileOverride).

“Animated prompts” creates animated sprite assets for icon sets with pressed sprites, so prompts can alternate between the normal and the pressed sprite of a key (see section [Animated Prompts](/input-icons-documentation/animated-prompts)).

“Sprite Quality at Small Sizes” (optional) lets you turn on mipmaps for the created sprite assets and for the icon sprites of your chosen icon sets, so icons stay smooth when they are shown smaller than their original size (see section [Quality Settings for Small Sprites](/input-icons-documentation/small-sprites)).

<img src="/input-icons-documentation/assets/images/guide/setup-wizard-2.png" alt="Screenshot" width="604">

## Finish

The Finish page shows a summary of your settings. The “Icons in Texts” section explains the two ways to show icons in TextMesh Pro texts and has two options:

- **Create or update the sprite assets** (needed for both ways): the sprite assets for texts are created from your icon sets. You can turn this off when you run the setup again and the sprite assets already exist, e.g. to only add a new Input Action Asset. A status line shows whether sprite assets are missing.

- **Add style tags to the TextMesh Pro style sheet** (style tags only): only needed if you want to write tags like \<style=Player/Jump\> into your texts. Text Prompt, Image Prompt and Sprite Prompt components work without them (see section [Displaying Bindings in TMPro](/input-icons-documentation/text-prompts)). The setup also turns on “Automatic style sheet updates”, so the style tags switch between keyboard and gamepad icons.

If TextMesh Pro has no default style sheet yet, the Finish page offers to import the missing TextMesh Pro resources. If some style tags are missing after the setup, the wizard adds them again once Unity has finished compiling.

Press **Set up Input Icons** and the wizard applies everything: it assigns your Input Action Assets, control schemes and icon sets, creates the TextMesh Pro sprite assets and adds the style tags (if selected). If your active Input Icons Manager and Configurator are still the ones inside the Input Icons folder, the wizard first creates your own copies in “Assets/TobiFroi/InputIconsSettings/Resources/InputIcons”, so updates of Input Icons never overwrite your settings. Unity may recompile once after the setup.

All settings of the advanced setup can be changed later in the Input Icons Settings window (see section [Input Icons Settings Window](/input-icons-documentation/settings-window)).

After the setup, open **Example Scene 0 (Quick Check)** with “Show example scenes”. It shows all prompt types side by side, static and animated, lights up a row when you use its action, and checks your setup while the scene runs. Press Pause (Esc or Start) to open the menu and rebind your controls.

In the editor, prompts in an open scene can stay blank until you start the scene once. In Play Mode and in builds they always show the right icons.

<img src="/input-icons-documentation/assets/images/guide/setup-wizard-3.png" alt="Screenshot" width="564">

## Project Status

After the setup, the wizard opens on the Project Status page. It checks your setup and offers a fix for common issues, for example:

- your settings are still inside the Input Icons folder

- new control schemes in your Input Action Assets that the manager doesn’t know yet (they are added after the existing ones)

- missing or outdated sprite assets, e.g. after adding pressed sprites

- a style sheet that is out of date after you added or renamed actions

- style tags that don’t switch between keyboard and gamepad icons, because “Automatic style sheet updates” is off

It is a good idea to open this page after changing your Input Action Assets. The page also shows the active Input Icons Manager and Configurator with buttons to select them. Make changes on these assets: other managers and configurators in the project are not used, and their inspector shows a warning.

The **Maintenance** section below the checks has tools you might need now and then:

- **Re-create sprite assets**: e.g. after you changed sprites of your icon sets

- **Restore icon set backups**: undoes the memory optimization (shown if backups exist, see section [Memory Optimization](/input-icons-documentation/memory-optimization))

- **Remove Input Icons style tags**: removes all entries Input Icons added to the default TextMesh Pro style sheet, e.g. to clean it up. “Update style sheet” or the setup add them again.

<img src="/input-icons-documentation/assets/images/guide/setup-wizard-4.png" alt="Screenshot" width="604">

## Help & Support

This page links the documentation, the video tutorials, the Unity forum and the support email, and lists the main components of Input Icons. Click a script to find it in the Project window.
