---
title: "Rebinding"
layout: default
nav_order: 6
---

# Rebinding

<img src="/input-icons-documentation/assets/images/guide/rebinding-2.png" alt="Screenshot" width="264">

<img src="/input-icons-documentation/assets/images/guide/rebinding-3.png" alt="Screenshot" width="181">

In the prefab folder we can find the **II_UI_RebindActionImageObject** which is a prefab we can use to rebind our input. You might want to create your own prefab with custom visuals but this prefab is a good starting point. (**I recommend to create another prefab out of this prefab so your buttons don’t get messed up when you update this asset**)

The script takes an Input Action as a reference which we can then rebind by using a button and then pressing the desired new key.

The settings to control which binding to display is very similar to the controls for Sprite-, Image-, and Text-Prompts.

The toggle “**Allow Rebinding**” can be turned off for input actions we don’t want to be rebound, but should still be visible to the player.

The toggle “**Ignore Other Buttons**” can be enabled if we want to keep the binding on that button, even if another rebind button gets bound to the same binding. This option is only available when the selected Rebind Behaviour for all buttons is set to “Override Existing”.

The text field “**Action Display Name**” provides a quick way to change the text of the action name label without having to select the text object in the hierarchy. It can also be used by the **Listening Text Format** field below to configure what message the users sees after clicking the button – e.g. “Press: Jump” or “Enter: Move Up” where {actionname} gets replaced by the value in the Action Display Name field. Since editing the Action Display Name field also changes the text within the **Action Name Display Text** itself, you might need to edit the TextMeshPro field manually again if you want to display a different text on that.

The last field “**Rebind Behavior**” can be used to choose the wanted behavior in case the player wants to bind a key to an already existing key. This option is global can also be found on the Input Icons Manager. The options are

1.  “**Override Existing**” in that case, the new binding gets accepted and the other action will be unbound.

2.  “**Cancel Override If Binding Already Exists**” will display a message like “Binding already in use” to the player. A single rebind button cancels the rebind, a multiple bindings button waits for another key. To use that key, the player first has to rebind the other action.

3.  “**Always Apply And Keep Other Bindings**” will always accept the new binding. Other bindings will not lose their binding like in “Override Existing” when a conflict occurs, also not when the saved bindings are loaded.

When the saved bindings are loaded, bindings that use the same key within an action map are cleared (except with “Always Apply And Keep Other Bindings”). The rebind buttons do the same while rebinding, so the bindings stay the same between play sessions. Cancelling a rebind (with the cancel key or a key of the wrong device) restores the previous binding.

<img src="/input-icons-documentation/assets/images/guide/rebinding-4.png" alt="Screenshot" width="243">

**Rebinding Multiple Bindings Button**

<img src="/input-icons-documentation/assets/images/guide/rebinding-5.png" alt="Screenshot" width="292">

Since version 4.1.0 the package includes a **II_UIRebindMultipleBindingsBehaviour** component which can be used for rebinding multiple bindings sequentially. This is especially useful for movement actions. The component can be used to rebind the WASD keys, the DPad or a stick for example.

The component mostly works like the single binding rebind component, there are some differences in the inspector though.

- In addition to the rebind order you can also define a display order. So you can display WASD but rebind the keys in the WSAD order if you want to. Rebind order is defined by the order of the binding in the list. The display order by an extra field “**Display Order**” in each entry. A value of “-1” will mean no order. You should either set all to “-1” or give each entry an order index.

- Compared to the single rebind buttons, there is no calculation for Composite and Non-Composite types included yet, so you will always have to select them manually in the inspector for now.

- You will need to add a few images to the **Binding Display Images** list in the inspector – one image per binding to be displayed. If you have WASD and the Left Stick of the controller, 4 images are enough. When the Left Stick gets displayed, the first image will display it. I recommend to use a Horizontal Layout Group on the parent object and set the Child Alignment to “Middle Center” to display the images properly aligned.

- The same key can’t be used for two bindings of one rebind sequence (e.g. Space for Up and Down). The button shows the “Key Already Used” object and waits for another key.

- With “Override Existing”, each new key is removed from other actions and from other bindings of the same action (e.g. the arrow keys when rebinding WASD).

- Cancelling the sequence restores all of its bindings, also the bindings of other actions that were cleared during the sequence.

## Saving and Loading Rebinds

**Input Icons automatically saves and loads all binding overrides using a JSON file** stored in your game's persistent data directory. When players customize their controls, the changes are immediately saved to rebinds.json in the InputIconsData folder. These settings persist across game sessions and app updates, ensuring players never lose their personalized control schemes. The system also includes automatic migration from the legacy PlayerPrefs storage method, so existing users will seamlessly transition to the new file-based system without losing their current rebinds. No additional setup is required - everything works automatically as long as the loadAndSaveInputBindingOverrides option is enabled in the Input Icons Manager.

## Rebinding Using A Generated C# Class

<img src="/input-icons-documentation/assets/images/guide/rebinding-1.png" alt="Screenshot" width="194">

If you use a generated C# class out of an Input Action Asset and you want to use the rebind button prefabs of this asset, you will have to do a little bit of additional work. The rebind prefabs which come with this tool can only rebind the actions of the Input Action Asset and can not rebind the actions of the generated C# class by default, therefore we have to write some code to keep the asset and the generated C# class in sync.

