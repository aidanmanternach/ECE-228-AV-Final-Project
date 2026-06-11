# Object, Depth, and Trajectory Estimation for Autonomous Vehicles

ECE 228 Final Project  
Team 56: Manasvin Surya BJ, Francisco Garcia, Harini Sabapathy, Aidan Manternach

This is an open-ended project which does camera-only scene reconstruction and trajectory prediction in a modular way using finetuned YOLOv8 model, metric Depth Anything V2 model, and Kalman Filter. The main output for project is Bird's Eye View (BEV) object projection and trajectory model with arrows demonstrating direction and velocity.  

**Note**: All of the notebooks render properly in Github, however, we have experienced instances where they do not render upon first time loading the web page. If facing this issue, the Github repo can be cloned locally where the notebooks will be properly displayed in the IDE or attempt reloading the page.

## Machine Learning Framework:  

1. YOLOv8 on camera inputs to get bounding boxes
2. Depth Anything V2 on camera inputs to get metric depth map
3. Track object across frames with a Kalman filter and remove ego motion (camera motion)

## Repository Structure

| Folder | Contents |
|---|---|
| [`depth_model`](depth_model/) | Loads and evaluates the Depth Anything V2 model |
| [`yolov8_finetuning`](object_model/) | Fine tune and evaluation YOLOv8 on KITTI, best model weights are saved as best.pt |
| [`bev_trajectory_modelling`](bev_trajectory_modelling/) | Main project framework for object, depth, and trajectory prediction |

## Run Code and Reproduce Results

All of our work was done primarily in jupyter notebooks.

### Model Notebooks

Both the depth and object model notebooks can be ran in order to evaluate the given models.

### BEV Trajectory Modelling Notebook

This notebook contains that main framework for BEV projection and trajectory prediction. This notebook can be run in any environment, but is recommended for google colab.  

In order to reproduce the results for the three driving test sequences, there are configuration variables at the top of the notebook. The configuration variables that need to be changed: `SEQUENCE_ID`, `RAW_DATE`, `RAW_DRIVE`

| Driving Sequence | Configuration Variables |
|---|---|
| 0003 | `SEQUENCE_ID` 0003 <br> `RAW_DATE`: 2011_09_26 <br> `RAW_DRIVE`: 2011_09_26_drive_0013_sync |
| 0004 | `SEQUENCE_ID` 0004 <br> `RAW_DATE`: 2011_09_26 <br> `RAW_DRIVE`: 2011_09_26_drive_0014_sync |
| 0005 | `SEQUENCE_ID` 0005 <br> `RAW_DATE`: 2011_09_26 <br> `RAW_DRIVE`: 2011_09_26_drive_0015_sync |

## Models

- YOLOv8m fine tuned on the KITTI dataset for Car, Pedestrian, and Cyclist. The training and best model are saved in the `object_model` folder
- Depth Anything V2 (`depth-anything/Depth-Anything-V2-Metric-Outdoor-Small-hf`) is a pretrained model for metric depth detection from HuggingFace
- Kalman Filter for kinematic state estimation that tracks velocity and position for objects across frames
