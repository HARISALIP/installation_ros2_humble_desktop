# installation_ros2_humble_desktop
ros2_humble


Here is a GitHub text for the above topics:

**Title:** ROS 2 Humble Installation on Ubuntu 22.04

**Description:** This guide provides step-by-step instructions on how to install ROS 2 Humble on Ubuntu 22.04.

**Prerequisites:**

* An instance of Ubuntu 22.04 desktop
* A sudo user configured on your instance

**Instructions:**

1. **Set locale**

```
locale
```

If the output of the command above does not include `en_US.UTF-8`, then install locales by running the following command:

```
sudo apt update && sudo apt install locales
```

Once installed, generate the UTF-8 locale using the following commands:

```
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
```

Then define and export the environment variable:

```
export LANG=en_US.UTF-8
```

2. **Add Official ROS 2 Humble repository to Ubuntu**

Install the essential packages required to add the repository:

```
sudo apt install software-properties-common curl gnupg lsb-release
```

Enable the Ubuntu Universe repository:

```
sudo add-apt-repository universe
```

Update the package lists:

```
sudo apt update
```

Add the ROS public GPG key:

```
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

Add the ROS 2 repository to the sources.list file:

```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

3. **Update the ROS 2 package index**

Update the APT repository cache:

```
sudo apt update
```

Upgrade all the packages to their latest versions:

```
sudo apt upgrade
```

4. **Install ROS 2 Humble on Ubuntu 22.04**

Install the ROS Humble desktop package:

```
sudo apt install ros-humble-desktop
```

**Note:** If you are using ROS for the first time, we strongly recommend the desktop install. On the other hand, you can opt to install the minimal setup or the essentials (without the helpful GUIs or learning materials that come with the desktop install) using the following commands:

```
sudo apt install ros-humble-ros-base
```

OR

```
sudo apt install ros-humble-ros-core
```

5. **Set up ROS 2 Humble environment**

Source the setup file:

```
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

If you are on zsh shell, run the following commands instead:

```
echo "source /opt/ros/humble/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```

6. **Verify ROS 2 installation**

Navigate to the /opt/ros/humble/lib/demo_nodes_cpp/ directory:

```
cd /opt/ros/humble/lib/demo_nodes_cpp/
```

Run the C++ talker:

```
ros2 run demo_nodes_cpp talker
```

If everything is working properly, you will get the following output:

```
Hello, world!
```

Alternatively, switch to the /opt/ros/humble/lib/demo_nodes_py/ directory:

```
cd /opt/ros/humble/lib/demo_nodes_py/
```

Run the Python listener:

```
ros2 run demo_nodes_py listener
```

You should get the following output:

```
I heard: Hello, world!
```

Once you have successfully completed these steps, you will have ROS 2 Humble installed and ready to use on your Ubuntu 22.04 system.
