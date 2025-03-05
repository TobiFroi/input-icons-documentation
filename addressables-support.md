---
title: Addressables Support
layout: default
nav_order: 13
---

# Addressable Support for Sprite Assets

TextMeshPro typically expects sprite assets to be in specific Resource folders, but you can optimize your project by using Unity's Addressable Asset System to load these assets on demand.

## Setup Options

### For Unity 2021.1 or newer with Addressables:

1. **Install the Addressables Package** if you haven't already (via Window > Package Manager).
2. **Create an Addressables Group** for your sprite assets:
   * Open the Addressables Groups window (Window > Asset Management > Addressables > Groups)
   * Create a new group (e.g., "TMP_SpriteAssets")
   * Drag your sprite assets into this group
3. **Add the TMPSpriteAssetLoader to your scene**:
   * Add it to a GameObject in your initial/persistent scene
   * Configure your sprite asset references in the Inspector using the Addressable references

### For Unity 2020.3 and earlier:

1. **Add the TMPSpriteAssetLoaderLegacy to your scene**:
   * Add it to a GameObject in your initial/persistent scene  
   * Directly assign your TMP_SpriteAsset objects to the sprite assets list in the Inspector

## Configuration

Both loader versions support the following features:

* **Platform-Specific Loading**:
  * Configure different sprite assets for different platforms (Windows, PlayStation, Xbox, etc.)
  * Create separate configurations for keyboard, gamepad, or touch controls as needed
  
* **Dynamic Loading**:
  * Load specific configurations by name during runtime using the `LoadConfigByName()` method
  * Unload all sprite assets when no longer needed with `UnloadAllSpriteAssets()`

## Code Example (Unity 2021.1+)

```csharp
// Configure in Inspector or via code
public class GameManager : MonoBehaviour 
{
    public TMPSpriteAssetLoader spriteLoader;
    
    void Start() 
    {
        // Optionally load a specific config by name
        spriteLoader.LoadConfigByName("PlayStationIcons");
    }
    
    void OnDestroy() 
    {
        // When no longer needed
        spriteLoader.UnloadAllSpriteAssets();
    }
}

## Benefits

Reduced initial load times and memory usage
Platform-specific assets loaded only when needed
Better organization of input-related sprite assets
Smaller build sizes when using Addressables (2021.1+ version)

## Common Issues

If sprites don't appear after loading, try refreshing your TMP_Text components using the RefreshTextComponents() method
Make sure your TMP Settings paths are correctly configured if you've moved your assets
For the Addressables version, remember that assets are loaded asynchronously, so plan accordingly in your UI initialization

