# Voice Navigation Robot
# Voice-Navigation-Robot-IvLabs

## Requirements

* Ubuntu 20.04
* ROS Noetic
* Pocketsphinx
* Gstreamer

## Turtlesim


## Gazebo

Gazebo is a robotics simulation environment included within ROS. It provides a 3D physics-based simulation of robots, environments, and sensors, allowing users to simulate and test robotic systems in a virtual environment before deploying them in the real world. We will use Turtlebot 3 inside gazebo for our simulations.

## Turtlebot 3

TurtleBot 3 is a versatile open source robot platform designed for education, research, and prototyping applications in robotics. It is fully compatible with ROS, making it easy to integrate with ROS-based software libraries, tools, and simulations allowing users to leverage the extensive ROS ecosystem for developing and testing robotic applications.

[Turtlebot 3 Manual](https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/)

INSTALLATION:
1) Run the following commands in your terminal. Make sure to clone the repositories into your workspace.
   ```
   git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
   git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
   git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
   ```
2) Build your packages.
   ```
   catkin_make
   ```

BASIC SIMULATION:
1) Export your turtlebot model. We will be using burger.
   ```
   export TURTLEBOT3_MODEL=burger
   ```
2) To launch and empty world use the following command.
   ```
   roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
   ```
3) To launch another world with objects use the following command.
   ```
   roslaunch turtlebot3_gazebo turtlebot3_world.launch
   ```
4) To perform teleoperations open another terminal and run the following.
   ```
   export TURTLEBOT3_MODEL=burger
   roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
   ```

## SLAM



## Pocketsphinx

PocketSphinx is a lightweight speech recognition engine developed by Carnegie Mellon University (CMU). We are using pocketsphinx with out own custom dictionary for the purpose of speech recognition and voice control of the robot.

INSTALLATION:
1) Clone the [pocketsphinx](https://github.com/cmusphinx/pocketsphinx) and [sphinxbase](https://github.com/cmusphinx/sphinxbase) repostories into your workspaces.
2) Go into the sphinxbase folder and build it.

   ```
   ./autogen.sh
   ./configure
   make
   make install
   ```

## Gstreamer

GStreamer is a multimedia framework that provides a pipeline-based architecture for constructing multimedia applications. It is open source and widely used in various applications and platforms to handle multimedia processing, streaming, and playback. We will be using gstreamer to integrate pocketsphinx into our ROS project. Its modular nature will help us examine indivudual elements of the pipeline.

INSTALLATION:  

```
apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio
```
## VOSK 

The VOSK voice model is a lightweight, open-source speech recognition toolkit that allows for offline voice command processing. In this project, VOSK is integrated with a TurtleBot operating in the Gazebo simulation environment, enabling voice-controlled navigation. Users can issue simple voice commands such as "forward," "stop," "right," "left," and "back" to control the TurtleBot's movements. VOSK supports multiple languages and dialects, increasing its usability across different regions.we had use this in alternative of pocketsphinx in case if it's not working. 

INSTALLATION:  

1. Run the following in a terminal.
```
pip install vosk
wget https://alphacephei.com/vosk/models/vosk-model-small-en-us-0.15.zip
unzip vosk-model-small-en-us-0.15.zip
```

2. Load the model into your Vosk speech recognition code by specifying the path to the unzipped model directory.

[VOSK GitHub Repository](https://github.com/alphacep/vosk-api): The official repository for the VOSK API.<br>
[VOSK Model Setup for ROS](https://github.com/alphacep/vosk-api/blob/master/doc/ros.md): Guide to setting up VOSK with ROS for voice control applications.<br>

## Running Voice Models in Turtlebot
 
1. **Recognition :** A publisher node with the voice models listens to microphone input for voice input.
2. **Processing :** Upon detecting a command, the voice model converts the voice input into string data.
3. **Publishing :** The string data is published over a speech topic.
4. **Execution :** A node with a subscriber and a publisher, listens for the incoming data over the topic and published relevant commands to the turtlebot3 topics.




