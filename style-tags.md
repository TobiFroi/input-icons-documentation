---
title: "Style Tags"
layout: default
nav_order: 3
parent: "Displaying Bindings"
---

# Style Tags

This requires the completion of part three of the setup window. In this part we added the necessary styles to the Default Style Sheet of TMPro. After that, we can display bindings by using the TMPro-style tag (as can be found on the official website [**http://digitalnativestudios.com/textmeshpro/docs/rich-text/#style**](http://digitalnativestudios.com/textmeshpro/docs/rich-text/#style)).

Although this method is not as flexible as using the II_TextPrompt component, it can be handy to display bindings without the need of an extra component.

<img src="/input-icons-documentation/assets/images/guide/style-tags-1.png" alt="Screenshot" width="254">

When we enter play mode, the opening tags in the style sheet will automatically be updated with the appropriate tags (given we enabled Style Sheet Autoupdates in the setup window), displaying the icons for the device currently in use.

To display the bindings for a specific action, we can insert the following into a TMPro text field: **\<style=NameOfActionMap/NameOfAction\>.** For example, to display the bindings for a "jump" action in the "Platform Controls" action map, we would insert **\<style=Platform Controls/Jump\>** into the text field. Similarly, to display the bindings for a "move" action, we would insert \<style=Platform Controls/Move\> which would likely display either the "W A S D" keyboard keys or arrow key sprites, or the left stick sprite if a gamepad is being used. To display only one part of the move action we can write insert **\<style=Platform Controls/Move/Down\>.**

<img src="/input-icons-documentation/assets/images/guide/style-tags-2.png" alt="Screenshot" width="366">

Open **Tools Input Icons Input Icons TMPro Style List Window** to open a window which contains all the information needed to display bindings. To display a binding, simply copy and paste the entry in the first column (labeled "TMPro Style Tag") into a text field. Or if you are using fonts, use the second column.

## Displaying Bindings as an SDF Font in TMPro using the style tag

Since version 2.0.0 it is possible to display a special font instead of sprites in TMPro texts. The advantage is that SDF fonts will always appear crisp at any size whereas sprites can become pixelated when scaled up a lot. A disadvantage is that since it is a font, adding details to the displayed symbols can only be done by assigning a material to the text.

Displaying font input icons is very similar to displaying them as sprites. Just add “Font/” in front of the style. If you used “\<style=Controls/Move\>” to display the move action, you would write **“\<style=Font/Controls/Move\>”** now. The scheme is **“\<style=Font/ActionMap/Action\>”.**

Just like with non font styles you can grab the style texts from the window: **Tools Input Icons Input Icons TMPro Style List Window**
