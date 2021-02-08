# ROS2 Packages on NVIDIA Jetson

Ease of use and deployment have made the [NVIDIA Jetson platform](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/) a logical choice for developers, researchers, and manufacturers building and deploying robots.

## ROS2 Package for Human Pose Estimation

The `ros2_trt_pose` package is implemented based on `trt_pose`, which enables pose estimation on the Jetson platform. The repository provides two trained models for pose estimation using resnet18 and densenet121. To understand human pose, pretrained models infer 17 body parts based on the categories from the COCO dataset.

[ NVIDIA-AI-IOT/ros2-trt-pose GitHub Link](https://github.com/NVIDIA-AI-IOT/ros2_trt_pose)

Here are the key features of the `ros2_trt_pose` package:

* Publishes `pose_msgs` such as count of person and `person_id`. For each `person_id`, it publishes 17 body parts.
* Provides launch file for easy usage and visualizations on Rviz2:
** Image messages
** Visual markers: `body_joints`, `body_skeleton`
* Contains a Jetson-based Docker image for easy install and usage

## ROS2 Package for PyTorch and NVIDIA TensorRT

There are two packages for classification and detection using PyTorch, each with their corresponding TRT versions implemented. These four packages are a good starting point for roboticists using ROS 2 to get started with deep learning using PyTorch.

TensorRT has been integrated into the packages with the help of torch2trt for accelerated inference. It generates a runtime engine which is optimized according to the architecture of the network and the deployment device.   

[NVIDIA-AI-IOT/ros2-torch-trt GitHub Link](https://github.com/NVIDIA-AI-IOT/ros2_torch_trt)

The main features of the packages are as follows:

* For classification, you can select from various ImageNet pretrained models, including Resnet18, AlexNet, SqueezeNet, and Resnet50.
* For detection, MobileNetV1-based SSD is currently supported, trained on the COCO dataset.
* The TRT packages provide a significant speedup in carrying out inference relative to the PyTorch models performing inference directly on the GPU.
* The inference results are published in the form of `vision_msgs`.
* On running the node, a window is also shown with the inference results visualized.
* A Jetson-based Docker image and launch file is provided for ease of use

## ROS 2 Package for DeepStream SDK

The DeepStream SDK delivers a complete streaming analytics toolkit to build end-to-end AI-based solutions using multi-sensor processing, video, and image understanding. It offers support for popular object detection and segmentation models such as state of the art SSD, YOLO, FasterRCNN, and MaskRCNN.

[NVIDIA-AI-IOT/ros2-deepstream GitHub Link](https://github.com/NVIDIA-AI-IOT/ros2_deepstream)

NVIDIA provide ROS 2 nodes that perform two inference tasks based on the DeepStream Python Apps project as follows:

* Object detection: Four classes of objects are detected: Vehicle, Person, RoadSign, and TwoWheeler.
* Attribute classification: Three types of attributes are classified for objects of class Vehicle: Color, Make, and Type.

These publisher nodes take single or multiple video streams as input from camera or file. They perform inference and publish results of detection and classification to different topics. We also provide sample ROS 2 subscriber nodes that subscribe to these topics and display results in `vision_msgs` format. Each inference task also spawns a visualization window with bounding boxes and labels around detected objects. Additional inference tasks and custom models can be integrated with the DeepStream pipeline provided in this project.

## ROS2 Package for Jetson Stats

The `ros2_jetson_stats` package is a community build package that monitors and controls your Jetson device. It can run on your terminal and provides a Python package for easy integration in Python scripts. Take advantage of the `ros2_jetson_stats` library and build ROS 2 diagnostic messages and services.

[NVIDIA-AI-IOT/ros2-jetson-stats GitHub Link](https://github.com/NVIDIA-AI-IOT/ros2_jetson_stats)

The `ros2_jetson_stats` package features the following ROS 2 diagnostic messages:

* GPU/CPU usage percentage
* EMC/SWAP/Memory status (% usage)
* Power and temperature of SoC

You can now control the following through the ROS 2 command line:

* Fan (Mode and Speed)
* Power model (nvpmodel)
* `jetson_clocks`
You can also provide a parameter to set the frequency of reading diagnostic messages.

## Deep Learning Nodes for ROS/ROS2

This repo contains deep learning inference nodes and camera/video streaming nodes for ROS/ROS2 with support for Jetson Nano/TX1/TX2/Xavier NX/AGX Xavier and TensorRT.

[GitHub Link](https://github.com/dusty-nv/ros_deep_learning)

The nodes use the image recognition, object detection, and semantic segmentation DNN's from the `jetson-inference` library and [NVIDIA Hello AI World](https://developer.nvidia.com/embedded/twodaystoademo) tutorial, which come with several built-in pretrained networks for classification, detection, and segmentation and the ability to load customized user-trained models.

The camera/video streaming nodes support the following input/output interfaces:

* MIPI CSI cameras
* V4L2 cameras
* RTP / RTSP
* Videos & Images
* Image sequences
* OpenGL windows

ROS Melodic and ROS2 Eloquent are supported, and the latest version of JetPack is recommended.

![Creative Commons License](https://i.creativecommons.org/l/by/4.0/88x31.png)

This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/)
