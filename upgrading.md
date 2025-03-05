---
title: Upgrading to Unity 6
layout: default
nav_order: 12
---

# Upgrading to Unity 6

When upgrading your project from an earlier Unity version to Unity 6, you'll need to make some adjustments to ensure Input Icons continues to work correctly.

## TextMeshPro Changes in Unity 6

The main difference in Unity 6 is that TextMeshPro comes integrated by default, rather than as a package manager asset. This change requires specific steps to maintain compatibility with Input Icons.

## Upgrading Process

Before starting:
1. Locate your TextMeshPro default stylesheet in the TextMeshPro/Resources folder
2. Create a backup copy to ensure you can restore your settings if needed

### Step-by-Step Guide

1. **Delete the default TextMeshPro stylesheet** from your TextMeshPro/Resources folder

2. **Import TMP Essential Resources**:
   - Go to Window > TextMeshPro > Import TMP Essential Resources
   - This will import the Unity 6 compatible version of the resources

3. **Reconfigure Input Icons setup**:
   - Open the Input Icons Setup window (Tools > Input Icons > Input Icons Setup)
   - Verify that all paths are correct for the new TextMeshPro location
   - Re-run the setup process to create new sprite assets in the correct location

4. **Recreate TMP Sprite Assets**:
   - In the Setup for TextMeshPro section, click the "Create TMP_SpriteAssets" button
   - This will generate new sprite assets compatible with Unity 6's TextMeshPro

5. **Update Style Sheet** (if using style tags):
   - In the Setup for TextMeshPro style tag section, regenerate the style tags
   - This ensures the styles are properly configured for the new TextMeshPro implementation

## Potential Issues

After upgrading, you might encounter these issues:

1. **Missing sprites in text**:
   - Ensure the sprite assets were created in the correct location
   - Check that your TMP_Settings reference the correct paths

2. **Style tags not working**:
   - Regenerate the style tags using the setup window
   - Verify that the style sheet was properly created and saved

3. **Font asset references**:
   - Some TextMeshPro components might need to have their font assets reassigned

## Verifying the Upgrade

To verify that Input Icons is working correctly after upgrading:

1. Enter Play mode and check if your input icons display correctly
2. Test switching between keyboard and gamepad to ensure the icons update
3. Verify that any custom styling or configurations have been preserved

If you encounter persistent issues after following these steps, you may need to reimport the Input Icons package or contact support for assistance.

{: .note }
Unity 6 represents a significant change in how TextMeshPro is integrated. The upgrade process ensures compatibility with this new implementation while maintaining all Input Icons functionality.