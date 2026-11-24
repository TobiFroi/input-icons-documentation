---
title: "Custom Context Sprites"
layout: default
nav_order: 3
parent: "Customization"
---

# Custom Context Sprites

<img src="/input-icons-documentation/assets/images/guide/custom-context-sprites-1.png" alt="Screenshot" width="164">

The preset Input Icon Sets that come with this package (in the folder **Assets/TobiFroi/InputIcons/Icon Sets/, Vol 1 and Vol 2** ) already have sprites defined for all common input keys, gamepad buttons and joysticks. In case we need more input controls, we can add them in the Custom Contexts list in the Input Icon Sets. We need the input binding string and a display icon, to add a new binding.

An easy way to find the input binding string for an input is to use the script “II_UITextDisplayAllActions” which is in the example folder of this package. Add it to a TextMeshProUGUI object to display current input bindings. Then we can use a rebind button to override the current binding with the new binding we want to add. The input binding string for that binding will be displayed in the brackets. For the mousewheel, the input binding string would be “Scroll” for example.

<img src="/input-icons-documentation/assets/images/guide/custom-context-sprites-2.png" alt="Screenshot" width="348">

**Important**: Whenever we make changes to an Input Icon Set, we will have to create a new Sprite Asset out of the Input Icon Set. Otherwise, our changes only exists in the Input Icon Set, but the desired sprite will not be available in the Sprite Asset used to display sprites within TMPro texts.
