

## How to Run the Simulation

### 1. Clone the repository (with submodules)
```bash
git clone --recurse-submodules <your-main-repo-url>
cd <your-main-repo>
```

### 2. Build the workspace
```bash
source /opt/ros/humble/setup.bash
colcon build --symlink-install
```

### 3. Source the workspace
```bash
source install/setup.bash
```


### 4. Launch the simulation
Basic launch:
```bash
ros2 launch neo_simulation2 simulation.launch.py
```

#### Example: Launch with custom robot, world, arm, and pan-tilt
```bash
ros2 launch neo_simulation2 simulation.launch.py \
	my_robot:=mmo_700 world:=neo_workshop arm_type:=ur5e include_pan_tilt:=true
```

### 5. (Optional) Using Docker
- Build the Docker image:
	```bash
	docker build --build-arg DOCKER_REPO=osrf/ros --build-arg ROS_DISTRO=humble --build-arg IMAGE_SUFFIX=-desktop-full --build-arg USERNAME=$USER -t test_ros2_sim_gazebo:latest -f .devcontainer/Dockerfile .
	```
- Run the container:
	```bash
	docker run -it --rm --net=host -e DISPLAY=$DISPLAY --gpus all -v /tmp/.X11-unix:/tmp/.X11-unix -v $(pwd):/home/ws test_ros2_sim_gazebo:latest
	```

---
For more details, see the [Neobotix ROS2 simulation documentation](https://neobotix-docs.de/ros/ros2/simulation_classic.html) and the [modern Gazebo migration guide](https://neobotix-docs.de/ros/ros2/simulation_modern.html).

---
Since the classic gazebo has reached End of Life, There will be no further updates to this packages. 

All the robots in this packages have been migrated to modern Gazebo with some more additional features. More information about the installation and usage of the new modern Gazebo simulation can be [found in our documentation.](https://neobotix-docs.de/ros/ros2/simulation_modern.html)
