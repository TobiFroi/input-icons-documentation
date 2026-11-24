---
title: "Upgrading To Unity 6"
layout: default
nav_order: 5
parent: "Getting Started"
---

# Upgrading To Unity 6

When upgrading your project to Unity 6, you'll need to make a few adjustments to ensure Input Icons continues to work correctly with the new integrated TextMeshPro system.

Before starting, locate your TextMeshPro default stylesheet in the TextMeshPro/Resources folder and create a backup copy. This ensures you can restore your settings if needed.

Follow these steps:

1.  Delete the default TextMeshPro stylesheet from your TextMeshPro/Resources folder

2.  Go to Window \> TextMeshPro \> Import TMP Essential Resources to get the Unity 6 compatible version

3.  Reconfigure your Input Icons setup

Unity 6 comes with TextMeshPro integrated by default, rather than as a package manager asset. This change requires the above steps to ensure proper compatibility between Input Icons and the new TextMeshPro implementation.

After completing these steps, Input Icons should work as expected in your Unity 6 project.
