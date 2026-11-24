---
title: "Mobile (Android & iOS)"
layout: default
nav_order: 1
parent: "Devices and Platforms"
---

# Mobile (Android & iOS)

Since version 3.2.0 displaying specific sprites on mobile devices is supported with some differences when compared to Keyboard and Gamepad support.

The main difference is that the displayed sprites are not derived from an actual binding within an Input Action Asset. This means the displayed sprites for mobile are fixed and will not adapt to rebound input actions. For the vast majority of games this should not be an issue as users are not used to rebind mobile input anyways (e.g. rebinding single touch (Touch\[Touchscreen\]) to multi touch (touch\*/Press\[Touchscreen\]).

<img src="/input-icons-documentation/assets/images/guide/mobile-support-1.png" alt="Screenshot" width="219">

So instead of referencing an input action in our components, we will instead use strings – specifically the strings defined in our mobile Icon Set. The **default mobile Icon Set** is placed under the “**Assets/TobiFroi/InputIcons/Icon Sets/Mobile/”** folder. As you can see in the image beside, we mainly use the Custom Context list to define which mobile actions we want to display.

It is highly recommended to **duplicate this asset (IconSet_Mobile_Grey) and exchange the sprites with your own sprites**. You can adjust your Icon Set to your liking. After that, head to the **Setup Window** (Tools – Input Icons -Input Icons Setup) and to the **Customization section** and replace the default Icon Set with your own. After that make sure to **(re-)create the sprite asset** containing your mobile sprites.

We can display mobile icons with SpriteRenderers, UI Images and TextMeshPro Texts. To make the mobile support component to work, the corresponding Input Icons Base Prompt Component needs to be attached to the object as well (have a look at the table below).

The behavior works as follows. When the Base Prompt Component updates the displayed sprites, it will fire an event. The Mobile Support Component will react to that event by overriding the sprites or \<inputaction\> tags with the ones used for the mobile version.

<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 40%" />
<col style="width: 42%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Base Prompt Component</strong></th>
<th><strong>Mobile Support Component</strong></th>
<th><strong>Example</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>II_SpritePrompt</strong></td>
<td><p><strong>II_SpritePromptMobileOverride</strong></p>
<p>Requires an II_SpritePrompt component.</p>
<p>Add sprite overrides using the button at the bottom. Then reference the same SpriteRenderers you referenced in the II_SpritePrompt and select which sprite to display.</p>
<p>The available sprite options depend on the mobile Icon Set referenced on the InputIconSetConfiguratorSO.</p></td>
<td>

<img src="/input-icons-documentation/assets/images/guide/mobile-support-2.png" alt="Screenshot">

</td>
</tr>
<tr class="even">
<td><strong>II_ImagePrompt</strong></td>
<td><p><strong>II_ImagePromptMobileOverride</strong></p>
<p>Requires an II_ImagePrompt component.</p>
<p>The rest is very similar to the component described above.</p></td>
<td>

<img src="/input-icons-documentation/assets/images/guide/mobile-support-3.png" alt="Screenshot">

</td>
</tr>
<tr class="odd">
<td><strong>II_TextPrompt</strong></td>
<td><p><strong>II_TextPromptMobileOverride</strong></p>
<p>Requires a II_TextPrompt component.</p>
<p>This allows you to replace the occurances of &lt;inputaction&gt; with the sprites defined in your mobile Icon Set.</p>
<p>You can replace a single &lt;inputaction&gt; tag with multiple sprites by adding more fields.</p></td>
<td>

<img src="/input-icons-documentation/assets/images/guide/mobile-support-4.png" alt="Screenshot">

</td>
</tr>
</tbody>
</table>
