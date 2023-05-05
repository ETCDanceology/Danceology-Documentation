---
title: ML Installation
---

# ML Installation
## Overview
This document provides the details on how to install and set up a development environment for the Python-based/ML component of the Danceology project. All of the following documentation will assume a certain amount of familiarity with [Python](https://www.python.org/) and [Git/GitHub](https://docs.github.com/en) technologies.

## Unity Project
### Repository Link
[https://github.com/ETCDanceology/Danceology-ML](https://github.com/ETCDanceology/Danceology-ML)

### Tech Requirements
#### Python
The Danceology project used [Python 3.10](https://www.python.org/downloads/) for development, along with [pip](https://pip.pypa.io/en/stable/installation/) to install all packages and dependencies.

### Installation Steps
1. [Clone](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository) the [Danceology ML repository](https://github.com/ETCDanceology/Danceology-ML) locally
2. (Optional) Set up a [Python virtual environment](https://docs.python.org/3/library/venv.html)
3. Install all dependencies using
```
% pip install -r requirements.txt
```

# Running ML Model on Input Video
All scripts and logic related to ML-based video processing are within the `video_processing` folder.

1. `cd` into the `video_processing` directory
2. Run the following command
```
% python main.py -i [path_to_input_video] -o [path_to_output_json]
```

The output json file from this can be directly used for data cleaning below.


# Data Cleaning
All data cleaning scripts and logic are within the `data_cleaning` folder. The `main.py` file contains all the main cleaning functions; the `util.py` file contains all utility functions that are used during the data cleaning process.

You can customize how data cleaning is done by modifying different parameters within the `main.py` file.

1. `cd` into the `data_cleaning` directory
2. Run the following command
```
% python main.py -i [path_to_input_json] -o [path_to_output_json]
```

The output file from data cleaning can be used within the Unity project.
