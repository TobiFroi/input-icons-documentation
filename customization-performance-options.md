---

title: Performance Options
layout: default
parent: Customization
nav_order: 4
---

# Performance Options

To improve performance when users switch devices, select **Text Update Method: "Via Input Icons Text Components"** in the Input Icons Manager.

## Performance Modes

- **Default Mode: "Search and Update"**
  - Searches all text objects in the scene and updates them when the user switches devices.
  
- **Optimized Mode: "Via Input Icons Text Components"**
  - Avoids searching the entire scene.
  - Requires that each text object has an **`InputIconsText`** component attached.
