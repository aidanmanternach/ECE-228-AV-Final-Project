# Object, Depth, and Trajectory Estimation for Autonomous Vehicles

ECE 228 Final Project  
Team 56: Manasvin Surya BJ, Francisco Garcia, Harini Sabapathy, Aidan Manternach

This is an open ended project which does camera only scene reconstruction and trajectory prediction in a modular way using finetuned YOLOv8 model, metric Depth Anything V2 model, and Kalman Filter. The main output for project is Bird's Eye View object projection and trajectory model with arrows demonstrating direction and velocity.  

## Machine Learning Framework:  

1. YOLOv8 on camera inputs to get bounding boxes
2. Depth Anything V2 on camera inputs to get metric depth map
3. Track object across frames with a Kalman filter and remove ego motion (camera motion)

## Repository Structure

| Folder | Contents |
|---|---|
| [`depth-model`](depth-model/) | Loads and evaluates the Depth Anything V2 model |

## Quick Start

TODO

## Models

- YOLOv8m fine tuned on the KITTI dataset for Car, Pedestrian, and Cyclist. The training and best model are saved in the `object-model` folder
- Depth Anything V2 (`depth-anything/Depth-Anything-V2-Metric-Outdoor-Small-hf`) is a pretrained model for metric depth detection from HuggingFace
- Kalman Filter for kinematic state estimation that tracks velocity and position for objects across frames