Whenever we change a binding using the prefab buttons, we also need to apply that new binding override to all instances of the generated C# class to keep it in sync. Have a look at the template class called “**II_InputActions_ControllerTemplate**” details.

**Attention**: In **version 3.2.13** the following methods changed from 2 methods to only 2 lines of code, making it quicker to implement.

**All you need to do now is to call the following two lines of code within the Awake function where “inputActions” is the instance of your generated class:**

- **InputIconsManagerSO.RegisterInputActionAssetForRebinding(inputActions.asset);**

- **InputIconsManagerSO.UpdateRegisteredInputActionAssetsForRebinding(inputActions.asset);**

For some more information you might also want to have a look at the example scene called “InputIcons_ExampleScene6_GeneratedCode”. This scene makes use of the template class to move the player object and to apply binding overrides to the generated C# class.

## Rebinding By Using Your Own Methods

If you decide to not use the rebind buttons that come with this asset, you can use the “**InputIconsManagerSO.ApplyBindingOverridesToInputActionAssets**” method to apply binding overrides to the Input Action Assets managed by the InputIconsManager. The manger should then update the displayed input icons accordingly.

For example: You have generated a C# class out of an Input Action Asset and set binding overrides to that class using your own rebinding tools. In this case the InputIconsManager would not know about the changes made. You have to use the above mentioned method to sync up the changes every time you make changes, so the InputIconsManager can display the correct sprites.

## Rebind Storage and Player Profiles

Input Icons provides flexible options for storing player rebind data, supporting both single-player and multiple sequential player setups.

**Storage Methods**

Choose between two storage methods in the **Input Icons Manager**:

**JSON File (new Default since v4.0.0)**

- **Best for**: Complex games, debugging, unlimited rebinds

- **Benefits**: No size limits, human-readable files, easy backup/version control

  - No size limits (unlimited rebinds per profile)

  - Human-readable files for easy debugging

  - Easy backup and version control integration

  - Cross-platform file format consistency

  - Built-in editor tools (Open JSON Folder button)

- **Limitations**: Manual sync required for cross-device play

- **Storage**: Application.persistentDataPath/InputIconsData/

**PlayerPrefs (Legacy)**

- **Best for**: Existing projects (v3.x compatibility), platform integration needs

- **Benefits**: Compatible with platform sync services (Steam Cloud, console profiles), familiar to existing Input Icons users, Automatic migration to JSON available

- **Limitations**: ~30KB size limit per profile, Platform-specific storage (harder to debug), No built-in backup capabilities

- **Storage**: Platform-specific preferences system

**Automatic Migration**

When switching from PlayerPrefs to JSON File storage, Input Icons automatically migrates existing rebind data. Legacy PlayerPrefs data is preserved and converted on first save with the new storage method.

**Player Profiles**

**Single Profile Mode (Default)**

Perfect for most games where each installation has one set of controls.

- Use Cases: Single-player games, online multiplayer, most indie games

- Benefits: Simple setup, optimal performance, clean file structure

- Storage: Single rebinds.json file or PlayerPrefs entry

**Multiple Player Profiles**

Enable in Input Icons Manager for scenarios where multiple users share the same device **sequentially** (one at a time).

**Setup**

1.  Open your **Input Icons Manager** in the inspector

2.  Choose your preferred **Storage Method** (PlayerPrefs or JSON File)

3.  Under **Player Profiles**, check **Enable Multi Player Profiles**

4.  Set **Max Player Profiles** (default: 4)

5.  The **Current Player Profile** shows which profile is active (0 = default)

**Use Cases**

- **Shared Computer**: Family members taking turns with different control preferences

- **Tournament Setup**: Quickly switch between competitor control schemes

- **Accessibility**: Different users with specialized control needs

**Features**:

- Up to 8 independent profiles per installation

- Profile-specific rebind storage

- Quick switching with automatic save/load

- Profile management tools (copy, delete, backup)

**Basic Usage**

*// Switch to player 2's bindings*  
**InputIconsManagerSO.SwitchToPlayerProfile(2);  
***// Save current bindings to player 1's profile  
***InputIconsManagerSO.SaveBindingsToPlayerProfile(1);  
***// Copy player 0's setup to player 3*  
**InputIconsManagerSO.CopyPlayerProfile(0, 3);**

**UI Integration**

Integrate with your settings menu by switching profiles when players access rebinding options:

**void OnPlayerSelectionChanged(int playerIndex)  
{  
InputIconsManagerSO.SwitchToPlayerProfile(playerIndex);  
*// Rebinding UI now shows that player's current bindings*  
}**

**File Storage Structure**

**PlayerPrefs Mode:**

- Single player: II-Rebinds\_

- Multiple players: II-Rebinds_0, II-Rebinds_1, II-Rebinds_2, etc.

<img src="/input-icons-documentation/assets/images/guide/rebinding-6.png" alt="Screenshot" width="191">

**JSON File Mode:**

**Important Notes**

- **Sequential Use Only**: Player profiles are designed for one player at a time, not simultaneous local multiplayer, although you can use profiles for multiple simultaneous players as well if you have Group A and Group B who like to take turns with their own custom bindings

- **Profile 0 Default**: Always serves as the main/default profile and supports legacy data migration

- **Persistent Storage**: All rebind data persists across game sessions and app updates

- **Cross-Platform**: Works on all Unity-supported platforms
