# Udacity Car Capstone project


#### Team Torque 


Members:
<table style="border-collapse: collapse; border: none;">
<tr>
    <td>Tom Bertalan</td>
    <td>tom@tombertalan.com</td>
</tr>
<tr>
    <td>Dean Liu</td>
    <td>windsurf_dean@yahoo.com</td>
</tr>
<tr>
    <td>Louis Chow</td>
    <td>lchow3@gmail.com</td>
</tr>
<tr>
    <td>LUUTHIEN XUAN</td>
    <td>luuthienxuan@gmail.com</td>
</tr>
<tr>
    <td>Prasad Pillai</td>
    <td>prasadpillaiofficial@gmail.com</td>
</tr>
</table>

## Introduction
This is the final project of Udacity Self-Driving Car Nano degree program. In this project we work in teams of ~5 members to develop and implement the core functionalities of a self driving car. We also get a change to deploy and run our code or a real self driving car. The functionalities we implement include traffic light detection, control, waypoints generation and following.
Initially we develop and test our code within a simulator and once we are satisfied with the results we submit the project to Udacity to run it on there self-driving car called, Carla.

## Project setup

### Project directories overview

The project has the following structure. Details of each folder is given below.

| Folder | Description |
| :------------ | :----------- |
| /data       | Contain waypoint CSV files for the test cases  |
| /img       | Contain images for the documentation  |
| /model       | Traffic light detection for both simulated and real environments |
| /ros       | ROS catkin workspace  |
| /ros/devel       |  development folder |
| /ros/launch       | Contains launch files, for simulator and site testing |
| /ros/src       | ROS nodes source files  |


#### System requirement

##### Development environment
* Ubuntu 16.04 Xenial Xerus or Ubuntu 14.04 Trusty Tahir
* Processor: 3.0GHz processor or above
* 6GB System RAM
* Nvidia GPU card

##### Udacity Self-Driving Car Hardware Specs
* 31.4 GiB Memory
* Intel Core i7-6700K CPU @ 4 GHz x 8
* TITAN X Graphics
* 64-bit OS

### Setup development environment
We used native installation. The steps are given below.

#### Native Installation

1. Be sure that your workstation is running Ubuntu 16.04 Xenial Xerus or Ubuntu 14.04 Trusty Tahir. [Ubuntu downloads can be found here](https://www.ubuntu.com/download/desktop).

2. If using a Virtual Machine to install Ubuntu, use the following configuration as minimum:
  * 2 CPU
  * 2 GB system memory
  * 25 GB of free hard drive space

  The Udacity provided virtual machine has ROS and Dataspeed DBW already installed, so you can skip the next two steps if you are using this.

3. Follow these instructions to install ROS
  * [ROS Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu) if you have Ubuntu 16.04.
  * [ROS Indigo](http://wiki.ros.org/indigo/Installation/Ubuntu) if you have Ubuntu 14.04.

4. [Dataspeed DBW](https://bitbucket.org/DataspeedInc/dbw_mkz_ros)
  * Use this option to install the SDK on a workstation that already has ROS installed: [One Line SDK Install (binary)](https://bitbucket.org/DataspeedInc/dbw_mkz_ros/src/81e63fcc335d7b64139d7482017d6a97b405e250/ROS_SETUP.md?fileviewer=file-view-default)

5. Download the [Udacity Simulator](https://github.com/udacity/CarND-Capstone/releases).

6. Either clone this repository to /capstone, or clone it elsewhere and symlink it there with `ln -s "$CLONEDIR" /capstone`.

7. Make a python 2.7 virtual environment. [*virtualenvwrapper*](https://virtualenvwrapper.readthedocs.io/en/latest/) is great for this.

8. If installing on a machine with a CUDA- and TensorFlow-capable GPU:
  * Follow [TensorFlow's](https://www.tensorflow.org/install/install_linux#tensorflow_gpu_support) installation instructions, including the link to instructions for installing the CUDA toolkit and cuDNN. You may want to insert any commands for modifying your environment variables, such as `LD_LIBRARY_PATH`, into your ~/.profile file.
  * Change `tensorflow` to `tensorflow-gpu` in requirements.txt.
  * Note that CUDA 8 may be necessary for running with Python 2.7, as is the norm for ROS. This can be installed alongside CUDA 9 with `sudo apt-get install cuda-8-0`.

9. Reproduce the installation steps from Dockerfile, including running tod_coco_install.sh. Note that you'll first need to run e.g. `export ROS_DISTRO=kinetic` depending on your ROS distribution. Note that tod_coco_install.sh modifies your .bashrc file.

10. Still in the virtualenv, run `pip uninstall em` and `pip install` [`catkin_pkg`](https://stackoverflow.com/questions/43024337/why-this-error-when-i-try-to-create-workspaces-in-ros) [`em`](https://answers.ros.org/question/257331/python-module-empy-missing-tutorials/) [`rospkg`](https://answers.ros.org/question/39657/importerror-no-module-named-rospkg/).

11. In /capstone/ros, run `catkin_make`.

12. Either in a terminal where `roslaunch` is to be run, or permanently via ~/.bashrc or ~/.profile, run `source /capstone/ros/devel/setup.sh`.

13. Download [luu_real.pb](https://www.dropbox.com/s/51db8bato54plx1/luu_real.pb?dl=1) and [luu_sim.pb](https://www.dropbox.com/s/jbzy1skrsso15bf/luu_sim.pb?dl=1) and put them both in /capstone/ros/src/tl_detector/light_classification/saved_nets, making this directory if necessary.

14. Optionally, install the the Rviz plugins with `sudo apt-get install ros-kinetic-jsk-rviz-plugins libbullet-dev libsdl-image1.2-dev libsdl-dev`.


### Port Forwarding
To set up port forwarding, please refer to the [instructions from term 2](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/16cf4a78-4fc7-49e1-8621-3450ca938b77)

### Usage
Run ROS command to start the program

    ```
    cd ros
    catkin_make
    source devel/setup.sh
    roslaunch launch/styx.launch
    ```

7. Launch the simulator, uncheck "Manual", and check "Camera".

### Real world testing
1. Download [training bag](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/traffic_light_bag_file.zip) that was recorded on the Udacity self-driving car.
2. Unzip the file
```bash
unzip traffic_light_bag_file.zip
```
3. Play the bag file
```bash
rosbag play -l traffic_light_bag_file/traffic_light_training.bag
```
4. Launch your project in site mode
```bash
cd CarND-Capstone/ros
roslaunch launch/site.launch
```
5. Confirm that traffic light detection works on real life images

## Result

This project is divided into parts
1. Running on the simulator
2. Testing on ROS bag
3. Testing on actual vehicle, Carla

We were able to successfully run the code on the simulator as well as with the ROS bags. Running on the
actual vehicle is pending.
