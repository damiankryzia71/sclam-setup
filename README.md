# Visual SCLAM Project Setup
### Authors: https://github.com/rodrigo-munguia/SCLAM-UAVs

The steps in this guide were executed on a freshly installed Ubuntu 20.04 system running on VMWare.
- [VMWare Download](https://livecsupomona-my.sharepoint.com/:u:/g/personal/rickramirez_cpp_edu/EauwsEtVC3ZIpcxP7PNTYyQBfk_FGKrOK8cS6195BIdhJQ?e=aO1hES)
- [Ubuntu 20.04 ISO Download](https://releases.ubuntu.com/focal/ubuntu-20.04.6-desktop-amd64.iso)

Before launching and using the SCLAM project, necessary dependencies must be installed.
These include:
- ROS 2 Galactic
- Armadillo 11.0.1
- OpenCV 4.2.0 with contrib modules
- GTSAM 4.1.1
- Webots v.R2023a

This guide will walk you through the installation of these dependencies and the main project.
The dependencies can be installed in any order, following the order of this depository is not required.

### 1. Install ROS 2
Run the following script to install ROS 2 Galactic and its necessary dependencies.

```bash
sudo apt update && sudo apt install locales
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt update
sudo apt upgrade
sudo apt install ros-galactic-desktop
sudo apt install ros-galactic-ros-base
sudo apt install ros-dev-tools
```

Optionally: reboot the system to ensure everything is correct.
```bash
sudo reboot
```

### 2. Install Armadillo 11.0.1
First, download Armadillo 11.0.1 [here](https://sourceforge.net/projects/arma/files/armadillo-11.0.1.tar.xz/download?use_mirror=master).
Then run the script below to install it.

```bash
sudo apt update
sudo apt install cmake libopenblas-dev liblapack-dev libarpack2-dev libsuperlu-dev
cd ~
sudo mv Downloads/armadillo-11.0.1.tar.xz .
sudo tar xf armadillo-11.0.1.tar.xz
cd armadillo-11.0.1/
sudo cmake .
```

Optionally: reboot the system to ensure everything is correct.
```bash
sudo reboot
```

### 3. Install GTSAM 4.1.1
Run the following script to install GTSAM 4.1.1 and its necessary dependencies.

```bash
cd ~
sudo apt update
sudo apt-get install libboost-all-dev
sudo apt-get install cmake
git clone -b 4.1 https://github.com/borglab/gtsam.git
cd gtsam
sudo mkdir build && cd build
sudo cmake ..
sudo make install
```
