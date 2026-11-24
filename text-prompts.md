---
title: "Text Prompts (TextMesh Pro)"
layout: default
nav_order: 2
parent: "Displaying Bindings"
---

# Text Prompts (TextMesh Pro)

There are two ways to show icons in TextMesh Pro texts. You can use both in the same project:

- **Text Prompt components** (II_TextPrompt, II_LocalMultiplayerTextPrompt): add the component to a text and write the Input Icons text tag (\<inputaction\> by default) where an icon should appear. The component fills in the icons of the actions you select on it. No style sheet entries are needed. Text Prompts can show several bindings, specific control schemes and the devices of individual players in local multiplayer.

- **Style tags:** write the action into any text, e.g. “Press \<style=Player/Jump\> to jump”. No component is needed, but the style tags must be added to the TextMesh Pro style sheet (setup wizard or Project Status page). Style tags are easy to combine with localization, as the tag is part of the translated text. Text Prompts work with localization too, with a bit of additional setup (see section [Localization](/input-icons-documentation/localization)).

Most text settings on the Input Icons Manager only affect one of the two: display type, delimiters, opening and closing tags and animated style tags only affect style tags. The Text Prompt tag settings only affect Text Prompt components. Tinting and “Use animated sprite assets for all texts” affect both.

We can use the II_TextPrompt script to display bindings along other text. In the inspector we need to assign a reference to a text component and an action reference. Then instead of typing the text into the TextMeshPro component, type it into the II_TextPrompt inspector instead. The II_TextPrompt script will apply the text to the TextMeshPro component and occurrences of **\<inputaction\>** will be replaced with sprite tags, displaying the bindings of the referenced action. You can display multiple action references with a single II_TextPrompt component by clicking the “Add” button at the bottom. The order of the action references matters. The first action reference will replace the first \<inputaction\>, the second reference will replace the second \<inputaction\> and so forth.

**Note:** if a prompt has more than one action reference and the text will be localized, use indexed tags instead, e.g. **\<inputaction:0\>** for the first action reference, **\<inputaction:1\>** for the second, and so on. Indexed tags are matched by their number instead of their position in the sentence, so a translated string can freely reorder them without changing which sprite ends up where. Plain **\<inputaction\>** tags still work exactly as described above and are matched by position, so mixing the two styles within the same prompt is not recommended.

The base functionality is the same as discussed in [Displaying Bindings with Sprites and Images](/input-icons-documentation/sprites-and-images), but we also have the option to display several bindings at once. For example, to display the move keys (WASD) with a II_SpritePrompt, we would need four separate sprites. In text we can use a single text component to achieve this and more.

By changing the Action Display Type, we can select “**Single Binding**”, “**All Matching Bindings Single**” and “**All Matching Bindings With Delimiters**”

<table>
<colgroup>
<col style="width: 16%" />
<col style="width: 34%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Single Binding</strong></th>
<th><p>This setting works the same as in the II_SpritePrompt and II_ImagePrompt and will display a single sprite.</p>
<p>You can search the binding by Binding Type or by Binding Index</p>
<p><strong>Advanced Mode</strong> provides more controls just like with the other prompt components.</p></th>
<th>

<img src="/input-icons-documentation/assets/images/guide/text-prompts-1.png" alt="Screenshot">

</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>All Matching Bindings Single</strong></td>
<td><p>This can display multiple bindings and is useful for composite bindings like <strong>“WASD”</strong>.</p>
<p><strong>Binding ID All List:</strong> If multiple possible bindings are available, this slider can control which bindings to display. (e.g. WASD or the Arrow Keys)</p>
<p><strong>Advanced Mode</strong> provides more controls.</p></td>
<td>

<img src="/input-icons-documentation/assets/images/guide/text-prompts-2.png" alt="Screenshot">

</td>
</tr>
<tr class="even">
<td><strong>All Matching Bindings With Delimiters</strong></td>
<td><p>This option will display all available bindings. E.g. <strong>“WASD or Arrow Keys”</strong></p>
<p><strong>Delimiter</strong>: This will be placed between the available bindings. It can be left empty or augmented with additional TMP tags like &lt;size&gt; or &lt;color&gt;</p></td>
<td>

<img src="/input-icons-documentation/assets/images/guide/text-prompts-3.png" alt="Screenshot">

</td>
</tr>
</tbody>
</table>

General II_TextPrompt Settings

<table>
<colgroup>
<col style="width: 32%" />
<col style="width: 67%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Allow Tinting</strong></th>
<th>This allows the displayed sprites for this action to be tinted, allowing you to display your sprites in the color you want, using the &lt;color&gt; tag before the &lt;inputaction&gt; tag.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Use Font (experimental, icon switching not supported)</strong></td>
<td><p>If we tag this field, the displayed bindings will be displayed as a special SDF font instead of sprites. This ensures the displayed icons won’t get pixelated at a large size.</p>
<p>Unfortunately, TMP does not seem to support Unicode symbols very well when assigning a new text to a text field. The text field won’t display the Unicode symbols appropriately, which means we can not use the font style in this manner when switching devices.</p>
<p>Using textComponent.OnRebuildRequested() would fix the issue, but this method is not available in builds.</p>
<p>If you know a fix or workaround, please let me know.</p></td>
</tr>
</tbody>
</table>

**Text Prompt tag settings:** The text tag (\<inputaction\> by default) and the opening and closing tags Text Prompts put around their icons (e.g. \<size=120%\> and \</size\> to make icons bigger) are set on the Input Icons Manager or in the Input Icons Settings window (Text & Style Tags). Since version 5.0.0 they are saved with the manager; earlier versions reset them after scripts recompiled.

## Changing displayed Bindings in II_TextPrompts

To change the displayed text and bindings in your text prompt components, it is best to use the following methods

<table>
<colgroup>
<col style="width: 42%" />
<col style="width: 57%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>SetText(string newText)</strong></th>
<th>This applies a new text and also refreshes the TMPro component.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>SetTextPromptData(List&lt;TextPromptData&gt; newTextPromptDatas)</strong></td>
<td>Use this method to update the list of bindings to display.</td>
</tr>
<tr class="even">
<td><strong>SetTextPromptData(II_TextPromptDataSO textPromptDataSO)</strong></td>
<td><p>Similar to the previous method, this can be used to update the list of bindings to display. First you need to create a Scriptable Object of type II_TextPromptDataSO. This object manages a <strong>TextPromptData</strong> list, similar to the II_TextPrompt component. Add the actions you want to display to that Scriptable Object, then call the SetTextPromptData method on the II_TextPrompt to display the bindings defined in the Scriptable Object.</p>
<p>The best way to use this is to create all the Scriptable Objects you need beforehand and assign them when needed.</p>
<p>

<img src="/input-icons-documentation/assets/images/guide/text-prompts-4.png" alt="Screenshot">

</p>
<p>Also, have a look at the TextPromptsRuntimeUpdates example scene.</p></td>
</tr>
</tbody>
</table>
