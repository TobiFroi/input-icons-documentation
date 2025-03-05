---
title: Troubleshooting
layout: default
nav_order: 8
---

# Troubleshooting

This section covers common issues and their solutions.

## Common Issues

| Problem | Possible Cause | Solution |
|---------|----------------|----------|
| Compile errors on import | Missing dependencies | Ensure TextMeshPro, Input System, and 2D Sprite packages are installed |
| Steamworks errors | Steamworks integration | If using Steamworks, ensure the Steamworks.NET package is installed |
| Missing style tags | Style sheet not updated | Run the setup tool again to update the TextMeshPro Default Style Sheet |
| Control schemes not working | Name mismatch | Ensure control scheme names match between Input Action Assets and the Setup window |
| Settings not applied | Manager reset after update | Reopen the setup window and reconfigure settings after updating |
| Icons not displaying in build | Manager not initialized | Make sure the Input Icons Manager is properly initialized in your first scene |

## Steamworks / Steamworks.NET Issues

If you get compile errors related to Steamworks: Type or namespace name 'Steamworks' could not be found

This means you have `STEAMWORKS_NET` in your Scripting Define Symbols but don't have the Steamworks.NET package installed.

Solutions:
1. Install [Steamworks.NET](https://github.com/rlabrecque/Steamworks.NET/releases)
2. Ensure "com.rlabrecque.steamworks.net" is added to the Assembly Definition References
3. If using a different Steam framework, you may need custom code

## Missing Assembly References

If you see errors like: The type or namespace name '...' does not exist in the namespace '...'

This is likely due to Assembly Definitions issues:

1. Delete the content of the "Scripts" folder in "InputIcons/Scripts"
2. Reimport the asset or the Scripts folder

## TextMeshPro Style Tags Troubleshooting

If your style tags aren't working:

1. **Check Sprite Assets**: Verify that sprite assets exist in "Assets/TextMesh Pro/Resources/Sprite Assets/" with names matching your Icon Sets
2. **Check Style Sheet**: Look for your actions in the Default Style Sheet at "Assets/TextMesh Pro/Resources/Style Sheets/"
3. **Persistence Issues**: If styles disappear after restarting Unity, make a small manual change to the style sheet and undo it to force a save

## Rebinding Issues

If rebinding doesn't update gameplay:

- When using a generated C# class from an Input Action Asset, you must manually sync changes
- Add these lines in your Awake method (where "inputActions" is your generated class instance):
  
  InputIconsManagerSO.RegisterInputActionAssetForRebinding(inputActions.asset);
  InputIconsManagerSO.UpdateRegisteredInputActionAssetsForRebinding(inputActions.asset);

## Controls Issues
If controls behave strangely:

Check for multiple active Player Input components in your scene
Steam can interfere with controls if the Unity Player runs via Steam
Try recreating your Input Action Asset if you've upgraded from an older Input System version

## Build Issues
If icons work in the editor but not in builds:

Make sure the Input Icons Manager is properly initialized in your first scene
Check that all necessary sprites are included in your build
Verify that your TextMeshPro resources are properly included in the build

