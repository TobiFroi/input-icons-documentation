### tmpro-bindings.md (child of displaying-bindings.md)
```markdown
---
title: TextMeshPro Bindings
layout: default
parent: Displaying Bindings
nav_order: 2
---

# Displaying Bindings in TextMeshPro

The `II_TextPrompt` script allows you to display binding icons seamlessly within your TextMeshPro text. This component replaces instances of `<inputaction>` with sprite tags showing the bindings of your referenced actions.

## Basic Setup

1. Add the `II_TextPrompt` component to a GameObject that has a TextMeshPro component
2. Assign a reference to your TextMeshPro component
3. Assign one or more action references
4. Type your text in the `II_TextPrompt` inspector, using `<inputaction>` where you want to show bindings

![TextPrompt Component](/input-icons-documentation/assets/images/text-prompt-component.png)

## Action Display Types

The component provides three ways to display actions:

### Single Binding

Shows a single binding, similar to the Sprite and Image prompts:

![Single Binding](/input-icons-documentation/assets/images/tmpro-single-binding.png)

| Setting | Description |
|---------|-------------|
| Search Method | "Binding Type" or "Binding Index" |
| Advanced Mode | Provides more controls for complex bindings |

### All Matching Bindings Single

Shows multiple bindings together, useful for composite bindings like WASD:

![All Matching Bindings](/input-icons-documentation/assets/images/tmpro-all-bindings.png)

| Setting | Description |
|---------|-------------|
| Binding ID All List | Controls which set of bindings to display |
| Advanced Mode | Provides additional control options |

### All Matching Bindings With Delimiters

Shows all available binding options, like "WASD or Arrow Keys":

![All Bindings With Delimiters](/input-icons-documentation/assets/images/tmpro-bindings-delimited.png)

| Setting | Description |
|---------|-------------|
| Delimiter | Text placed between available bindings |

## Component Settings

| Setting | Description |
|---------|-------------|
| Allow Tinting | Enables sprite tinting using the `<color>` tag |
| Use Font | Uses a special SDF font instead of sprites (experimental) |

## Updating Text at Runtime

You can dynamically update text prompts using these methods:

```csharp
// Update the text while preserving bindings
textPrompt.SetText("Press <inputaction> to jump");

// Update the bindings to display
textPrompt.SetTextPromptData(newTextPromptDataList);

// Use a preconfigured ScriptableObject for bindings
textPrompt.SetTextPromptData(textPromptDataSO);