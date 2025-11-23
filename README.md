## Installation

### Ubuntu Setup

1. Install UBUNTU distro `wsl -install -list`
2. Local Configuration
```
locale
sudo apt update && sudo apt upgrade
sudo locale-gen en_US ne_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
locale
```
3. Software Properties and Universe Repo
```
sudo apt install software-properties-common
sudo add-apt-repository universe
```
4. CUrl isntallation and ROS Key
```
sudo apt update && sudo apt install curl -y
export ROS_APT_SOURCE_VERSION=$(curl -s https://api.github.com/repos/ros-infrastructure/ros-apt-source/releases/latest | grep -F "tag_name" | awk -F\" '{print $4}')
curl -L -o /tmp/ros2-apt-source.deb "https://github.com/ros-infrastructure/ros-apt-source/releases/download/${ROS_APT_SOURCE_VERSION}/ros2-apt-source_${ROS_APT_SOURCE_VERSION}.$(. /etc/os-release && echo ${UBUNTU_CODENAME:-${VERSION_CODENAME}})_all.deb"
sudo dpkg -i /tmp/ros2-apt-source.deb
```

5. ROS Desktop Install
```
sudo apt install ros-humble-desktop
```

6. ROS ENV Setup
```
source /opt/ros/humble/setup.bash
```

7. Running Executables
```
sudo apt update
sudo apt install ros-humble-turtlesim

ros2 pkg list # Verify packages
ros2 pkg executables # Verify executables
ros2 pkg executables turtlesim # Verify executables

ros2 run turtlesim turtlesim_node
ros2 run turtlesim turtle_teleop_key
```