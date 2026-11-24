---
title: "Updating From An Earlier Version"
layout: default
nav_order: 4
parent: "Getting Started"
---

# Updating From An Earlier Version

When updating, it's essential to have a backup prepared in case of any unforeseen issues.

**Folder location:** Since version 4.2.0, new installations of Input Icons are placed in “Assets/TobiFroi/InputIcons”. Projects that already contain Input Icons keep their “Assets/InputIcons” folder, the update gets imported there and you don’t need to move anything. If you want to move the folder, do so inside the Unity Editor (Project window), not in the file explorer. The paths in this guide use the new location.

**Steam:** Since version 4.2.0, Input Icons does not connect to Steam on its own anymore. If your game uses Steamworks.NET or Facepunch Steamworks, see chapter [Steam Input Troubleshooting](/input-icons-documentation/steam).

**Setup window:** Since version 5.0.0, Input Icons comes with a new setup wizard (Tools → Input Icons → Input Icons Setup Wizard) and an Input Icons Settings window. Existing projects keep working without changes and don’t need to be set up again. The classic setup window is still available. When you run the new setup, it creates your own copies of the Input Icons Manager and Configurator in “Assets/TobiFroi/InputIconsSettings/Resources/InputIcons” (if your active ones are still the ones inside the Input Icons folder), so future updates can’t overwrite your settings. If an earlier setup created them in “Assets/InputIconsSettings”, they keep working there; you can move that folder into “Assets/TobiFroi” if you like, as long as the files stay in a Resources/InputIcons folder.

**Sprite assets:** After updating to 5.0.0, create the sprite assets again (setup wizard, or Project Status → Re-create sprite assets), so they include the new pressed sprites.

Upgrading to a new version may result in your settings being reset to default values. To prevent your settings on the manager and configurator from being overwritten during an update process, we can first duplicate these two assets, rename them and use them instead. Since version 3.2.12 it is possible to duplicate them directly through the setup window (within the Base Setup section). After the duplication, they should have “Is Actual Manager” or “Is Actual Configurator” enabled in the inspector of each asset.

<img src="/input-icons-documentation/assets/images/guide/updating-1.png" alt="Screenshot" width="278">

<img src="/input-icons-documentation/assets/images/guide/updating-2.png" alt="Screenshot" width="278">

**If you don’t have your own duplicated versions:**

Any modifications made to the InputIconManager and the InputIconConfigurator could potentially be lost and may need to be recreated. If you haven't made extensive changes, updating the references in the setup window (Tools → Input Icons → Input Icons Setup) should be sufficient. However, it's advisable to also inspect the Input Icons Manager (located in Assets/TobiFroi/InputIcons/Resources/InputIcons/) for a comprehensive overview.

<img src="/input-icons-documentation/assets/images/guide/updating-3.png" alt="Screenshot" width="210">

If you've made alterations to the icon sets that include the displayed sprites, consider creating a copy of them before the update. This allows you to reuse your custom icon sets after the update. Make sure to reassign your personalized icon sets to the InputIconSetConfigurator.

<img src="/input-icons-documentation/assets/images/guide/updating-4.png" alt="Screenshot" width="338">

<img src="/input-icons-documentation/assets/images/guide/updating-5.png" alt="Screenshot" width="344">

