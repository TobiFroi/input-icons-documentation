---
title: "Performance Options"
layout: default
nav_order: 6
parent: "Customization"
---

# Performance Options

These settings are on the Input Icons Manager and in the Input Icons Settings window (Text & Style Tags).

We can improve the performance when the user switches devices by selecting the Text Update Method “Via Input Icons Text Components” in the Input Icons Manager.

<img src="/input-icons-documentation/assets/images/guide/performance-options-1.png" alt="Screenshot" width="209">

The default setting is “Search and Update”, which will search for all text objects in the scene and update them when the user switches devices.

By using the “Via Input Icons Text Components” method, the manager won’t have to search through the whole scene every time the user switches devices. But we have to ensure that the required text objects have a InputIconsText component attached to them.
