---
title: Danceology Implementation
---

# Danceology Implementation
## Overview
This document provides implementation details on the Danceology project; specifically, we will go into the Unity file structure and provide details on how specific features are benig implemented. For further Unity documentation see their [User Manual](https://docs.unity3d.com/Manual/UnityManual.html).

## Code Structure
Danceology follows the standard folder structure of Unity Projects. Most edits will take place in the `Assets` folder, which contains:

```
Assets
| - Animations        # All animations + animation controllers
| - Art               # All art assets
| - Materials         # All GameObject materials
| - Plugins           # Files provided by other Unity Plugins
| - Prefabs           # All prefabricated assets
| - Presets           # Editor presets
| - Resources         # Special Resources folder containing runtime-loaded assets
| - Scenes            # All game scenes
| - Scripts           # All C# scripts
| - Settings          # Shader and rendering-related settings
| - Shaders           # All shader assets
| - Sounds            # All SFX + BGM sound assets
| - TextMesh Pro      # Text rendering package
| - Textures          # All textures
```

Most of these folders contain various assets that are used within the project, such as 3D models, 2D UI assets, animations, shaders, and sounds. The below sections will highlight some of the key folders to be familiar with.

### Scenes
Each "level" within Unity is captured within a **Scene**. For the Danceology project, there are three main scenes:

- **StartScene:** The initial scene presented to a user, with all of the menuing to start a level.
- **IntroScene:** A separate scene used for the introduction level (playing an intro video).
- **MainScene_FeedbackTest:** The main scene with all of the level-related assets. This is where most of the epxerience takes place (TODO: rename this scene)

To edit a particular **Scene**, double-click its corresponding file in this folder to open the scene in the Editor.

### Resources
The [Resources folder](https://docs.unity3d.com/Manual/BestPracticeUnderstandingPerformanceInUnity6.html) is a special folder in Unity that allows for runtime loading of assets. For this project, we use the Resources folder to store 2D pose data for pose matching and feedback, UI images for "Next Pose" indicators, and captions for the tutorial level.

### Scripts
All of the code within the game is located in this folder. Each of the code files is also separated into more specific directories based on functionality:

TODO: Please clean this up and fill it out
```
Scripts
  | - Sound              # Sound-related scripts
  | - UI                 # UI-related scripts
  | - Util               # General utility scripts
```

#### Sound
This directory contains managers and related scripts for SFX and BGM used in the game.

#### UI
This directory contains managers and related scripts for all of the UI used in the game.

#### Util
This directory contains utility scripts used in the game and used to customize the editor.

## General Game Flow
The following sections provide a general overview of what happens behind-the-scenes in a given play session.

TODO: Fill out
