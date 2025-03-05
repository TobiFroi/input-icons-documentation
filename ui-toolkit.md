---
title: UI Toolkit Integration
layout: default
nav_order: 9
---

# UI Toolkit Integration

Input Icons offers support for Unity's UI Toolkit through a separate extension asset available on the Asset Store.

## UI Toolkit Extension

The UI Toolkit extension allows you to display Input Icons within UI Toolkit interfaces:

- Display input bindings in UI Documents
- Update bindings automatically when input devices change
- Integrate with UI Builder for visual editing


## Availability

The UI Toolkit extension is available as a free separate package on the Unity Asset Store. This modular approach keeps the main package focused while providing specialized UI Toolkit support for those who need it.

[Get the UI Toolkit Extension on the Asset Store](https://assetstore.unity.com/packages/tools/gui/input-icons-ui-toolkit-extension-255994)

## Current Limitations

The current version of the UI Toolkit extension has some limitations compared to the main package:

- Advanced mode for prompts is not available
- Displaying input icons as fonts is not supported
- Local multiplayer games support requires additional work
- Some specialized features may require custom implementation

These limitations may be addressed in future updates to the extension.

## Using the Extension

After importing the extension:

1. The UI Builder will have new components for displaying input icons
2. You can reference input actions similar to the main package
3. Icons will update automatically when the input device changes

For detailed usage instructions, please refer to the documentation included with the UI Toolkit extension.

{: .note }
The UI Toolkit integration is maintained alongside the main Input Icons package but may receive updates on a different schedule.