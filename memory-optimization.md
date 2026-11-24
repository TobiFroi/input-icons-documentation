---
title: "Memory Optimization"
layout: default
nav_order: 5
parent: "Customization"
---

# Memory Optimization

Input Icons creates sprite atlases for TextMeshPro text while also maintaining references to individual sprites for UI Images and Sprite Renderers. This can result in duplicate sprite references in memory.

## Optimizing Memory Usage

To reduce memory usage, you can configure your Icon Sets to reference sprites directly from the TextMeshPro sprite atlas:

1.  Complete the TextMeshPro setup first (section 1.4)

2.  Go to **Tools → Input Icons → Input Icons Setup → TextMeshPro Setup**

3.  Scroll to the **Memory Optimization** section

4.  Enable "Create backups of Icon Sets" (recommended)

5.  Click "Optimize Memory Usage" and confirm when prompted

After optimization, both your TextMeshPro text and UI components will use the same sprite references, potentially reducing memory usage in your game.

The memory optimization is also available as an option on the Finish page of the advanced setup in the setup wizard.

If “Use animated sprite assets for all texts” is enabled, icon sets with an animated sprite asset reference the animated atlas instead, for their normal and their pressed sprites. Then only the animated atlas is loaded.

## Restoring From Backups

If you need to modify the original sprites or revert the optimization:

1.  Open the Project Status page of the setup wizard (or Tools → Input Icons → Input Icons Setup → Customization in the classic setup window)

2.  Find “Restore icon set backups” in the Maintenance section (or the Restore from Backups section)

3.  Click Restore (or "Find and Restore Backup Icon Sets")

Without backups, re-importing Input Icons resets the included icon sets to their original sprites. Backups are recommended if you changed the included icon sets or use your own. Memory optimization is best for projects with finalized icons, so consider using it in later stages of development.
