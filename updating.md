---
title: Updating the Asset
layout: default
nav_order: 11
---

# Updating From An Earlier Version

When updating Input Icons to a new version, it's important to follow some best practices to ensure a smooth transition and avoid losing your custom settings.

## Before Updating

Always create a backup of your project before updating to a new version of Input Icons. This ensures you can revert if any unforeseen issues arise.

## Preserving Custom Settings

When updating, your settings on the manager and configurator might be reset to default values. To prevent this:

### Method 1: Using the Setup Window (Recommended)

Since version 3.2.12, you can easily create duplicates of the manager and configurator through the setup window:

1. Open Tools → Input Icons → Input Icons Setup
2. In the Base Setup section, look for the duplication options
3. Click to duplicate the InputIconManager and InputIconConfigurator
4. The duplicated assets will have "Is Actual Manager" or "Is Actual Configurator" enabled in their inspector

![Duplicating Manager](/input-icons-documentation/assets/images/duplicate-manager.png)

### Method 2: Manual Duplication

If you're on an earlier version or prefer manual control:

1. Locate the InputIconManager and InputIconConfigurator in the project
   - Usually found in Assets/InputIcons/Resources/InputIcons/
2. Duplicate these assets (Ctrl+D or right-click → Duplicate)
3. Rename the duplicates clearly (e.g., "MyCustomInputIconManager")
4. Enable "Is Actual Manager" or "Is Actual Configurator" in the inspector of each asset

## After Updating

After updating to a new version:

1. **Check your references**: Ensure the Input Icons Setup window points to your custom manager and configurator assets
2. **Verify settings**: Check that your settings have been preserved
3. **Update TMP resources if needed**: If the update changed any TextMeshPro resources, you might need to regenerate them

## Preserving Custom Icon Sets

If you've created custom icon sets with your own sprites:

1. Before updating, create a copy of your custom icon sets
2. After updating, ensure these custom icon sets are still assigned in the InputIconSetConfigurator
3. If needed, reassign your icon sets in the Customization section of the setup window

![Custom Icon Sets](/input-icons-documentation/assets/images/custom-icon-sets.png)

## Handling Major Version Updates

When updating across major versions (e.g., from 2.x to 3.x):

1. Read the changelog thoroughly to understand new features and breaking changes
2. Consider setting up the new version in a test project first
3. Follow any specific update instructions provided in the release notes
4. You may need to reconfigure some aspects of your setup for major version changes

## Troubleshooting Update Issues

If you encounter issues after updating:

1. **Missing scripts**: Reimport the Input Icons package
2. **Compile errors**: Check for any API changes that might affect your custom scripts
3. **Display issues**: Regenerate sprite assets using the setup window
4. **Duplicate managers**: Ensure only one manager and configurator have the "Is Actual" flag enabled

If problems persist, you can always revert to your backup and contact support for assistance.