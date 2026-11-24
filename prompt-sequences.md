---
title: "Prompt Sequences (QTEs, Combos)"
layout: default
nav_order: 2
parent: "Interaction Prompts"
---

# Prompt Sequences (QTEs, Combos)

**II_PromptSequence** shows prompts one after another (quick time events) or in a row (combos, like entering a code). It works without a player (e.g. in cutscenes) and with one (started by an II_Interactable).

## Sequence Data

The data can be stored in an **II_PromptSequenceDataSO** asset (Create \> Input Icons \> Prompt Sequence Data), so timings and actions can be changed without opening scenes, or directly on the component (Data Source: Inline). A sequence consists of **groups**, and each group of **steps**:

- **Step**: the prompt type (Tap, Hold, Mash, Timing), the action (with an optional composite part and additional actions), the **slot** where it appears, a **delay** before it appears and a **time limit**. Depending on the type also the hold duration and release mode, the presses needed and the alternate action, or the approach duration.

- **Group**: e.g. “Dodge” or “Up Up Down Down”. A group can be a **checkpoint**, a **combo** (Show All At Once) and have its own On Fail setting.

- Optionally a **Time Scale Curve** per step (e.g. slowing down more as time runs out).

## Slots and Prompt Prefabs

Slots are empty RectTransforms where the prompts appear, in a Screen Space or a World Space canvas. Steps refer to them by their index. The scale of a slot also sets the size of the prompts. The sequence creates the prompts from its **Prompt Prefabs** (the prefabs of Input Icons by default, or your duplicates).

## Starting a Sequence

- **Manual**: call **StartSequence()** from code, a UnityEvent (e.g. a button) or a Timeline Signal Receiver. **StartSequence(groupIndex)** starts at a group, **StartFromCheckpoint()** after the last completed checkpoint, **Stop()** stops it.

- **On Enable**, or started by an **Interactable** (when its prompt is completed, or when a player comes in range).

- While running, the sequence enables the actions it needs (e.g. if the player’s controls are disabled during a cutscene) and restores them afterwards.

## Wrong Input, Failing and Checkpoints

- **Wrong Input**: **Off**, **Sequence Actions** (default: buttons of other actions in the sequence fail the step) or **Any Button** (any other button fails it).

- **On Fail**: **Fail Sequence**, **Retry Step**, **Retry Group**, **Restart From Checkpoint** or **Skip** (the step counts as missed, e.g. for scored sequences). **Max Retries** and **Retry Delay** limit the retries.

- **Results**: **CurrentGroup**, **CurrentStep**, **LastCheckpoint**, **CompletedSteps**, **MissedSteps**, **PerfectSteps** and **Retries**. Events: On Started, On Step Started/Completed/Failed, On Group Completed, On Checkpoint, On Succeeded and On Failed.

## Slow Motion and Timers

- **Slow Motion**: a time scale while the sequence runs, eased in and out, also slowing down physics steps. The prompts keep running at normal speed, and pause while the time scale is 0 (e.g. in a pause menu).

- **Show Timer** (off by default): the prompts show the time left on their thin outer timer ring.

## Combos

A group with **Show All At Once** shows all its prompts in a row at the **Combo Slot** (with **Combo Spacing**). The current prompt is highlighted, completed ones are dimmed. A wrong input fails the combo; with On Fail “Retry Group” it starts again. An optional **Combo Time Limit** applies to the whole group.
