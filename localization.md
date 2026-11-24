---
title: "Localization"
layout: default
nav_order: 4
parent: "Displaying Bindings"
---

# Localization

Both ways of showing icons in texts work with localization tools like Unity’s Localization package. The tags simply become part of the translated strings.

**Style tags** are the easiest to localize: put the tag into the translated string, e.g. “Press \<style=Player/Jump\> to jump” in English and “Drücke \<style=Player/Jump\> zum Springen” in German. Any localization tool that writes the translated text into the TextMesh Pro component works, and the icons keep updating when the player switches devices.

**Text Prompts** need one extra step: a Text Prompt keeps the text with its tags and writes the finished text (with the icons) into the TextMesh Pro component. If a localization tool writes the translated text into the TextMesh Pro component directly, the Text Prompt overwrites it with its previous text at the next update. Instead, pass the translated string to the Text Prompt:

- **Unity Localization:** add a Localize String Event to the text, and in its “Update String” event select the Text Prompt and **SetText** (in the Dynamic String section). Remove the default entry that writes to the TextMeshPro text.

- **Other tools or your own code:** call SetText with the translated string, e.g.

> textPrompt.SetText(localizedString);

- **Several actions in one text:** use indexed tags like \<inputaction:0\> and \<inputaction:1\>. They are matched by their number, so a translation can change the order of the actions in the sentence without mixing up the icons.

II_LocalMultiplayerTextPrompt works the same way.

**Key names as text:** if bindings are displayed as text instead of sprites (Display Type “Text” or “Text In Brackets”), the key names can be shown in English or in the language of the player’s system (see “Text Display Language” in section [Display Settings](/input-icons-documentation/display-settings)). Action names shown as text can be changed with the action name overrides.
