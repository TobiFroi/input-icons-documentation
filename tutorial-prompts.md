---
title: "Tutorial Prompts"
layout: default
nav_order: 3
parent: "Interaction Prompts"
---

# Tutorial Prompts

**II_TutorialPrompt** hides a hint like “Press \[Space\] to jump” once the player used the action. Put it on the object that shows the hint, e.g. a Text Prompt.

- **Required Uses** and **Minimum Hold Time** (e.g. 0.4 seconds for moving, so a short tap doesn’t count).

- **Show Delay**, **Hide Delay** and fading with a **CanvasGroup**. **Hide While Action Disabled** hides the hint e.g. during cutscenes.

- **Remember**: the uses are stored in PlayerPrefs by default. Set **II_TutorialPrompt.Profile** (e.g. per save slot or player name), so players sharing a computer don’t share their progress.

- **Your own save system**: assign your own **II_ITutorialStorage** (Load and Save) to **II_TutorialPrompt.Storage**. The static event **CountChanged** is called before a count is saved, **AnyLearned** when a tutorial was learned.

- Events **On Used** and **On Learned**, and the methods **ResetLearned** and **MarkLearned**.
