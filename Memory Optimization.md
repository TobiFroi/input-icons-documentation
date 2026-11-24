---
title: Memory Optimization
layout: default
parent: Customization
nav_order: 3
---

# Memory Optimization

Input Icons creates sprite atlases for TextMeshPro text while also maintaining references to individual sprites for UI Images and Sprite Renderers. This dual reference system can result in duplicate sprite data being loaded into memory.

## How Memory Optimization Works

The memory optimization feature allows your Icon Sets to reference sprites directly from the TextMeshPro sprite atlas instead of keeping separate sprite references. This means both TextMeshPro text and UI/Sprite components will use the same sprite references, potentially reducing memory usage.

![Memory Optimization Section](/input-icons-documentation/assets/images/memory-optimization.png)

## Optimizing Memory Usage

To reduce memory usage with sprite references:

1. Complete the TextMeshPro setup first
2. Go to **Tools → Input Icons → Input Icons Setup → TextMeshPro Setup**
3. Scroll to the **Memory Optimization** section
4. Enable "Create backups of Icon Sets" (strongly recommended)
5. Click "Optimize Memory Usage" and confirm when prompted

## Restoring From Backups

If you need to modify the original sprites or revert the optimization:

1. Go to **Tools → Input Icons → Input Icons Setup → Customization**
2. Find the **Restore from Backups** section
3. Optionally enable "Rename original sets to include '_AtlasSprites' suffix"
4. Click "Find and Restore Backup Icon Sets"

When restoring with renaming enabled:
- Original icon sets get the '_AtlasSprites' suffix
- Backup icon sets are restored to the original filenames

## When to Use Memory Optimization

**Recommended for:**
- Projects concerned with memory usage
- Games with finalized icon designs
- Later stages of development

**Not recommended for:**
- Projects frequently modifying icon sprites
- Early development stages

**Note:** This optimization cannot be easily reversed without backups.