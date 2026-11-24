---
title: "Steam Input"
layout: default
nav_order: 2
parent: "Devices and Platforms"
---

# Steam Input

When a game runs through Steam, Steam Input can take over a player’s controller and present it to the game as a virtual XBox controller. Unity’s Input System then detects a PS4 controller as an XBox controller, for example. Whether this happens depends on the Steam settings of the player and on the Steam Input settings of your game.

Input Icons comes with extensions for Steamworks.NET (<https://steamworks.github.io/>) and Facepunch Steamworks, which ask Steam for the real controller type and display the matching icons. For this to work, your project needs to initialize Steam, as described in the next section.

The icons are chosen as follows:

- **Steamworks.NET and Facepunch Steamworks:** The icons match the controller the player is currently using. If several controllers are connected through Steam Input, Input Icons learns which controller is which as soon as a button is pressed on it. Right after starting the game or reconnecting a controller, the icons might be wrong until a button on that controller is pressed. This detection is only available on Windows.

- Controllers for which Steam Input is not enabled are detected by Unity directly and always show their own icons.

- If Steam is not initialized, controllers taken over by Steam Input show XBox icons, as Unity only sees XBox controllers. In this case, Input Icons logs a hint to the console once.

You can turn off this behavior by removing the creation of the Steam Input extensions in the **CreateSteamExtensions** method of the InputIconsManagerSO.cs script. But note if you do so, players who have enabled Steam Input for a specific device will likely not get displayed the correct icons while using that device and user preference should always go first.

## Initializing Steam

**Since version 4.2.0, Input Icons does not connect to Steam on its own.** Initializing Steam is the responsibility of your project, for example with a SteamManager script. After Steam has been initialized, call **InputIconsManagerSO.RefreshSteamInputDetection()** so the correct icons are displayed right away:

> if (SteamAPI.Init())
>
> {
>
> InputIconsManagerSO.RefreshSteamInputDetection();
>
> }

When using Facepunch Steamworks, initialize Steam with **SteamClient.Init(yourAppId)** and call **InputIconsManagerSO.RefreshSteamInputDetection()** afterwards as well.

**Initialize Steamworks in Builds:** If you prefer Input Icons to initialize Steam for you, enable “Initialize Steamworks in Builds” in the Steam Settings of the Input Icons Manager (Steamworks.NET only). Input Icons then initializes Steam in builds that were launched through Steam. It never connects the Unity Editor and never connects builds that were started outside of Steam. I recommend leaving this option disabled and initializing Steam in your own project.

**Avoid connecting the Unity Editor to Steam:** Once the Unity Editor has been connected to Steam, Steam shows your game as running until you close Unity, and gamepads can stop responding, e.g. when you also start a build of your game. Unless you need to test Steam features in the editor, only initialize Steam in builds (for example by wrapping your initialization in \#if !UNITY_EDITOR).

**Publishing on other stores (itch.io, Epic Games Store, GOG):** The cleanest way is a separate build per store. For builds that are not published on Steam, add **DISABLESTEAMWORKS** to the Scripting Define Symbols when using Steamworks.NET. This removes all Steamworks code, including the Input Icons extension. If you use one build for all stores, only initialize Steam when the game was launched through Steam:

> if (InputIconsManagerSO.WasLaunchedBySteam())
>
> {
>
> // initialize Steam here
>
> }

## Local Multiplayer with Steam Input

With Steamworks.NET and Facepunch Steamworks, each player sees the icons of their own controller, also when Steam Input is enabled for it, like in the example below. On Windows, Input Icons learns which controller belongs to which player as soon as each player presses a button, which usually happens when players join the game. This works with the Local Multiplayer prompts and the II_LocalMultiplayerDeviceBasedObjectController.

<img src="/input-icons-documentation/assets/images/guide/steam-1.png" alt="Screenshot" width="501">

**Known limitations:**

- Matching controllers to players is only available on Windows.

- Replacing a controller during the game (e.g. when its battery runs out) can show wrong icons for the new controller, as Steam does not always report newly connected controllers correctly.

- The example II_LocalMultiplayerUserManager may assign a reconnected controller to a new player, as Steam Input recreates its virtual controllers whenever a controller is connected or disconnected.

- Depending on the player’s Steam settings, Steam can present the same controller twice after switching windows (e.g. Alt+Tab): as the controller itself and as a virtual XBox controller. Local multiplayer setups that add a player per device, like the example II_LocalMultiplayerUserManager, then create an additional player. In my tests, this happened with “PlayStation Controller Support” set to “Enabled in Games w/o Support” and did not happen with “Enabled” (Steam launcher: Steam -\> Settings -\> Controller).

## Steam Settings and Testing

Players can enable or disable Steam Input per controller type in the Steam settings (from the Steam launcher: Steam -\> Settings -\> Controller).

<img src="/input-icons-documentation/assets/images/guide/steam-2.png" alt="Screenshot" width="465">

These settings can also be overridden per Steam game by right clicking the game in the library and opening “Properties... -\> Controller”.

<img src="/input-icons-documentation/assets/images/guide/steam-3.png" alt="Screenshot" width="460">

Your game’s Steamworks page also allows you to opt controllers into Steam Input by default. Input Icons supports both options, so choose what fits your game and test it with the settings your players will likely use:

<img src="/input-icons-documentation/assets/images/guide/steam-4.png" alt="Screenshot" width="515">

**Tips for development and testing:**

- **Gamepads not responding?** In my tests, gamepads stopped responding in the Unity Editor and in games launched through Steam when Steam Input was disabled for them. Enabling Steam Input for these controller types fixed it. This might vary between gamepads and computers, but if you run into unresponsive gamepads, enabling Steam Input in the Steam settings is a good first step. Also close all running instances of your game and restart Unity, as an editor that was connected to Steam stays connected until Unity is closed.

- **Second player spawns after Alt+Tab?** Steam may present a PlayStation controller twice after switching windows. Setting “PlayStation Controller Support” to “Enabled” instead of “Enabled in Games w/o Support” solved this in my tests. See the known limitations in the local multiplayer section.

- Test Steam Input in a build that was launched through Steam, e.g. through your game’s Steam app or by adding your build as a Non-Steam game (Steam launcher: Games -\> Add a Non-Steam Game to My Library). Builds that were started directly from the .exe file can lose gamepad input once they connect to Steam.

- To initialize Steam in a build started outside of Steam, SteamAPI.Init() needs a steam_appid.txt file containing your App ID next to the .exe file. Only use this for testing and don’t ship it with your game.

- Test with a PlayStation or Switch Pro controller. XBox controllers look the same with and without Steam Input.

- Builds write their logs to the Player.log file (on Windows: %USERPROFILE%\AppData\LocalLow\\CompanyName\>\\ProductName\>\Player.log). For a Development Build, you can also connect the Unity Console to the running build.

If you are facing troubles or know a way to provide better support for Steam Input while using the new Input System, please reach out to me, either by email: <tobias.froihofer@gmx.at> or through the forum thread of this tool: <https://forum.unity.com/threads/input-icons-for-tmpro-easily-display-action-bindings.1253292/>
