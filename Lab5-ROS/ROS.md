###Install ROS
1.Set up your sources.list
```shell
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
2.Set up your keys
```shell
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116
```
3.Installation
```shell
sudo apt-get update
sudo apt-get install ros-kinetic-desktop-full
```
4.Initialize rosdep
```shell
sudo rosdep init
rosdep update
```
5.Environment setup
```shell
echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```
6.Getting rosinstall
```shell
sudo apt-get install python-rosinstall
```