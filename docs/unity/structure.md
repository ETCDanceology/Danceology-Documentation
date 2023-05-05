---
title: Unity Codebase Structure
---

# Unity Codebase Structure
## Folder Structure
Danceology follows the standard folder structure of Unity Projects. Most edits will take place in the `Assets` folder, which contains:

```
Assets
| - Animations        # All animations + animation controllers
| - Art               # All art assets
| - Data              # Scriptable objects and other game data
| - Materials         # All GameObject materials
| - Models            # Pose detection ML model
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
- **MainScene:** The main scene with all of the level-related assets. This is where most of the epxerience takes place

To edit a particular **Scene**, double-click its corresponding file in this folder to open the scene in the Editor.

### Resources
The [Resources folder](https://docs.unity3d.com/Manual/BestPracticeUnderstandingPerformanceInUnity6.html) is a special folder in Unity that allows for runtime loading of assets. For this project, we use the Resources folder to store 2D pose data for pose matching and feedback, UI images for "Next Pose" indicators, and captions for the tutorial level.

### Scripts
All of the code within the game is located in this folder. Each of the code files is also separated into more specific directories based on functionality:

```
Scripts
  | - Data               # Scripts relating to level and in-game data
  | - GameObjects        # Scripts relating to specifically instantiable GameObjects
  | - Managers           # Global scene-specific managers
  | - PoseProcessing     # Scripts for logic relating to pose parsing, comparison, and output
  | - Sound              # Sound-related scripts
  | - UI                 # UI-related scripts
  | - Util               # General utility scripts
  | - _UNUSED            # Deprecated scripts
```

#### Data
This directory contains all the scripts that work directly with level-based data loaded into the level and other configurable [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html). 

#### GameObjects
This directory contains scripts that are directly employed by instantiable GameObjects within the scenes.

#### Managers
This directory contains global managers used within the scenes. These Managers are more global-level controllers for specific parts of the experience.

#### PoseProcessing
All of the logic for processing various aspects of pose input, comparison, and output (display within the experience) are contained within this folder.

- `OpenPoseOutputProcessor.cs` is the most low-level script within this folder that directly works with the output of the ML model. It performs all the basic conversions from the direct heatmap output of the model into readable formats for the rest of the code.
- `PoseDetector.cs` contains the global logic used to detect and perform computations/actions based on the webcam input as parsed by the ML model. Most of the general actions will go through this file.
- `MovementCompare.cs` specifically handles how the webcam input for the player's actions are compared and scored against the reference video positions.
- `OutputDataReader.cs` will convert and display the points found by the model into visible UI markers for the player.

#### Sound
This directory contains managers and related scripts for SFX and BGM used in the game.

#### UI
This directory contains managers and related scripts for all of the UI used in the game. The UI scripts in this directory have been split into two main categories: `StartSceneUI`, which has all the main menu-ing UI in the `StartScene`; and `GameSceneUI`, which has all of the assets used specifically within the levels themselves. 

Other files outside of these include util/base classes used for other UI assets. 

#### Util
This directory contains utility scripts used in the game and used to customize the editor.
